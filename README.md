soon.js
need include css/soon.min.css 
need include js/soon.min.js

Documentation: http://sooncountdown.com/docs.html#topic-quick-setup-using-jquery 

Options:

For cookie

$(document).ready(function(){ var element = document.getElementById('timer');
var dateEnd; console.log($.cookie("timer")); if($.cookie("timer")) { dateEnd = $.cookie("timer"); 
} else { dateEnd = new Date(); dateEnd.setMinutes(dateEnd.getMinutes()+9); $.cookie("timer", dateEnd, {expires: null});
dateEnd = 'in 9 minutes'; };
var options = { due: dateEnd, layout: 'label-small', face: 'slot', format: 'h,m,s,ms', labelsGours: "Часы,Часов", labelMinutes: "Минуты,Минут", labelsSeconds: "Секунды,Секунд", labelsMilliseconds: "Милисекунд" };
// $('#timer').soon().create(options); Soon.create(element, options); });
