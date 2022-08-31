Скрипт анализирует приложенные лог файлы.

1. Возможно указать директорию, где искать логи или конкретный файл (ключ -p)
2. Обработка всех логов внутри одной директории
3. Cтатистика сохраняется в json-файл и выводится в терминале
4. Для access.log собирается следующая информация:
- общее количество выполненных запросов - total_requests
- количество запросов HTTP(GET, POST, PUT, DELETE ,HEAD, OPTIONS) - total_stat 
- топ 3 IP с которых были выполнены запросы - top3_ip_requests
- топ 3 самых медленных запроса (IP, METHOD, URL, DATE ,DURATION) - top3_slowly_requests
Пример:
(venv) MacBook-Air-Dmitrij:hw9 opk$ python3 HW9.py -p "access.log"

 LOG FILE(S): access.log 
 {
    "total_requests": 3216723,
    "total_stat": {
        "GET": 2247848,
        "POST": 918794,
        "PUT": 70,
        "DELETE": 1,
        "HEAD": 49971,
        "OPTIONS": 39
    },
    "top3_ip_requests": {
        "193.106.31.130": {
            "REQUESTS_COUNT": 235209
        },
        "198.50.156.189": {
            "REQUESTS_COUNT": 167812
        },
        "5.112.235.245": {
            "REQUESTS_COUNT": 166722
        }
    },
    "top3_slowly_requests": [
        {
            "IP": "62.93.172.245",
            "METHOD": "POST",
            "URL": "-",
            "DATE": "23/Dec/2015:07:27:57",
            "DURATION": 10000
        },
        {
            "IP": "213.162.68.113",
            "METHOD": "GET",
            "URL": "http://www.almhuette-raith.at/index.php?option=com_phocagallery&view=category&id=1&Itemid=53",
            "DATE": "06/Jan/2016:18:47:57",
            "DURATION": 10000
        },
        {
            "IP": "194.166.55.43",
            "METHOD": "GET",
            "URL": "http://www.almhuette-raith.at/index.php?option=com_phocagallery&view=category&id=1&Itemid=53",
            "DATE": "06/Jan/2016:21:29:02",
            "DURATION": 10000
        }
    ]
}
