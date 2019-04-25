# VKUserInfo
VK_UserInfo.exe - консольное приложение для системы Windows, написанное на C++, которое позволяет:

1) Собирать информацию о пользователях социальной сети VK:
     - основная информация о пользователе,
     - статус пользователя,
     - подписчики,
     - друзья,
     - группы,
     - фотографии и посты на стене (с информацией о всех пользователях, оставивших комментарии и поставивших лайки).

2) Отслеживать изменения на страницах пользователей за определенный срок времени:
     - новая/устаревшая информация о пользователе,
     - новый/устаревшая статус,
     - новые/удалившиеся подписчики,
     - новые/удалившиеся друзья,
     - новые/удаленные группы,
     - новые/удаленные фотографии и посты на стене (в том числе новые/удаленные лайки и комменарии).
     
3) Выявлять взаимную активность двух пользователей:
     - общие друзья,
     - общие группы,
     - лайки и комментарии пользователей под фотографиями/на стенах друг друга.

Собранная информация помещается в папку 'userdata', а именно:
1) Информация о пользователе загружается в папку, название которой соответствует дате сбора данных в формате: 
     - userdata/06.01.2019/Имя_Фамилия[id123456789].txt, где 06.01.2019 - дата сбора данных, Имя_Фамилия - соответственно имя и фамилия пользователя в VK, 123456789 - id пользователя в VK.
2) Изменения на станице пользователя за период времени, например, с 0.01(01.01.2018) по 23.59(30.12.2018) загружаются в папку 'comparison' в формате:
     - userdata/comparison/Имя_Фамилия[id123456789][0.01(01.01.2018)-23.59(30.12.2018)].txt, где Имя_Фамилия - соответственно имя и фамилия пользователя в VK, 123456789 - id пользователя в VK, 0.01(01.01.2018) - дата первого среза информации о пользователе (которая уже должна существовать по адресу 'userdata/01.01.2018/Имя_Фамилия[id123456789].txt'), 23.59(30.12.2018) - дата, когда собираются данные об изменениях на странице.
   То есть для получения изменений на странице пользователя необходимо наличие собранной ранее информации об этом пользователе.
3) Взаимная активность пользователей загружается в папку 'activity' в формате:
     - userdata/activity/Имя1_Пользователя1[1]_Имя2_Пользователя2[2].txt, где Имя1_Пользователя1 и Имя2_Пользователя2 - имена и фамилии пользователей в VK
   При этом необходимо, чтобы информаиция о пользователях уже была закачена ранее.

При этом загрузка информации производится с помощью токена, располагающегося по адресу 'token/token.txt'. При этом при начале использования программы пользователю будет необходимо ввести свой токен, который соответственно будет помещен по указанному адресу. Позже при выборе опции 'Default token' токен будет автоматически загружаться для использования из указанного файла.
Все данные собираются в формате JSON и актуальны для версии токена 5.65.

Примечание:

VK_UserInfo[.txt].exe - все данные собираются в формате JSON и сохраняются в файлы с расширением .txt
VK_UserInfo[.json].exe - все данные собираются в формате JSON и сохраняются в файлы с расширением .json 