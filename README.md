<!DOCTYPE html>

<html lang="en" xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="utf-8" />
    <title></title>
    <script>
      function RimToArab(Rimskoe) {
	var znachenie = 0;
	for (var i = 0; i < Rimskoe.length; i++) {
		if (Rimskoe[i] == "M") {
			znachenie += 1000
		}
		if (Rimskoe[i] == "D") {
			znachenie += 500
		}
		if (Rimskoe[i] == "C") {
			znachenie += 100
		}
		if (Rimskoe[i] == "L") {
			znachenie += 50
		}
		if (Rimskoe[i] == "X") {
			znachenie += 10
		}
		if (Rimskoe[i] == "V") {
			znachenie += 5
		}
		if (Rimskoe[i] == "I") {
			znachenie += 1
		}
		if (Rimskoe[i] + Rimskoe[i + 1] == "CM") {
			znachenie -= 200
		}
		if (Rimskoe[i] + Rimskoe[i + 1] == "CD") {
			znachenie -= 200
		}
		if (Rimskoe[i] + Rimskoe[i + 1] == "XC") {
			znachenie -= 20
		}
		if (Rimskoe[i] + Rimskoe[i + 1] == "XL") {
			znachenie -= 20
		}
		if (Rimskoe[i] + Rimskoe[i + 1] == "IX") {
			znachenie -= 2
		}
		if (Rimskoe[i] + Rimskoe[i + 1] == "IV") {
			znachenie -= 2
		}
		otvet = znachenie;
	}
}




function ArabToRim(Arabskoe) {
	var arNum = Arabskoe;
	let rimNum = '';
	while (arNum >= 1000) {
		rimNum += 'M';
		arNum -= 1000;
	}
	while (arNum >= 900) {
		rimNum += 'CM';
		arNum -= 900
	}
	while (arNum >= 500) {
		rimNum += 'D';
		arNum -= 500
	}
	while (arNum >= 400) {
		rimNum += 'CD';
		arNum -= 400
	}
	while (arNum >= 100) {
		rimNum += 'C';
		arNum -= 100
	}
	while (arNum >= 90) {
		rimNum += 'XC';
		arNum -= 90
	}
	while (arNum >= 50) {
		rimNum += 'L';
		arNum -= 50
	}
	while (arNum >= 40) {
		rimNum += 'XL';
		arNum -= 40
	}
	while (arNum >= 10) {
		rimNum += 'X';
		arNum -= 10
	}
	while (arNum >= 9) {
		rimNum += 'IX';
		arNum -= 9
	}
	while (arNum >= 5) {
		rimNum += 'V';
		arNum -= 5
	}
	while (arNum >= 4) {
		rimNum += 'IV';
		arNum -= 4
	}
	while (arNum >= 1) {
		rimNum += 'I';
		arNum -= 1
	}
	chiselko = rimNum;
};



function slozhenie() {
	var chleni = virazhenie.split('+');
	var chlen1 = chleni[0];
	var chlen2 = chleni[1];
	RimToArab(chlen1);
	let slagaemoe1 = otvet;
	RimToArab(chlen2);
	let slagaemoe2 = otvet;
	var summa = slagaemoe1 + slagaemoe2;
	ArabToRim(summa)
	var Raz = chiselko;
	if (Raz.length == 0) {
		alert("ошибка")
	} else {
		alert(Raz)
	};
}

function vichitanie() {
	var chleni = virazhenie.split('-');
	var chlen1 = chleni[0];
	var chlen2 = chleni[1];
	RimToArab(chlen1);
	let umenshaemoe = otvet;
	RimToArab(chlen2);
	let vichitaemoe = otvet;
	var raznost = umenshaemoe - vichitaemoe;
	ArabToRim(raznost);
	var Raz = chiselko;
	if (Raz.length == 0) {
		alert("ошибка")
	} else {
		alert(Raz)
	};
}

function umnozhenie() {
	var chleni = virazhenie.split('*');
	var chlen1 = chleni[0];
	var chlen2 = chleni[1];
	RimToArab(chlen1);
	let mnozhitel1 = otvet;
	RimToArab(chlen2);
	let mnozhitel2 = otvet;
	var proizvedenie = mnozhitel1 * mnozhitel2;
	ArabToRim(proizvedenie);
	var Raz = chiselko;
	if (Raz.length == 0) {
		alert("ошибка")
	} else {
		alert(Raz)
	};
}

function delenie() {
	var chleni = virazhenie.split('/');
	var chlen1 = chleni[0];
	var chlen2 = chleni[1];
	RimToArab(chlen1);
	let delimoe = otvet;
	RimToArab(chlen2);
	let delitel = otvet;
	if (delimoe == 0 || delitel == 0) {
		alert("ошибка");
		return
	}
	var chastnoe = delimoe / delitel;
	if (Number.isInteger(chastnoe) === false) {
		for (var i = 1; i <= delimoe; i++) {
			if (delimoe % i === 0 && delitel % i === 0)
				delimoeD = delimoe / i, delitelD = delitel / i;
		}
		ArabToRim(delimoeD);
		var Raz = chiselko;
		ArabToRim(delitelD);
		var Dva = chiselko;
		alert(Raz + "/" + Dva);
	} else {
		ArabToRim(chastnoe);
		var Raz = chiselko;
		alert(Raz)
	}
}

var virazhenie = prompt("Введите выражение");
if (virazhenie.indexOf("+") != -1) {
	slozhenie();
} else if (virazhenie.indexOf("-") != -1) {
	vichitanie();
} else if (virazhenie.indexOf("*") != -1) {
	umnozhenie();
} else if (virazhenie.indexOf("/") != -1) {
	delenie();
} else {
	alert("ошибка");
}
</script>
</head>
<body>

</body>
</html>
