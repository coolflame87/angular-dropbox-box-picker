angular-dropbox-box-picker
==========================

A simple and cool angular directive which interacts with box and dropbox file pickers

Demo
==========================

https://samarhaider.github.io/angular-dropbox-box-picker/app/

Installation
==========================

1. Using NPM (recommended)

  ```bash
  npm install angular-dropbox-picker --save
  ```

2. Using Bower

  ```Bash
  bower install angular-dropbox-picker --save
  ```

3. Manually

Download [https://github.com/samarhaider/angular-dropbox-box-picker/archive/master.zip](https://github.com/samarhaider/angular-dropbox-box-picker/archive/master.zip)



Usage
==========================


 1. Include script in html
 
   ```html
  <script src="dropbox-picker.min.js"></script>
  ```
    For Dropbox:
    ```html
  <script type="text/javascript" src="https://www.dropbox.com/static/api/2/dropins.js" id="dropboxjs"  data-app-key="APP_KEY"></script>
  ```
    Don't forgot ot replace APP_KEY with appkey which get from dropbox app console    https://www.dropbox.com/developers/apps
    For Box:
   ```html
  <script type="text/javascript" src="https://app.box.com/js/static/select.js"></script>
  ```
    

 2. Include the dropbox-picker as a dependency for your app

      angular.module('myApp', ['dropbox-picker'])

 3. Configuration
 
  for more details about options got https://www.dropbox.com/developers/dropins/chooser/js and      https://developers.box.com/the-box-file-picker/

       angular.module('DropboxControllers', ['dropbox-picker'])
    
        .config(['DropBoxSettingsProvider', function(DropBoxSettingsProvider) {
    
          // Configure the options
            DropBoxSettingsProvider.configure({
                linkType: 'preview',//dropbox link type
                multiselect: true,//dropbox multiselect
                extensions: ['.pdf', '.doc', '.docx'],//dropbox file extensions
                box_clientId: 'tdjpulviw9wzj20gd1t8rlh93vpvvh4m',// box CLient Id
                box_linkType: 'shared',//box link type
                box_multiselect: 'true'//box multiselect
              });
        }])
        
 4.  Create scope to handle choosed files
 
      .controller('DropBoxCtrl', ['$scope', 'DropBoxSettings', function($scope, DropBoxSettings) {
   
        $scope.onDropboxSuccess = function (files) {
            angular.forEach(files, function (file, index) {
                console.log(file);
            });
        }
        $scope.onDropboxCancel = function () {
            console.log('Dropbox close/cancel!');
        }

        $scope.onBoxSuccess = function (files) {
            angular.forEach(files, function (file, index) {
                console.log(file);
            });
        }
        $scope.onBoxCancel = function () {
            console.log('Box close/cancel!');
        }
      }]);   

 5. Add the directive to your HTML element
 
    Dropbox:
      
          <a href="javascript:;" drop-box-picker on-dropbox-success="onDropboxSuccess(files)"  on-dropbox-cancel="onDropboxCancel()">Dropbox Picker</a>

    Box:
    
          <a href="javascript:;" box-picker on-box-success="onBoxSuccess(files)"  on-box-cancel="onBoxCancel()">Box Picker</a>
          
 6. Done.

 
