
.PHONY: help run lint format format-check typecheck fullcheck fulltest clean precommit

help:
	@echo "Доступные команды:"
	@echo "  make run         - Запуск программы"
	@echo "  make lint        - Проверка кода линтером (Ruff)"
	@echo "  make format      - Автоформатирование кода (Ruff)"
	@echo "  make format-check - Проверка форматирования (Ruff)"
	@echo "  make typecheck   - Проверка типов (Mypy)"
	@echo "  make fullcheck   - Все статические проверки"
	@echo "  make precommit   - Установка Git hooks"
	@echo "  make clean       - Очистка временных файлов"


run:
	python script.py text.txt alfa.txt key.txt decrypted.txt


lint:
	ruff check .
	@echo "Линтер завершен без ошибок"


format-check:
	ruff format --check .
	@echo "Форматирование проверено"

format:
	ruff format .
	@echo "Код отформатирован"


typecheck:
	python -m mypy script.py
	@echo "Проверка типов завершена"


fullcheck: lint format-check typecheck
	@echo "Все статические проверки пройдены"

precommit:
	pip install pre-commit
	pre-commit install
	pre-commit install --hook-type pre-push
	@echo "Git hooks установлены"

clean:
	-rmdir /s /q __pycache__ 2>nul
	-del /s /q *.pyc 2>nul
	-rmdir /s /q .ruff_cache 2>nul
	-rmdir /s /q .mypy_cache 2>nul
	@echo "Очистка завершена"
