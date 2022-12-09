# NoDelayNTPClient
## Форк NTPClient БЕЗ delay() и с доп. функциями
Источник форка arduino-libraries "https://github.com/arduino-libraries/NTPClient"


## Как это работает
**"getEpochTime()"** - возвращает время эпохи Unix, то есть секунды, прошедшие 
с 00:00:00 UTC 1 января 1970 года (секунды координации игнорируются, каждый день считается имеющим 86400 секунд). 
**Внимание**: Если вы установили смещение времени, это смещение времени будет добавлено к вашей отметке времени эпохи.

## Отличия от оригинального NTPClient
- Удалён delay() в коде! Вместо него используются таймеры на millis()
- Добавлены функции получения получения: Год, Месяц, Дата, День, Дата строкой, Дата и Время строкой
- Обновлены примеры: убраны все dalay()

# Использование
```cpp
bool begin();																					// Запустить
bool update();																				// Запросить и обновить время с сервера (если настал период обновления)
bool forceUpdate();																		// Принудительно запросить и обновить время с сервера

void setTimeOffset(int timeOffset);						        // Установить часовой пояс "в секундах"
void setUpdateInterval(uint32_t updateInterval);		  // Установить интервал обновления "в миллисекундах"
void setPoolServerName(const char* poolServerName);		// Установить сервер обновления (по умолчанию: ru.pool.ntp.org)
void end();												                    // Остановить

int getDay();											                    // Получить день недели в виде числа (1 - ПН; 2 - ВТ; 3 - СР; 4 - ЧТ; 5 - ПТ; 6 - СБ; 7 - ВС)
int getHours();											                  // Получить часы
int getMinutes();										                  // Получить минуты
int getSeconds();										                  // Получить секунды
int getDate();											                  // Получить  дату
int getMonth();											                  // Получить месяц
int getYear();											                  // Получить  год

uint32_t getEpochTime();															// Получить Unix время

String getFormattedTime();														// Получить строку времени 'ЧЧ:ММ:СС'
String getFormattedDate();														// Получить строку даты 'ДД.ММ.ГГГГ'
String getFullFormattedTime();												// Получить строку даты и времени 'ДД:ММ:ГГГГ ЧЧ:ММ:СС'

```

ver. 1.0
