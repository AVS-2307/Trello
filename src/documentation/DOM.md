# Класс Dom

Класс DOM предназначен для работы с DOM-элементами, а именно:
* создание и удаление элементов
* добавление и удаление элементов со страницы
* добавления обработчиков событий на элементы и их обработка


## Структура класса:
1. Общие методы
	* constructor(classContainer, svgCollection)
	* init()
	* initListener()

2. Методы работы с хранилищем
	* createObj(section)
	* getData()
	* displayData(arrData)

3. Методы создания элементов
	* createEl(typeEl, classEl = null, content = null)
	* createTextarea(buttonName)
	* createTask(content, className = 'task')
	* createSection(title, className = 'task-section')
	* createSectionHeader(name)
	* createSectionFooter()
	* createImageBlock(files)
	* createAddSectionButton()
	* createSVG(svgObject, className)

4. Методы обработчиков события и их назначения
	* addListener(el, typeEvent, func, additional = null)
	* footerBntHandler(event)
	* textareaBtnAddHandler(event)
	* textareaBtnCloseHandler(event)
	* taskBtnCloseHandler(event)
	* taskMouseoverHandler(event)
	* taskMouseoutHandler(event)
	* inputImgHandler(event)
	* addSectionButtonHandler(event)

## Краткое описание методов:

### Общие методы:
1. **constructor(classContainer, svgCollection)** - В методе происходит привязка контейнера, в котором будут располагаться секции с задачами, а также привязка коллекции svg-изображений и объявление массива с названием основных секций, используемых для первой инициализации

2. **init()** - метод инициализации. Располагает основные секции в привязанном контейнере, а также запускает метод добавления слушатели на кнопки добавления задач, кнопку добавления новой секции и на input добавления картинки в карточку задачи

3. **initListener()** - метод инициализации изначальных слушателей


### Методы работы с хранилищем:
1. **createObj(section)** - метод формирования объекта секции с задачами для дальнейшего сохранения в LocalStorage. Формирует объект вида:
```
 obj= {
	classSect: // Класс секции
	titleSect: // Название секции
	tasksArr: [ // Массив задач в секции
		{
			className: // Класс задачи
			content: // Текст задачи
		}
	]
}
```

2. **getData()** - Метод получения массива объектов секции для сохранения в localStorage

3. **displayData(arrData)** - Метод отображения секций, хранящихся в локальном хранилище, в привязанном контейнере


### Методы создания элементов
1. **createEl(typeEl, classEl = null, content = null)** - Метод сохдания элемента. Создает элемент типа typeEl с классом classEl, который может и отсутствовать и контентом, который также может отсутствовать

2. **createTextarea(buttonName)** - Метод создания блока с полем ввода новой задачи или имени новой секции. Создает блок, в котором находится textarea и блок с кнопками. Одна кнопка - добавления задачи/секции с контентом buttonName и вторая кнопка закрытия с иконкой закрытия

3. **createTask(content, className = 'task')** - Метод создания карточки задачи. Создает пункт меню с классом className, в котором находится блок с абзацем , в котором храниться описание хадачи content, а также кнопкой удаления задачи. Также добавляет слушатель событий mouseover, mouseout над задачей, а также клика по кнопке удаления задачи

4. **createSection(title, className = 'task-section')** - Метод создания секции с задачами с классом className. Секция состоит из шапки секции, в которой хранится название секции title. Контейнера с задачами, в котором находится ненумерованный список и подвалом секции с кнопками добавления задач и input для добавления картинки в карточку

5. **createSectionHeader(name)** - Метод создания шапки секции с именем секции name. В шапке находится также кнопка меню секции

6. **createSectionFooter()** - Метод создания подвала секции, в котором находится кнопка добавления задачи и удаления.

7. **createImageBlock(files)** - Метод создания блока с картинкой. Принимает files  создает блок с картинкой с src по первому элементу files

8. **createAddSectionButton()** - Метод создания кнопки добавления новой секции. Создает кнопку и добавляет ее в контейнер

9. **createSVG(svgObject, className)** - Метод создания кода SVG-изображения c слассом className для вставки на страницу. Данные для svg-картинки получаем из объекта коллекции svg-изображений


### Методы обработчиков события и их назначения
1. **addListener(el, typeEvent, func, additional = null)** - Метод добавления обработчика события typeEvent на элемент el, с функцией обработки события func и, если необходимо, дополнительными данными для передачи, которые могут остуствовать additional

2. **footerBntHandler(event)** - Метод обработки клика по кнопке добавления новой задачи в подвале секции. При клике появляется поле для ввода текста задачи

3. **textareaBtnAddHandler(event)** - Метод обработки клика по кнопке добавления новой задачи в секцию в блоке с полем ввода

4. **textareaBtnCloseHandler(event)** - Метод обработки клика по кнопке закрытия блока с полем для ввода новой задачи

5. **taskBtnCloseHandler(event)** - Метод обработки клика по кнопке удаления задачи. По клику удаляет задачу

6. **taskMouseoverHandler(event)** - Метод обработки события mouseover на задаче. При произшествии события делаем видимой кнопку удаления задачи

7. **taskMouseoutHandler(event)** - Метод обработки события mouseout на задаче. При произшествии события скрываем кнопку удаления задачи

8. **inputImgHandler(event)** - Метод обработки клика по элементу input в подвале страницы

9. **addSectionButtonHandler(event)** - Метод обработки клика по кнопке добавления новой секции. При клике появляется блок с полем ввода названия секции
