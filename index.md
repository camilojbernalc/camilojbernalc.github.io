<meta charset="utf-8">

<h1>Challenge 1 CoDec</h1>
<br>
<h2>Escriba el texto que desea encriptar o desencriptar</h2>
<textarea id="enc" rows="10" cols="50"></textarea>
<br><br>
<button id="crypt">Encriptar</button> 
<button id="decrypt">Desencriptar</button> 
<br><br>
<h2>Texto encriptado</h2>
<textarea id="output" rows="10" cols="50"></textarea>
<br><br>
<button id ="copy">Copiar</button>

<script>
	var getText = document.getElementById("enc");
	var cryptButton= document.getElementById("crypt");
	var decryptButton = document.getElementById("decrypt");
	var toCopy = document.getElementById("output");
	var copyButton = document.getElementById("copy")
	var word;
	var char=[];
	var out;
	function encrypt(){
		word = getText.value;
		char = Array.from(word); 		//array.from => para separar las letras de la palabra en un arreglo de una por una
		for (i=0;i<=char.length;i++){	//char.lenght => para tomar el tamaño del arreglo como limite
			if(char[i]=="a"){
				char[i]="ai";
			}else if(char[i]=="e"){
				char[i]="enter";
			}else if(char[i]=="i"){
				char[i]="imes";
			}else if(char[i]=="o"){
				char[i]="ober";
			}else if(char[i]=="u"){
				char[i]="ufat";
			}
		}
		out = char.join("");	// char.join => para unir las letras del arreglo en una palabra
		document.getElementById('output').innerHTML = out 	//para poder mostar
	}

	function decrypt(){
		word = getText.value;
		char= Array.from(word);
		var out1=[];
		for (i=0;i<=char.length;i++){
			if (char[i]=="a" && char[i+1]=="i"){
				char[i]="a";
				char.splice(i+1,1)
			}else if (char[i]=="e" && char[i+1]=="n" && char[i+2]=="t" && char[i+3]=="e" && char[i+4]=="r"){
				char[i]="e";
				char.splice(i+1,4)
			}else if(char[i]=="i" && char[i+1]=="m" && char[i+2]=="e" && char[i+3]=="s"){
				char[i]="i";
				char.splice(i+1,3);
			}else if(char[i]=="o" && char[i+1]=="b" && char[i+2]=="e" && char[i+3]=="r"){
				char[i]="o";
				char.splice(i+1,3);
			}else if(char[i]=="u" && char[i+1]=="f" && char[i+2]=="a" && char[i+3]=="t"){
				char[i]="u";
				char.splice(i+1,3);
			}
		}
		out = char.join("");
		document.getElementById("output").innerHTML = out
	}

	function getCopy(){
		textEnc = toCopy.value;
		navigator.clipboard.writeText(textEnc);		//para asignar la accion de copiar con el botón
		getText.value = "";
		document.getElementById("enc").innerHTML = getText
	}
	cryptButton.onclick=encrypt;
	decryptButton.onclick=decrypt
	copyButton.onclick=getCopy;

	

		
</script>
