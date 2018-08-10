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
git clone https://github.com/af001/pi-detector.git<br />
cd pi-detector/scripts<br />
sudo chmod +x install.sh<br />
sudo ./install<br />

### Getting started

First, you need to create a new collection on AWS Rekognition. Creating a 'home' collection would look like:

cd pi-detector/scripts<br />
python add_collection.py -n 'home'<br />

Next, add your images to the pi-detector/faces folder. The more images of a person the better results you will get for detection. I would recommend several different poses in different lighting.

cd pi-detector/faces<br />
python ../scripts/add_image.py -i 'image.jpg' -c 'home' -l 'Tom'<br />

I found the best results by taking a photo in the same area that the camera will be placed, and by using the picam. If you want to do this, I created a small python script to take a photo with a 10 second delay and then puts it into the pi-detector/faces folder. To use it:

cd pi-detector/scripts<br />
python take_selfie.py<br />

Once complete, you can go back and rename the file and repeat the steps above to add your images to AWS Rekognition. Once you create a new collection, or add a new image, two reference files will be created as a future reference. These are useful if you plan on deleting images or collections in the future.

To delete a face from your collection, use the following:

cd pi-detector/scripts<br />
python del_faces.py -i '000-000-000-000' -c 'home'<br />

If you need to find the image id or a collection name, reference your faces.txt and collections.txt files.

To remove a collection:

cd pi-detector/scripts<br />
python del_collections.py -c 'home'<br />

Note that the above will also delete all the faces you have stored in AWS. 

The last script is facematch.py. If you have images updated and just want to test static photos against the faces you have stored on AWS, do the following:

cd pi-detector/scripts<br />
python facematch.py -i 'tom.jpg' -c 'home'<br />

The results will be printed to screen, to include the percentage of similarity and confidence. 
