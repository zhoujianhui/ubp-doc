
## 查询对象
```java
@ApiModel("角色查询对象")
@NoArgsConstructor
@Getter
@Setter
public class RoleQuery {

    @ApiModelProperty("角色名")
    private String roleName;

    @ApiModelProperty("用户名")
    private String username;

    @ApiModelProperty("权限名")
    private String permissionName;


    static Specification<Role> roleNameLike(String roleName) {
        return (root, query, criteriaBuilder) -> criteriaBuilder.like(root.get("name"), "%" + roleName + "%");
    }

    static Specification<Role> userNameLike(String roleName) {
        return (root, query, criteriaBuilder) -> {
            final Join<Role, User> userRoot = root.join("users", JoinType.INNER);

            return criteriaBuilder.like(userRoot.get("username"), "%" + roleName + "%");
        };
    }

    static Specification<Role> permissionNameLike(String permissionName) {
        return (root, query, criteriaBuilder) -> {
            final Join<Role, Permission> permissionRoot = root.join("permissions", JoinType.INNER);

            return criteriaBuilder.like(permissionRoot.get("name"), "%" + permissionName + "%");
        };
    }

    public Specification<Role> build() {
        Specification<Role> specification = where(null);

        if (this.username != null) {
            specification = specification.and(userNameLike(this.username));
        }

        if (this.roleName != null) {
            specification = specification.and(roleNameLike(this.roleName));
        }

        if (this.permissionName != null) {
            specification = specification.and(permissionNameLike(this.permissionName));
        }

        return specification;
    }
}
```

```java
@Test
@DisplayName("find role by query")
public void findByQuery() {
    RoleQuery roleQuery = new RoleQuery();
    roleQuery.setRoleName("管理员");
    roleQuery.setUsername("admin");
    roleQuery.setPermissionName("个人中心");

    Specification<Role> specification = roleQuery.build();

    List<Role> roles = roleRepository.findAll(specification);

    assertThat(roles).hasSize(1);
}
```

Spring Data JPA @Modifying Annotation
https://www.baeldung.com/spring-data-jpa-modifying-annotation