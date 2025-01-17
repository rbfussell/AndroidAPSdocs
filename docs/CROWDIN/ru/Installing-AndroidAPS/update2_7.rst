Необходимые проверки после обновления с AndroidAPS 2.6
***********************************************************

* Программный код был существенно изменен при переходе на AAPS 2.7. 
* Поэтому важно проверить и/или изменить настройки после обновления.
* Подробнее о новых и расширенных функциях смотрите в <../Installing-AndroidAPS/Releasenotes.html#version-2-7-0>`_.

Проверяем источник ГК
-----------------------------------------------------------
* Проверьте, корректен ли источник ГК после обновления.
* При использовании `xDrip+ <../Configuration/xdrip.html>`_ возможно, что источник ГК изменится на приложение Dexcom (модифицированное).
* Откройте конфигуратор `Config builder <../Configuration/Config-Builder.html#bg-source>`_ (сэндвич-меню в левом верхнем углу главного экрана)
* Прокрутите вниз до "источник ГК".
* Выберите правильный источник ГК.

.. изображение:../images/modules.png
  :alt: источник ГК

Завершаем экзамен
-----------------------------------------------------------
* AAPS 2.7 содержит новую цель 11 для `автоматизации <../Usage/Automation.html>`_.
* Для прохождения `цели11 необходимо завершить экзамен (`цели 3 и 4 <../Usage/Objectives.html#objective-3-prove-your-knowledge>`_) <../Usage/Objectives.html#objective-11-automation>`__.
* Если например, вы не прошли `цель 3 <../Usage/Objectives. tml#objective-3-prove-your-knowledge>`_ у вас не получится начать `цель 11 <../Usage/Objectives.html#objective-11-automation>`__. 
* Это не повлияет на другие цели, которые вы уже выполнили. У вас сохранятся все завершенные цели!

Установите главный пароль
-----------------------------------------------------------
* Необходимо, чтобы можно было `экспортировать настройки <../Usage/ExportImportSettings.html>`_ в том виде, в каком они зашифрованы начиная с версии 2.7.
* Откройте настройки, нажав три точки меню в верхней правой части главного экрана
* Нажмите на треугольник под "General"
* Нажмите "Главный пароль"
* Введите пароль, подтвердите пароль и нажмите кнопку Ok.

.. изображение:: ../images/MasterPW.png
  :alt: Установить основной пароль
  
Экспорт настроек
-----------------------------------------------------------
* AAPS 2.7 использует новый зашифрованный формат резервного копирования. 
* после обновления до версии 2.7 следует `экспортировать настройки <../Usage/ExportImportSettings.html>`_.
* Импорт настроек из предыдущих версий возможен только в AAPS 2.7. Экспорт будет в новом формате.
* Не забудьте сохранить экспортированные настройки не только на телефоне, но и по крайней мере в одном безопасном месте (на ПК, в облачном хранилище...).
* Если вы собираете AAPS 2.7 с тем же хранилищем ключей, что и в предыдущих версиях, вы можете установить новую версию, не удаляя предыдущую. 
* Все настройки, а также завершенные цели останутся такими же, как и в предыдущей версии.
* In case you have lost your keystore build version 2.7 with new keystore and import settings from previous version as described in the `troubleshooting section <../Installing-AndroidAPS/troubleshooting_androidstudio.html#lost-keystore>`_.

Autosens (Hint - no action necessary)
-----------------------------------------------------------
* Autosens is changed to a dynamic switching model which replicates the reference design.
* Autosens will now switch between a 24 and 8 hours window for calculating sensitivity. It will pick which ever one is more sensitive. 
* If users have come from oref1 they will probably notice the system may be less dynamic to changes, due to the varying of either 24 or 8 hours of sensitivity.

Set Pump Password for Dana RS (if using Dana RS)
-----------------------------------------------------------
* Pump password for `Dana RS <../Configuration/DanaRS-Insulin-Pump.html>`_ was not checked in previous versions.
* Open Preferences (three-dot-menu on top right of screen)
* Scroll down and click triangle next to "Dana RS".
* Click "Pump password (v1 only)"
* Enter pump password (`Default password <../Configuration/DanaRS-Insulin-Pump.html#default-password>`_ is different depending on firmware version) and click OK.

.. image:: ../images/DanaRSPW.png
  :alt: Set Dana RS password
  
To change password on Dana RS follow instructions on `DanaRS page <../Configuration/DanaRS-Insulin-Pump.html#change-password-on-pump>`_.
