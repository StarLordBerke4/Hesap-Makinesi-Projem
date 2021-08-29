<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>Hesap Makinesi Projem</title>
	<style>
		.sayfa{
			
			width:360px;
			margin:auto;
		}
		table{
			background:black;
			border-spacing: 10px;
			text-align: center;
		}
		
		table .btn{
			width: 60px;
			background:white;
			text-align: center;
			line-height: 60px;
			color:black;
			font-size: 1.5em;
		}
		#islem, #gosterge{
			padding:5px;
			text-align: right;
		}
		
		#gosterge{
			height: 60px;
			background:#ddfafa;
			color:#333;
			font-size: 1.8em;
			text-align: right;
			line-height: 40px;
			padding:10px;
			box-sizing: border-box;
		}
		#islem{
			background: yellow;
		}
	</style>
</head>
 
<body>
	<div class="sayfa">
		<h1>Hesap Makinesi</h1>
		<table>
			<tr>
				<td colspan="5" id="islem"></td>
			</tr>
			<tr>
				<td colspan="5" id="gosterge">0</td>
			</tr>
			<tr>
				<td class="btn btnRakam">7</td>
				<td class="btn btnRakam">8</td>
				<td class="btn btnRakam">9</td>
				<td class="btn btnOpt">/</td>
				<td class="btn btnCE">CE</td>
			</tr>
			<tr>
				<td class="btn btnRakam">4</td>
				<td class="btn btnRakam">5</td>
				<td class="btn btnRakam">6</td>
				<td class="btn btnOpt">*</td>
				<td class="btn btnC">C</td>
			</tr>
			<tr>
				<td class="btn btnRakam">1</td>
				<td class="btn btnRakam">2</td>
				<td class="btn btnRakam">3</td>
				<td class="btn btnOpt">-</td>
				<td rowspan="2" class="btn btnEsit">=</td>
			</tr>
			<tr>
				<td colspan="2" class="btn btnRakam">0</td>
				<td class="btn btnNokta">.</td>
				<td class="btn btnOpt">+</td>
			</tr>
		</table>
	</div>
	<script>
    
    var optDurum=false,opt="",sonuc=0;
    
    var btnRakam=document.querySelectorAll(".btnRakam");
    var gosterge=document.querySelector("#gosterge");
    var btnOpt=document.querySelectorAll(".btnOpt");
    var islem=document.querySelector("#islem");
    var btnC=document.querySelector(".btnC");
    var btnCE=document.querySelector(".btnCE");
    var btnEsit=document.querySelector(".btnEsit");
    var btnNokta=document.querySelector(".btnNokta");
    
    btnRakam.forEach(function(element){
    
       element.onclick=function(e){
       
       if(gosterge.textContent=="0" || optDurum)
           gosterge.textContent="";
           
       gosterge.textContent+=this.textContent;
       optDurum=false;
       
       }
    });
    
    btnOpt.forEach(function(element){
       element.onclick=function(e){
           optDurum=true;
           var yeniOpt=this.textContent;
           
           islem.textContent=islem.textContent+" "+gosterge.textContent+" "+yeniOpt;
           
           switch(opt)
           {
               case "+":gosterge.textContent=(sonuc + Number(gosterge.textContent));break;
               case "-":gosterge.textContent=(sonuc - Number(gosterge.textContent));break;
               case "*":gosterge.textContent=(sonuc * Number(gosterge.textContent));break;
               case "/":gosterge.textContent=(sonuc / Number(gosterge.textContent));break;
               default:break;
           }
           
           sonuc=Number(gosterge.textContent);
           opt=yeniOpt;
       }
    
    });
		
        btnC.onclick=function(e){
           gosterge.textContent="0";
        
        }
        
        btnCE.onclick=function(e){
           gosterge.textContent="0";
           islem.textContent="";
           sonuc=0;
           opt="";
        
        }
        btnEsit.onclick=function(e)
        {
            İslem.textContent="";
            optDurum=true;
            
             switch(opt)
           {
               case "+":gosterge.textContent=(sonuc + Number(gosterge.textContent));break;
               case "-":gosterge.textContent=(sonuc - Number(gosterge.textContent));break;
               case "*":gosterge.textContent=(sonuc * Number(gosterge.textContent));break;
               case "/":gosterge.textContent=(sonuc / Number(gosterge.textContent));break;
               default:break;
           }
           sonuc=Number(gosterge.textContent);
           gosterge.textContent=sonuc;
           sonuc=0;
           opt="";
        }
        btnNokta.onclick=function(e)
        {
            if(!optDurum && !gosterge.textContent.includes("."))
            {
                gosterge.textContent+=".";
            }
            else if(optDurum)
            {
                gosterge.textContent="0";
            }
            if(!gosterge.textContent.includes("."))
            {
                gosterge.textContent+=".";
            }
            optDurum=false;
        }
	</script>
</body>
</html>