#  Перечень автоматизируемых сценариев 

   ##### Предусловие - Открыт сервис покупки тура по адресу http://localhost:8080 , выбран 1 из методов оплаты(КУПИТЬ,т.е. оплата банковской картой или КУПИТЬ В КРЕДИТ,т.е. получение кредита на банковскую карту)

#### Валидные данные для тестирования полей 

- номер карты -ввод 16 арабских цифр

- срок действия- текущий месяц и 2 последние цифры текущего года арабскими цифрами

- владелец - фамилия и имя ,с пробелом между ними, латиницей

- CVC/CVV - 3 арабские цифры


Предполагаемые тестовые сценарии:
### 1. Проверка покупки тура через кнопку КУПИТЬ,т.е. банковской картой клиента

1.1 Оплата дествующей банковской картой
   - заполнить все поля валидными значениями ,отправить заявку
   - ОР - оплата тура прошла успешно.Запись в базу данных в таблицу со статусом APPROVED

1.2. Оптата не действующей банковской картой (карта заблокирована банком)
 - заполнить все поля валидными значениями ,отправить заявку
 - ОР - оплата тура не прошла, появлось сообщение об ошибке.Запись в базу данных в таблицу со статусом DECLINED.

 1.3. Оптата не действующей банковской картой (срок дейсвия карты истек)
- заполнить все поля валидными значениями ,указать месяц срока действия карты месяцем ранее  текущего месяца ,отправить заявку
- ОР - оплата тура не прошла, появилось сообщение о б ошибке.


 ### 2. Проверка покупки тура через кнопку КУПИТЬ В КРЕДИТ,т.е. получение кредита на оплату тура на банковскую карут клиента

2.1 Получение кредита на  дествующую банковскую карту
   - заполнить все поля валидными значениями ,отправить заявку
   - ОР - кредит предоставлен на карту,оплата тура прошла успешно.Запись в базу данных в таблицу со статусом APPROVED

2.2. Получение кредита на не действующую банковскую карту (карта заблокирована банком)
 - заполнить все поля валидными значениями ,отправить заявку
 - ОР -кредит не предоставлен на карту оплата тура не прошла, появлось сообщение об ошибке.Запись в базу данных в таблицу со статусом DECLINED.

2.3. Получение кредита на не действующую банковскую карту(срок дейсвия карты истек)
 - заполнить все поля валидными значениями ,указать месяц срока действия карты месяцем ранее  текущего месяца ,отправить заявку
- ОР - кредит не предоставлен на карту оплата тура не прошла, появлось сообщение об ошибке.


 ### 3. Общие проверки 
 3.1. Отправка формы со всеми пустыми полями
- оставить все поля пустыми ,нажать отправить
- ОР - появляется сообщение - "Ошибка,заполните необходимые поля "

3.2. Отправка формы с пустыми полем НОМЕР КАРТЫ
- заполнить заявку валидными значениями,но НОМЕР КАРТЫ оставить пустым ,нажать отправить
- ОР - появляется сообщение - "Ошибка,заполните необходимые поля "

3.3. Отправка формы с пустыми полем СРОК ДЕЙСТВИЯ
- заполнить заявку валидными значениями,но СРОК ДЕЙСТВИЯ оставить пустым ,нажать отправить
- ОР - появляется сообщение - "Ошибка,заполните необходимые поля "

3.4. Отправка формы с пустыми полем ВЛАДАЛЕЦ
- заполнить заявку валидными значениями,но ВЛАДЕЛЕЦ оставить пустым ,нажать отправить
- ОР - появляется сообщение - "Ошибка,заполните необходимые поля "

