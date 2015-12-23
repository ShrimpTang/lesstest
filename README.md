https://www.youtube.com/watch?v=YQYJUeokqOY&list=PL6gx4Cwl9DGCshbAx1JpBtNoKh8iKAAiy

`` html
<!DOCTYPE html>
<html lang="en" ng-app="myApp">
<head>
    <meta charset="UTF-8">
    <title></title>
</head>
<body ng-controller="myCtrl">
<input type="text" ng-model="cc" render/>
<button ng-click="ccc()">Change phone number</button>
{{cc}}
<script src="../bower_components/angular/angular.js"></script>
<script>
    angular.module('myApp', [])
            .directive('render', function () {
                return {
                    restrict: 'A',
                    scope: {},
                    priority: 1,
                    require: '?ngModel',
                    link: function (scope, element, attrs, ngModel) {
                        ngModel.$render = function () {//用了render就要自己控制值
                            element.val(ngModel.$modelValue);
                            console.info(ngModel.$modelValue+"@"+ngModel.$viewValue);
                        }
                    }
                }
            })
            .controller('myCtrl', ['$scope', function ($scope) {
                $scope.cc = 'cc';
                $scope.ccc= function () {
                    $scope.cc='asdf';
                }
            }]);

</script>
</body>
</html>
``
