soon.js
need include css/soon.min.css 
need include js/soon.min.js

html
<div id="soon" class="soon"></div>

Documentation: http://sooncountdown.com/docs.html#topic-quick-setup-using-jquery 

Options:

For cookie

$(document).ready(function(){ var element = document.getElementById('timer');
var dateEnd; console.log($.cookie("timer")); if($.cookie("timer")) { dateEnd = $.cookie("timer"); 
} else { dateEnd = new Date(); dateEnd.setMinutes(dateEnd.getMinutes()+9); $.cookie("timer", dateEnd, {expires: null});
dateEnd = 'in 9 minutes'; };
var options = { due: dateEnd, layout: 'label-small', face: 'slot', format: 'h,m,s,ms', labelsGours: "Часы,Часов", labelMinutes: "Минуты,Минут", labelsSeconds: "Секунды,Секунд", labelsMilliseconds: "Милисекунд" };
// $('#timer').soon().create(options); Soon.create(element, options); });





soon.js with coockie and event function after finish

$(document).ready(function(){
// функция скрытия кнопки
function timerEnd() {
$('.ob1').css('display', 'none');
$('.ob2').css('display', 'block');
};
// 15 минутная задержка выполнения функции
// 1sec = 1000ms = 1 minute
setTimeout(function(){
timerEnd();
}, 900000)

var element = document.getElementById('soon');
var dateEnd;
console.log($.cookie("timer"));

if($.cookie("timer")) { // берем дату с куки, если есть и сравниваем истек ли таймер
dateEnd = $.cookie("timer");
var dateNov = Date.now();
var timeLeft = Date.parse(dateEnd) - dateNov;
setTimeout(function(){
timerEnd();
}, timeLeft)
if(timeLeft < 0){
timerEnd();
}
}

else { // устанавливаем дату окончания таймера и записываем ее в куки
dateEnd = new Date();
dateEnd.setMinutes(dateEnd.getMinutes()+15);
$.cookie("timer", dateEnd, {expires: null});
console.log(Date.parse(dateEnd));
dateEnd = 'in 15 minutes';
};

var options = { // настройки таймера
due: dateEnd,
layout: 'tight label-hidden',
face: 'slot',
format: 'm,s',
visual: 'ring color-light glow',
eventComplete:function(){ alert("done!")}
};

// создаем таймер
Soon.create(element, options);
});

