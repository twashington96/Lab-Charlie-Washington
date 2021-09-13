# Lab-Charlie
[Link to Heroku]()

## Angular

`angular.html`, creates a controller to get the data using this code:
```javascript
app.controller('MainController', function ($scope, $http) {
            $scope.user = null;

            $http.get('/user')
                .then(response => {
                    console.log(response.data);

                    $scope.user = response.data;
                });

        });
```

Then proceeds on to ```<h3 id="user-greeting">and hi there, {{ user.name }}</h3>```.

An input box is created with the line ```<input ng-model="user.name">``` and updates the 'name' live. While the page is updated live, the actual `user.json` file doesn't change so anything that is changed on the page isn't permanent.
