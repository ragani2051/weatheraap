var input = document.querySelector('.input_text');
var main = document.querySelector('#name');
var tempv = document.querySelector('.temp');
var desc = document.querySelector('.desc');
var icon1 = document.querySelector('.icon');
var button= document.querySelector('.submit');


button.addEventListener('click', function(name){
fetch('https://api.openweathermap.org/data/2.5/weather?q='+input.value+'&appid=671a98173ee3d12259e3b7ec748f1fe1&unit=imperial')
.then(response => response.json())
.then(data => {
  var temp1 = data['main']['temp'];
  temp1=(temp1-273.15).toFixed(2);
  var nameV = data['name'];
  var desc1 = data['weather'][0]['description'];
  var iconv =data['weather'][0]['icon'];

  main.innerHTML = nameV;
  desc.innerHTML = desc1;
  tempv.innerHTML = (temp1);
  icon1.innerHTML =iconv;
  input.value ="";

})

.catch(err => alert("Please enter correct city !"));
})