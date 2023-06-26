# Упатство за подесување на Veyon софтвер за во кабинет по информатика
## I. Професорски компјутер

## Чекор 1:
Се инсталира софтверот Veyon комплетно со штиклирање на Master i Configurator

## Чекор 2: 
Во Configurator кога ќе се отвори прозорецот:
A. Во полето General:
- Во Language се одбира  System Language Settings
- Во Method се одбира key file authentication
- Во Backend се одбира Builtin (PC and locations in localconf)
Б. Во  полето Service:
- Се селектираат:
   Show notification when an  unauthorized access is blocked 
   Show notification on remote connection
- Во VNC Server се одбира Builtin VNC Server
и се селектира Enable multi monitor support
В. Во полето Master се останува како што е, освен по желба на професорот може да се одредат боите на позадината и бојата на текстот.
Г. Во полето Access Control:
Во user groups backend се одбира Default (system user groups)
Се селектира Grant access to every authenticated user (default)
Д. Во полето Authentication keys :
Се генерира пар на клучови со притискање на копчето Create key pair
и потоа пишење на име на клучовите. Се генерираат два вида на клучови и тоа Private за на професорскиот компјутер и Public за на ученичките компјутери
За пренесување на public клучот во ученичките компјутери сe селектира клучот и се притиска на копчето Export key и се одбира на локација каде ќе се сними примерок од клучот која потоа се импортира во секој ученички компјутер.
Ѓ. Во полето Locations & computers:
- Се креира група на компјутери со притискање на копчето со знакот + од полето Locations и потоа со клик на името New Group  се променува името на групата.
- Се креираат компјутери со притискање на копчето + од полето Computers и со двоклик се променува името на компјутерот во Name
   Во host adress/IP се внесува hostname од сите ученички компјутери доколку не се работи со статични IP адреси , односно доколку се работи со статични IP адреси може да се внесат статичните адреси на компјутерите.
Е. И на крај се притиска копчето Apply (препорачливо е после секоја промена во било кое поле да се притиска копчето поради поголема сигурност од запамтување на промените).

## II. Ученички компјутер

## Чекор 1:
Да се сменат корисничките имиња (user name) и имињата на компјутерите (hostname) на учениците (на пр. hostame: UcenikPc-1 UcenikPc-2 ... ; user name: ucenik1 ucenik2 ......).

## Чекор 2: 
На секој ученички компјутер се инсталира софтверот Veyon само како Configurator

## Чекор 3:
Во Configurator кога ќе се отвори прозорецот:
А. Во полето General се подесува како во професорскиот компјутер
Б. Во полето Service се подесува како во професорскиот компјутер
В. Во полето Master се останува како што е, освен по желба на професорот може да се одредат боите на позадината и бојата на текстот.
Г. Во полето Access Control се подесува како во професорскиот компјутер
Д. Во полето Authentication Keys со притискање на копчето Import се импортира/внесува  претходно генрираниот клуч од професорскиот компјутер.
Ѓ. И на крај се притиска Apply (препорачливо е после секоја промена во било кое поле да се притиска копчето поради поголема сигурност од запамтување на промените).