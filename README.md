[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-green.svg)](http://creativecommons.org/licenses/by-nc-sa/4.0/)


# pi-detector
Распознавание лица строиться на использовании AWS и Pi-Timolo.

### Описание
Pi-детектор используется с  [Pi-Timolo](https://github.com/pageauc/) для поиска движения на видео изображении, для распознавания и совпадений лиц, путем использования AWS Rekognition. В текущем состоянии совпадения записываются в event.log. При желании Вы можете отправить уведомление или разрешить/запретить доступ в комнату с минимальными изменениями. Скрипт установки поместит соответствующие файлы в /etc/rc.loal для запуска при загрузке.  

### Требование к конструкции
Raspberry Pi (или аналогичные платы) <br />
Picamera <br />
AWS Rekognition Access (доступен бесплатный тариф) <br />

В качестве альтернативы, этот набор скриптов может быть изменен для просмотра любой директории, содержащей изображения. Например, если вы собираете изображения с другой камеры и сохраняете их на диск, вы можете изменить путь к изображению, чтобы запустить распознавание лица против любой созданной новой фотографии.

### Установка
Установите Rasbian по инструкции <br />
https://robotos.in/uroki/ustanovka-raspbian-s-pomoshchyu-noobs <br />

Скопируйте это repo и установите:<br />
git clone https://github.com/robotoss/Pi-Detector.git<br />
cd pi-detector/scripts<br />
sudo chmod +x install.sh<br />
sudo ./install<br />

### Полная инструкция

Доступна - https://robotos.in/uroki/raspoznavanie-litsa-na-raspberry-pi-s-pomoshchyu-amazon-rekognition
