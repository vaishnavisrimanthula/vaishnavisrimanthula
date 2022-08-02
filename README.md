<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html>
    <head>
        <title>Login2explore</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>

    <body>
        <div>Vaishnavi Srimanthula</div>
    
<html lang="en">
<head>
<title>Bootstrap Example</title>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet"
href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
<script
src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
<script
src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</head>
<body>
<div class="container">
<h2>Student Application Form</h2>
<form id="stuform" method="post">
<div class="form-group">
<span><label for="stuId">Student ID:</label> <label id="stuIdMsg">
</label></span>
<input type="text" class="form-control" name="stuId" id="stuId"
placeholder="Enter Student ID" required>
</div>
<div class="form-group">
<label for="stuName">Student Name:</label>
<input type="text" class="form-control" id="stuName"
placeholder="Enter Student Name" name="stuName">
</div>
<div class="form-group">
<label for="stuEmail">Email ID:</label>
<input type="email" class="form-control" id="stuEmail"
placeholder="Enter Student Email ID" name="stuEmail">
</div>
<div class="form-group">
<label for="stuMobile">Mobile No.:</label>
<input type="mobile" class="form-control" id="stumobile"
placeholder="Enter Student Mobile No." name="stumobile">
</div>

<input type="button" class="btn btn-primary" id="stuSave" value="Save"
onclick="saveStudent();">
</form>
</div>
    <script>
       function  validateAndGetFormData() {
var stuIdVar = $("#stuId").val();
if (stuIdVar === "") {
alert("Student ID is Required to Proceed");
$("#stuId").focus();
return "";
}
var stuNameVar = $("#stuName").val();
if (stuNameVar === "") {
alert("Student Name is Required to Proceed");
$("#stuName").focus();
return "";
}
var stuEmailVar = $("#stuEmail").val();
if (stuEmailVar === "") {
alert("Student Email is Required to Proceed");
$("#stuEmail").focus();
return "";
}
var jsonStrObj = {
stuId: stuIdVar,
stuName: stuNameVar,
stuEmail: stuEmailVar,
};
return JSON.stringify(jsonStrObj);
}

function executeCommand(reqString, dbBaseUrl, apiEndPointUrl) {
var url = dbBaseUrl + apiEndPointUrl;
var jsonObj;
$.post(url, reqString, function (result) {
jsonObj = JSON.parse(result);
}).fail(function (result) {
var dataJsonObj = result.responseText;
jsonObj = JSON.parse(dataJsonObj);
});
return jsonObj;
}
function resetForm() {
$("#stuId").val("")
$("#stuName").val("");
$("#stuEmail").val("");
$("#stuId").focus();
}


       function saveStudent(){
        var jsonStr = validateAndGetFormData();
if (jsonStr === "") {
return;
}
var putReqStr = createPUTRequest("90937585|-31949295054917225|90940193",
jsonStr, "Student", "stu-rel");
alert(putReqStr);
jQuery.ajaxSetup({async: false});
var resultObj = executeCommand(putReqStr,
"http://api.login2explore.com:5577", "/api/iml");
alert(JSON.stringify(resultObj));
jQuery.ajaxSetup({async: true});
alert(JSON.stringify(result0bj));
resetForm();
    alert ("Student registeration has successfully done.");
        
        }
        </script>
</body>
</html>
