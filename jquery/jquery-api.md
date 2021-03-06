jQuery API
================================================================================

.add()
--------------------------------------------------------------------------------

> Добавялет элементы в набор.

    .add(selector)
    .add(elements)
    .add(html)
    .add(jQuery object)
    .add(selector, context)

`context` - часть документа, с которой селектор должен начать поиск.

.addBack([selector])
--------------------------------------------------------------------------------

> Добавляет предыдущий набор элементов в текущий рабор, опционально отфильтрованный с помощью селектора.

    $('#b2').next().addBack().css('background-color', 'red'); // Добавляет и 2 и 3

.addClass();
--------------------------------------------------------------------------------

> Добавляет класс к набору.

    addClass(className);

Функция принимает индекс текущего элемента в наборе и существующие классы и должна возвращать строку имен классов, разделенных запытыми.

    addClass(function (index, currentClass) {});

.after();
--------------------------------------------------------------------------------

> Вставляет содержимое, определенное параметром, после каждого элемента набора.

    .after(content[, content]);

Функция получает индекс текущего элемента и должна возвращать HTML-строку, DOM-элемент, или jQuery-объект.

.ajaxComplete()
--------------------------------------------------------------------------------

> Регистрирует обработчик, который будет вызван при выполнении Ajax-запроса.

    $(document).ajaxComplete(function(event, XMLHttpRequest, ajaxOptions) {
        $( ".log" ).text( "Triggered ajaxComplete handler." );
    });

.ajaxError()
--------------------------------------------------------------------------------

> Регистрирует обработчик, который вызывается при выполнении Ajax-запроса с ошибкой.

    $(document).ajaxError(function(event. jqXHR, ajaxSettings, thrownError) {
        $( "div.log" ).text( "Triggered ajaxError handler." );
    });

.ajaxSend()
--------------------------------------------------------------------------------

> Привязывает функцию, которая будет выполнена перед отправкой Ajax-запроса.

    $(document).ajaxSend(function(event, jqXHR, ajaxOptions) {
        $( ".log" ).text( "Triggered ajaxSend handler." );
    });

.ajaxStart()
--------------------------------------------------------------------------------

> Регистрирует обработчик, вызываемый при начале первого Ajax-запроса.

    $(document).ajaxStart(function() {
        $( ".log" ).text( "Triggered ajaxStart handler." );
    });

.ajaxStop()
--------------------------------------------------------------------------------

> Регистрирует обработчик, вызываемый при завершении выполнения всех Ajax-запросов.

    $( ".log" ).ajaxStop(function() {
        $(this).text( "Triggered ajaxStop handler." );
    });

.ajaxSuccess()
--------------------------------------------------------------------------------

> Привязывает функцию, выполняемую при успешном выполнении Ajax-запроса.

    $(document).ajaxSuccess(function(event, XMLHttpRequest, ajaxOptions) {
        $( ".log" ).text( "Triggered ajaxSuccess handler." );
    });

Селектор '*'
--------------------------------------------------------------------------------

> Выбирает все элементы.

.andSelf() (нерекомендуется, является псевдонимом для .addBack())
--------------------------------------------------------------------------------

> Добавляет предыдущий набор элементов в текущий набор.

.animate()
--------------------------------------------------------------------------------

> Выполняет пользовательскую анимацию набора CSS-свойств

Селектор ':animated'
--------------------------------------------------------------------------------

> Выбирает все элементы, которые в текущий момент находятся в процессе анимации.

.append()
--------------------------------------------------------------------------------

> Вставляет контент в конец каждого элемента набора.

    .append(content [, content ]);

Функция принимает индекс текущего элемента и старое HTML-значение элемента и возвращает HTML-строку, DOM-элементы или jQuery-объект.

    .append(function (index, html) {});

.appendTo()
--------------------------------------------------------------------------------

> Вставляет каждый элемент набора в конец целевого элемента.

    $('<p>Test</p>').appendTo('.inner');

.attr()
--------------------------------------------------------------------------------

> Получает значения атрибута для первого элемента набора или устанавливает один или несколько атрибутов для каждого элемента набора.

    .attr(attributeName); // Возвращает значение атрибута первого элемента набора.
    
    .attr(attributeName, value); // Устанавливает значение атрибута каждого элемента набора
    .attr(attributes); // Устанавливает значения несколько атрибутов (объект)

Функция получает индекс текущего элемента и текущее значение возвращает значение аттрибута.

    .attr(attributeName, function (index, attr) {});

Селектор [name|='value']
--------------------------------------------------------------------------------

> Выбирает элементы, которые имеют значение атрибута, равное или начинающееся с указанного.

Селектор [name*='value']
--------------------------------------------------------------------------------

> Выбирает элементы, которые содержат атрибут, значение которого содержат указанное.

Селектор [name~\'value']
--------------------------------------------------------------------------------

> Элемент с атрибутом, содержащим указанное слово (разделенное пробелами)

Селектор [name$='value']
--------------------------------------------------------------------------------

> Элемент с атрибутом, значение которого заканчивается указанным.

Селектор [name='value']
--------------------------------------------------------------------------------

> Элементы со значением атрибута, равным заданному.

Селектор [name!='value']
--------------------------------------------------------------------------------

> Элементы с атрибутами, не равными заданному значению.

Селектор [name^='value']
--------------------------------------------------------------------------------

> Элементы с атрибутами, значения которых начинаются с указанного.

.before()
--------------------------------------------------------------------------------

> Вставляет содержимое перед каждым элементом набора.

    .before(content[, content]);
    .before(function () {}); // Функция должна возвращать HTML, DOM или jQuery

--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



--------------------------------------------------------------------------------