3.5. Отправка формы с пустыми полем CVC/CVV
- заполнить заявку валидными значениями,но CVC/CVV оставить пустым ,нажать отправить
- ОР - появляется сообщение - "Ошибка,заполните необходимые поля "

  
3.6. Заполнение поля Номер карты не валидными значениями (буквами)
- ввести в поле номер карты буквы
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле номер карты подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.7. Заполнение поля Номер карты не валидными значениями (спец символами,например ++++)
- ввести в поле номер карты спец символы ++++
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле номер карты подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.8. Заполнение поля Номер карты не валидными значениями (пробелами)
- заполнить поле номер карты пробелами
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле номер карты подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.9. Заполнение поля Номер карты 16 нулями
- заполнить поле номер карты 16 нулями
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле номер карты подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.10. Заполнение поля мясяц срока действия буквами
- ввести в поле срок действия буквы
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле срок действия подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.11. Заполнение поля год срока действия буквами
- ввести в поле год срока действия буквы
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле срок действия подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.12. Заполнение поля месяц срока действия спец символами(например +++)
- ввести в поле месяц срока действия +++
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле срок действия подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.13. Заполнение поля год срока срок действия спец символами(например +++)
- ввести в поле год срока действия +++
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле срок действия подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.14. Заполнение поля месяц срока действия пробелами
- ввести в поле месяц срока действия пробелы
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле срок действия подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.15. Заполнение поля год срока действия пробелами
- ввести в поле год  срока действия пробелы
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле срок действия подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.16. Заполнение поля месяц срока действия нулями (00)
- ввести в поле срок действия 00
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле срок действия подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

  
3.17. Заполнение поля год срока действия нулями (00)
- ввести в поле срок 00
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле срок действия подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.18. Заполнение поля Владелец цифрами
- ввести в поле владелец цифры
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле владелец подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.19. Заполнение поля Владелец кириллицей
- ввести в поле владелец фамилию и имя кириллицей
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле владелец подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.20. Заполнение поля Владелец пробелами
- ввести в поле владелец пробелы
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле владелец подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.21. Заполнение поля Владелец спец символами (например ***)
- ввести в поле владелец ***
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле владелец подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.22. Заполнение поля CVC/CVV буквами
- ввести в поле CVC/CVV буквы
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле CVC/CVV подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит


3.23. Заполнение поля CVC/CVV спец символами (например +++)
- ввести в поле CVC/CVV +++
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле CVC/CVV подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.24. Заполнение поля CVC/CVV пробелами
- ввести в поле CVC/CVV пробелы
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле CVC/CVV подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.25. Заполнение поля CVC/CVV нулями
- ввести в поле CVC/CVV 000
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле CVC/CVV подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

3.26. Заполнение поля месяц срока действия  цифрой более 12 
- ввести в поле месяц цифру 13
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле срок действия подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

 3.27. Заполнение поля год срока действия  годом текущий год+6 лет
- ввести в поле год срока действия 2029 год
- остальные поля заполнить валидными данными 
- нажать оправить
- ОР - поле срок действия подчеркивается красным цветом, появляется сообщение об ошибке,отправка формы не происходит

# Перечень используемых инструментов с обоснованием выбора
- Intel IDEA - програма для написания кода и проведения тестирования
- Git -система контроля версий
- Git Hub - система для размещения проекта 
- Java -язык программирования,необходимый для написания кода
- JUnit5 - это фреймворк для языка программирования Java, предназначенный для автоматического тестирования программ
- Gradle - система автоматической сборки.
- Selenide - это автоматизированная система тестирования программного обеспечения, используемая для написания программных кодов, которая помогает создавать и отправлять HTTP-запросы на Server/Grid
- Allure- это инструмент для создания отчетов о результатах тестирования в автоматизированных тестовых сценариях.
- Lombok -это библиотека для сокращения кода в классах и расширения функциональности языка Java
- Faker- это библиотека, которая позволяет генерировать случайные данные
- Google Chrome- браузер ,необходимый для визуализиции тестирования и запуска необходимых программ,посика инфориации
- Docker -это платформа, которая позволяет упаковать в контейнер приложение со всем окружением и зависимостями, а затем доставить и запустить его в целевой системе.

  
  # Перечень и описание возможных рисков при автоматизации
  - проблемы с техникой,Интернетом
  - не верно настроенные и выбранные инструменты для работы
  - сложности в написании автотестов (т.к.в процессе обучения были большие трудности с этим)


  # Интервальная оценка с учётом рисков в часах
  60 часов


  # План сдачи работ: когда будут готовы автотесты, результаты их прогона
 Написание   автотестов: ориентировочно до 22.12.
 Оформление результатов:ориентировочно до 27.12.


 
  
 

  
  
  





