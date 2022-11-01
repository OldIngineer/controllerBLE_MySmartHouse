			ПРОГРАММА: controller_ble
	для контроллера устройства управления системы "Умный дом", соединенной с сеть с помощью интерфейса BLE.
		1 Вкл.\выкл. исполнительных устройств произодится через посылку рекламы(адвертайзинга)
с узлового устройства сети RS485 расположенного в данном помещении.
	 После общего наименования локальной сети следует номер передающего узла BLE.
 Если номер заданный с помощью перемычек, совпадает с полученным номером,
 разрешается управление одним исполнительным устройством из указанного ниже списка.
 В полном локальном имени рекламы в конце три цифры\байта означают команду\число как сумму кодов:
- Выкл. = 0;
- Вкл. = 256;
- вкл.\выкл. мотор. = 1;
- вкл.\выкл. свет. = 2;
- вкл.\выкл. вода. = 4;
- вкл.\выкл. сирена.= 8;
- вкл.\выкл. отопление. = 16;
- вкл.\выкл. розетка. =32;
	Пример: "MySmartHouse_06_258" - означает включить свет.
		2 За основу взяты примеры:
	- работа с BLE "esp-idf/examples/bluetooth/bluedroid/ble/gatt_client";
	
	3 Содержимое файла sdkconfig.default взято из вышеуказанного примера

	Для формирования файла конфигурации указать Pyton расположение проекта, например,
cd C:\ESP32\Project\controller_ble
	Задать чип ESP32 в качестве объекта для компилирования
idf.py set-target esp32

	Изменение тактовой частоты MIN 80MHz командой для компилятора:
"idf.py menuconfig" в настройках таблицы: component config/ESP_specific/

	Использование только одного ядра "PRO_CPU" командой для компилятора:
"idf.py menuconfig" в настройках таблицы:
component config/FreeRTOS/Run FreeRTOS only on first core
	
   
