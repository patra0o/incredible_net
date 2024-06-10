# Instructions for multiple ad implementation

## Modify the script tag
For displaying three ads on the site
```
<script>
    var formdata1 = new FormData();
    formdata1.append("type", "Dark Square"); // These are the type of ad servers defined on the dashboard
    formdata1.append("tags", "tech, food,fashion"); // These are the categories you assign your ad

    var formdata2 = new FormData();
    formdata2.append("type", "Dark Square");
    formdata2.append("tags", "sports,fitness");

    var formdata3 = new FormData();
    formdata3.append("type", "Light Square");
    formdata3.append("tags", "technology,food");
```
### Add multiple ajax (Asynchronous Javascript) calls 
For each ad formdata that you create, also create an ajax call.

```
var ajax1 = new XMLHttpRequest();
    ajax1.addEventListener("load", completeHandler1, false);
    ajax1.open("POST", "https://ad.simaneka.com/api/get");
    ajax1.setRequestHeader("authorisation", "HwTHYpCv80Tj8JGFETHdMVJLE73kSeqZ");
    ajax1.send(formdata1);

    var ajax2 = new XMLHttpRequest();
    ajax2.addEventListener("load", completeHandler2, false);
    ajax2.open("POST", "https://ad.simaneka.com/api/get");
    ajax2.setRequestHeader("authorisation", "HwTHYpCv80Tj8JGFETHdMVJLE73kSeqZ");
    ajax2.send(formdata2);

    var ajax3 = new XMLHttpRequest();
    ajax3.addEventListener("load", completeHandler3, false);
    ajax3.open("POST", "https://ad.simaneka.com/api/get");
    ajax3.setRequestHeader("authorisation", "HwTHYpCv80Tj8JGFETHdMVJLE73kSeqZ");
    ajax3.send(formdata3);
```
### Add multiple completeHandlers for each call to the api
For each call to the api, add a corresponding completeHandler.
```
 function completeHandler1(event) {
      var response = JSON.parse(event.target.responseText);
      document.querySelector('.advertIMG1').src = response.link;
      document.querySelector('.advertIMG1').alt = response.alt;
      document.querySelector('.anchorElement1').href = response.href;
    }

    function completeHandler2(event) {
      var response = JSON.parse(event.target.responseText);
      document.querySelector('.advertIMG2').src = response.link;
      document.querySelector('.advertIMG2').alt = response.alt;
      document.querySelector('.anchorElement2').href = response.href;
    }

    function completeHandler3(event) {
      var response = JSON.parse(event.target.responseText);
      document.querySelector('.advertIMG3').src = response.link;
      document.querySelector('.advertIMG3').alt = response.alt;
      document.querySelector('.anchorElement3').href = response.href;
    }
```
### Finally, integrate in html body
You can place your ads anywhere on the site. Just make sure to change the ```class=anchorElement(number)``` and ```class="advertIMG2 ```

```
 <a class="anchorElement1" href="#" target="_blank">
        <img class="advertIMG1 img-fluid" src="" alt="">
 </a>
 <a class="anchorElement2" href="#" target="_blank">
        <img class="advertIMG2 img-fluid" src="" alt="">
 </a>
 <a class="anchorElement3" href="#" target="_blank">
        <img class="advertIMG3 img-fluid" src="" alt="">
 </a>
```

# Complete script after modifications
```
<script>
    var formdata1 = new FormData();
    formdata1.append("type", "Dark Square");
    formdata1.append("tags", "tech, food,fashion");

    var formdata2 = new FormData();
    formdata2.append("type", "Dark Square");
    formdata2.append("tags", "sports,fitness");

    var formdata3 = new FormData();
    formdata3.append("type", "Light Square");
    formdata3.append("tags", "technology,food");

    var ajax1 = new XMLHttpRequest();
    ajax1.addEventListener("load", completeHandler1, false);
    ajax1.open("POST", "https://ad.simaneka.com/api/get");
    ajax1.setRequestHeader("authorisation", "HwTHYpCv80Tj8JGFETHdMVJLE73kSeqZ");
    ajax1.send(formdata1);

    var ajax2 = new XMLHttpRequest();
    ajax2.addEventListener("load", completeHandler2, false);
    ajax2.open("POST", "https://ad.simaneka.com/api/get");
    ajax2.setRequestHeader("authorisation", "HwTHYpCv80Tj8JGFETHdMVJLE73kSeqZ");
    ajax2.send(formdata2);

    var ajax3 = new XMLHttpRequest();
    ajax3.addEventListener("load", completeHandler3, false);
    ajax3.open("POST", "https://ad.simaneka.com/api/get");
    ajax3.setRequestHeader("authorisation", "HwTHYpCv80Tj8JGFETHdMVJLE73kSeqZ");
    ajax3.send(formdata3);


    function completeHandler1(event) {
      var response = JSON.parse(event.target.responseText);
      document.querySelector('.advertIMG1').src = response.link;
      document.querySelector('.advertIMG1').alt = response.alt;
      document.querySelector('.anchorElement1').href = response.href;
    }

    function completeHandler2(event) {
      var response = JSON.parse(event.target.responseText);
      document.querySelector('.advertIMG2').src = response.link;
      document.querySelector('.advertIMG2').alt = response.alt;
      document.querySelector('.anchorElement2').href = response.href;
    }

    function completeHandler3(event) {
      var response = JSON.parse(event.target.responseText);
      document.querySelector('.advertIMG3').src = response.link;
      document.querySelector('.advertIMG3').alt = response.alt;
      document.querySelector('.anchorElement3').href = response.href;
    }
  </script>
```