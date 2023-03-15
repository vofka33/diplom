Регистрация

Зарегистрировать пользователя может только администратор через административную модель, при регистрации необходимо 
отнести пользователя в соответствующую группу (Клиент, Сервисная организация, Менеджер).

Основные страницы

http://127.0.0.1:8000/
Начальная страница куда попадает неавторизованный пользователь (без авторизации остальные страницы недоступны).


http://127.0.0.1:8000/user/
После авторизации пользователь попадает на главную стрнаицу с информацией о машинах если пользователь авторизован как клиент показываются машины только для этого клиента, если пользователь авторизован как сервисная компания показываются только машины для этой сервисной компании, если пользователь является менеджером (состоит в группе Менеджер) показываются все машины и появляется кнопка перехода к спискам. 

http://127.0.0.1:8000/to/
Список всех ТО 

http://127.0.0.1:8000/complaint/
Список всех рекламаций 
    
http://127.0.0.1:8000/complaintlist/<int:machine_id>/
Список всех рекламаций по выбранной машине
							

http://127.0.0.1:8000/tolist/<int:machine_id>/
Список всех техобслуживаний по выбранной машине
    
Так же по всем вкладкам и страницам имеются кнопки на изменение, добавление и удаление доступ к ним возможен в зависимости 
от наличия авторизованного пользовател в одной из групп (Клиент, Сервисная компания, Менеджер) реализовано через LoginRequiredMixin.

Преход на главную страницу осуществляется кликом по логотипу.

Для Таблиц доступна фильтрация по полям в соответствии с ТЗ:
для таблицы «Машина»
	модель техники;
	модель двигателя;
	модель трансмиссии;
	модель управляемого моста;
	модель ведущего моста.
для таблицы «ТО»
	вид ТО;
	зав.номер машины;
	сервисная компания.
для таблицы «Рекламация»
	узел отказа;
	способ восстановления;
	сервисная компания.

Сортировка данных в Таблицах по умолчанию проводиться по полям (от нового к старому):
«дата отгрузки с завода» для таблицы «Машина»;
«дата проведения ТО» для таблицы «ТО»;
«дата отказа« для таблицы «Рекламации».

#Списки
Страница со списками доступна только для пользователей являющихся Менеджером соответствующая кнопка перехода
доступна (появляется) только если авторизованный пользователь являеся менеджером (состоит в группе Менеджер).
Так же менеджер может редактировать, добавлять или удалять списки.

#API
http://127.0.0.1:8000/api/machine/ Данные по таблице Машина

http://127.0.0.1:8000/api/to/ Данные по таблице ТО

http://127.0.0.1:8000/api/complaint/ Данные по таблице Рекламации

http://127.0.0.1:8000/openapi Автодокументация API

