# Сеть LInTech
Проект посвящен сбору информации, реконструкции и исследованию учебного сетевого комплекса LInTech для компьютерных классов СССР.

## История
<img src="./Documentation/UKNC1.png" align="right" width="30%">

Комплекс был [разработан](https://dic.academic.ru/dic.nsf/ruwiki/46187#.D0.9C.D0.BE.D0.B4.D0.B5.D1.80.D0.BD.D0.B8.D0.B7.D0.B0.D1.86.D0.B8.D1.8F) в 1990-х гг. ООО «ЛИнТех» («Лаборатория информационных технологий») совместно с ООО «Алтер-Вест»
для модернизации существующих учебных классов на базе ПЭВМ Корвет, УКНЦ и БК0010 для изучения современного на тот момент ПО для IBM PC.

Обеспечивалась работа мест учеников в режимах локальной сети и в терминальном режиме.

Наиболее интересным и необычным для того времени является **терминальный режим**, в котором существующие места учеников становятся сетевыми терминалами для головной машины на базе IBM PC. 
Поддерживаются как режимы текстового терминала для изучения MS DOS, так и графического для изучения MS Windows 3.11. 

В режиме локальной сети ученикам предоставляется доступ к дискам головной машины, причем скорость работы заметно выше штатной учебной сети. 

Комплекс упоминается в [журналах](http://school136.perm.ru/sunduk/samos/info.htm) и документах 
министерства образования и был [рекомендован](http://web.archive.org/web/20070927175919/http://www.informika.ru/text/goscom/normdoc/d_96/PRIK~5/l155.html) к применению в школах.
Однако классы на базе ПЭВМ СССР на тот момент уже активно замещались западными PC, в том числе при активной поддержке западных производителей, 
в результате комплекс LInTech не успел получить широкого распространения и был практически утрачен.

В настоящее время ученические платы изредка встречаются в ПЭВМ, списаных из школ. Чаще всего это ПЭВМ Корвет, реже УКНЦ, также известно несколько экземпляров плат для БК. 
Долгое время не удавалось разыскать сетевую плату и ПО головной машины, без которых невозможна работа ни одной из этих сетей. 
На данный момент доподлинно известно о двух сохранившихся экземплярах головной платы и, возможно, еще одном.

Первый и пока единственный публично упомянутый запуск-реконструкция сети LInTech / NET-Rt11 осуществлены [Arseny](http://uknc.narod.ru/) для ПЭВМ УКНЦ (МС 0511). 
На его сайте представлены [качественные фото плат](http://uknc.narod.ru/Img/index.htm) и [комплект учительского ПО для УКНЦ](http://uknc.narod.ru/Net-RT11/index.htm).
Однако задача реконструкции комплекса на данном этапе была существенно затруднена отсутствием копии защищенной от чтения прошивки микроконтроллера головной платы.

Второй экземпляр головной платы и бумажную документацию удалось разыскать [Serebriakov](https://github.com/paulargent). 
Благодаря его усилиям были налажены контакты с разработчиками из ЛИнТех, получено оставшееся в архивах ПО и прошивки контроллера головной платы.
Это решило принципиальный вопрос с прошивками и сделало возможной дальнейшую реконструкцию системы. Также есть надежда, что со временем появится и электронная версия найденной документации.

Мне удалось разыскать и восстановить клиентские платы БК0010 и УКНЦ, найти около десятка контроллеров от платы головной машины (увы, без самих плат). 

Все это позволяет попробовать реконструировать и запустить сеть ЛИнТех.

## Реконструкция
[<img src="./Server-IBM-PC/KiCad/LinTech-GM-board_NC-ACM-2.2.png" height="250px" margin="15px">](./Server-IBM-PC/)[<img src="./Terminal-UKNC/KiCad/LInTech-UKNC.png" height="250px">](./Terminal-UKNC/)

Аппаратно комплекс реализован в виде клиентских плат, устанавливаемых в слоты расширения ПЭВМ учеников, и головной ISA платы для учительской IBM PC совместимой машины. 
Платы построены на основе микроконтроллеров Intel 8031 и 8051.

Связь в сети осуществляется по последовательной двухпроводной линии, что позволяет использовать существующую кабельную инфраструктуру компьютерных классов.

В качестве программного обеспечения были разработаны системы: 
- [NET-Rt11](https://www.emuverse.ru/wiki/%D0%A3%D0%9A%D0%9D%D0%A6_%D0%B6%D1%83%D1%80%D0%BD%D0%B0%D0%BB_1994-01_%D0%9B%D0%98%D0%BD%D0%A2%D0%B5%D1%85), 
- [DOS-Line](http://www.uw.ru/about/archive/dos-line/), 
- [NET-CP/M](https://oldkorvet.narod.ru/Utils.html)
- NET-БК0010

В данном проекте представлены:
- [Server-IBM-PC](./Server-IBM-PC/) - головная **[ учительская плата ISA для IBM PC ]** а так же **учительское ПО**
- [Terminal-UKNC](./Terminal-UKNC/) - клиентская плата УКНЦ
- [Terminal-BK0010](./Terminal-BK0010/) - клиентская плата БК 0010
- [Documentation](./Documentation/) - руководства

Дружественные проекты:
- [Терминал плата для ПЭВМ Корвет](https://github.com/lordamot/retro-lintech) была реконструирована коллегами NexusOfPenza и Lordamot

Платы в данном проекте не являются точной копией оригинала т.к. некоторые участки плат не видны под установлеными компонентами и невозможно сделать точную копию без разрушения оригинала. 
Реконструкция создана в KiCad с чистого листа имея оригинальную плату (или ее фото) в качестве образца. 
Не видимые элементы воссозданы путем отсмотра, прозвонки и изучения/воссоздания логики работы платы. 

Все данные публикуются с согласия представителя ЛИнТех.

## Ссылки
1. [academic.ru: Что такое УКНЦ? см раздел "Модернизация"](https://dic.academic.ru/dic.nsf/ruwiki/46187#.D0.9C.D0.BE.D0.B4.D0.B5.D1.80.D0.BD.D0.B8.D0.B7.D0.B0.D1.86.D0.B8.D1.8F)
2. [Каталог статей об УКНЦ (а также, о разработках фирмы ЛИнТех)](http://school136.perm.ru/sunduk/samos/info.htm)
3. [«NET-Rt11» — СЕТЕВАЯ СИСТЕМА ДЛЯ КУВТ «УКНЦ» С IBM-СОВМЕСТИМОЙ ГОЛОВНОЙ МАШИНОЙ](https://www.emuverse.ru/wiki/%D0%A3%D0%9A%D0%9D%D0%A6_%D0%B6%D1%83%D1%80%D0%BD%D0%B0%D0%BB_1994-01_%D0%9B%D0%98%D0%BD%D0%A2%D0%B5%D1%85)
4. [Приказ Мин Обр 'О модернизации отечественных КУВТ "Корвет" и УКНЦ' N 155/28 от 13.05.96г](http://web.archive.org/web/20070927175919/http://www.informika.ru/text/goscom/normdoc/d_96/PRIK~5/l155.html)
5. [Многозадачная, многопользовательская операционная система DOS-Line](http://www.uw.ru/about/archive/dos-line/)
6. [uknc.narod.ru: Фото от Arseny](http://uknc.narod.ru/Img/index.htm)
7. [uknc.narod.ru: оригиналы инструкции и ПО УКНЦ от Arseny](http://uknc.narod.ru/Net-RT11/index.htm)
8. [Старые фото и описание плат ЛИнТех от Serebriakov на форуме zx-pk.ru](https://zx-pk.ru/threads/2597?p=922488&viewfull=1#post922488)
9. [Образы дискет с установщиком ЛИнТех от Serebriakov на его старом сайте по Корвету oldkorvet.narod.ru)](https://oldkorvet.narod.ru/Utils.html)
10. [Дружественный проект по реконструкции платы для ПЭВМ Корвет от коллег NexusOfPenza и Lordamot](https://github.com/lordamot/retro-lintech)
