
function output()
{
var a=document.getElementById("ara").value;
  a=a.toLowerCase();
document.getElementById("hide").style.display = "none";
if(a=="")
{
var name="Please enter movie name";
document.getElementById("error").innerHTML=name;

}
else
{
document.getElementById("error").innerHTML="";
  document.getElementById("hide").style.display = "block";
  $.getJSON('https://www.omdbapi.com/?apikey=def8c9a0&t='+encodeURI(a)).then(function (response){
console.log(response);
    var name=response.Title;
    var d=name.toLowerCase();
    var rele=response.Released;
    var ti  =response.Runtime;
    var gen =response.Genre;
    gen=gen.replace(",", "/");
    var plot1=response.Plot;
    var dirit=response.Director;
    var rate=response.imdbRating; 
    var mat,divi,cou,num;
    var er="Did You Mean";
    cou=ti.substring(0, 4);
    num=parseInt(cou)
    mat=num%60;
    divi=num/60;
    divi=parseInt(divi);
    var tot=" "+"-"+" "+divi+"h"+" "+mat+"m";
    if(d==a)
      {
    document.getElementById("title").innerHTML=name;
    document.getElementById("plot").innerHTML=plot1;
    document.getElementById("ini").innerHTML="<b>Initial release : </b>"+rele;
    document.getElementById("rel").innerHTML=rele.substring(rele.length-4,rele.length);
    document.getElementById("time").innerHTML=tot;
    document.getElementById("mov").innerHTML=" "+"-"+" "+gen;
    document.getElementById("Imdb").innerHTML=rate+"/10"+"<br><b>Imdb</b>";
    document.getElementById("dir").innerHTML="<b>Director : </b>"+dirit;
      }
      else
        {
          document.getElementById("error").innerHTML=er;
           document.getElementById("title").innerHTML=name;
           document.getElementById("plot").innerHTML=plot1;
           document.getElementById("ini").innerHTML="<b>Initial release : </b>"+rele;
           document.getElementById("rel").innerHTML=rele.substring(rele.length-4,rele.length);
           document.getElementById("time").innerHTML=tot;
           document.getElementById("mov").innerHTML=" "+"-"+" "+gen;
          document.getElementById("Imdb").innerHTML=rate+"/10"+"<br><b>Imdb</b>";
         document.getElementById("dir").innerHTML="<b>Director : </b>"+dirit;
        }
    
      });
}
}
