# Сервис каталога

Услуги, прайс по филиалам, нормативы расхода материалов. Справочник:
отвечает на запросы, ничего не потребляет из брокера и переживает
остановку между вызовами.

## Зависимости

| Пакет | Роль |
|---|---|
| [`mirea-contracts`](https://github.com/mireacrm/contracts-py) | сообщения и стабы gRPC |
| [`mireacrm-common`](https://github.com/mireacrm/py-common) | настройки, метрики, трасса, ошибки, база, события, gRPC |

Оба приезжают из своих репозиториев по версии из `pyproject.toml`.
Версию контрактов называет сервис, а не обвяз: два прямых URL одного
пакета pip считает конфликтом.

## Локально

```
pip install -e ".[dev]"
python -m pytest tests/unit -q
python -m pytest tests/integration -q   # нужен Postgres
docker build -t catalog-service .
```

Систему целиком поднимает [`mireacrm/deploy`](https://github.com/mireacrm/deploy).
