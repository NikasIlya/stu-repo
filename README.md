# stu-repo
 repository for students for examples


## Рассматриваемый пример
Чтобы в каждом модуле не писать на каких тестовых данных производится проверка, то я напишу его здесь:
1) Длина преамбулы (ту которую надо обнаружить) - 8 бит
2) Длина СП - 8 бит
3) Длина ИЧК - 8 бит

### Исходные данные
`Преамбула : 10101010 (PREAMBLE)`
`СП : 11001100 (SYNC)`
`ИЧК: 01100110 (CODE)`

## Описание модулей:
### каталог sources
1. `delay_register` - простой сдвиговый регистр на 4 бита
2. `delay_reg_cfg` - сдвиговый регистр с конфигурируемым количеством бит
3. `preamble_det_x8` - вариант обнаружителя преамбулы на 8 бит с использованием сдвигового регистра. При обнаружении преамбулы генерирует один сигнал dvo длительностью один такт
4. `preamble_det_x8_long` - вариант обнаружителя преамбулы на основе сдвигового регистра, но только сигнал обнаружения dvo имеет длительность в 16 тактов. (длина СП + длина ИЧК)
5. `sync_seq_det_x8` - обнаружитель СП, основан на работе конечного автомата. Сейчас не готов

### каталог testbenches
1. `tb_delay_register` - файл-обвязка для проверки регистра задержки и демонстрации его работы
2. `tb_preamble_searcher_x8` - файл обвязка который проверяет модули :
- `preamble_det_x8`
- `preamble_det_x8_long`
- `delay_reg_cfg`
в данном примере демонстрируется как обеспечить отрезание части преамбулы от остальной части информационного сообщения при использовании delay_reg_cfg и preamble_det_x8_long.  