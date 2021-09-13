# lab-charlie-noahc
[Link to live app on Heroku](https://lab-charlie-noahc.herokuapp.com/)

## About how Angular is used in this app
When the user navigates to the main page, "and hi there, tom tom" is one of the things displayed. "tom tom" is part of an object that comes from the `user.json` file, which can be seen on the [/user page](https://lab-charlie-noahc.herokuapp.com/user). `index.js` maps to that file with this bit of code:
```javascript
app.get('/user', function (req, res) {

    res.sendFile('/user.json', { root: __dirname });

});
```
The main page, `angular.html`, creates a controller to get the data with this javascript code:
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

and then displays the 'name' with ```<h3 id="user-greeting">and hi there, {{ user.name }}</h3>```.
An input box is created with the line ```<input ng-model="user.name">``` and updates the 'name' live on the page without a refresh of the page. However, the data is not updated and saved in `user.json`, so anything new put in the box is gone when the page is refreshed.
