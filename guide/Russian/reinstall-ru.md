﻿<img align="right" src="../../assets/nabu.png" width="425" alt="Linux Running On A Xiaomi Pad 5">


# Windows на Xiaomi Pad 5

## Переустановка
### Переустановка Windows если что-то пошло не так

- Если текущая версия Windows не подходит или была испорчена, вероятно, Вам поможет переустановка Windows, благо это довольно простой процесс.
- Если Вы не восстанавливали таблицу разделов, то используйте этот гайд с текущей таблицей разделов.

### Требования

- Существующие разделы для Windows и загрузки (*если их нет, [используйте данную инструкцию](/guide/Russian/partition-ru.md)*)
  
- [Образ рекавери](../../../../releases/tag/1.0)
  
- [ADB и Fastboot](https://developer.android.com/studio/releases/platform-tools)



### Запустите рекавери для форматирования разделов

```cmd
fastboot boot <recovery.img>
```

### Форматирование разделов
> Если скрипт попросит запустить его ещё раз, то так и сделайте

```cmd
adb shell format
```


### [Следующий шаг: Установка Windows](/guide/Russian/install-ru.md#Выполните-скрипт-msc)
