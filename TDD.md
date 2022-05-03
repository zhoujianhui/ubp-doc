// RestAssured处理原生类型
RestAssured.registerParser("text/plain", Parser.TEXT);
given().contentType(ContentType.JSON).body(imageCaptchaVerifyInfo)
        .when().post("/captchas/img/verify")
        .then()
        .statusCode(HttpStatus.OK.value())
        .body(is("true"));