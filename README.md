Created Apps Script in Google with below function

function doPost(e) {
  var data = Utilities.base64Decode(e.parameters.data);
  var filename = Utilities.formatDate(new Date(), "GMT-8", "yyyyMMdd_HHmmss")+".jpg";
  var blob = Utilities.newBlob(data, e.parameters.mimetype, filename);

  var folder, folders = DriveApp.getFoldersByName("ESP32-CAM");
  if (folders.hasNext()) {
    folder = folders.next();
  } else {
    folder = DriveApp.createFolder("ESP32-CAM");
  }
  var file = folder.createFile(blob); 

  return ContentService.createTextOutput("Completed")
}

During Deployment, 
1. choose web app
2. Execute As Me
3. The web app will be authorized to run using your account data. - Anyone
