# Проверка перед запуском
## Lint
```
helm lint <path_to_chart>
```
## Template Verifying (Проверка шаблона => Область шаблона работает, как ожидается)
```
helm template <path_to_chart>
helm template <path_to_chart> --debug

helm template <name_chart> <path_to_chart>

```
## Dry Run (Сухой прогон => Пробный запуск)
```
helm install <name_chart> <path_to_chart> --dry-run
```