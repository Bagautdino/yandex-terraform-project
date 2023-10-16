# Yandex Cloud Terraform Пример

## 🛠 Конфигурация

Перед началом работы выполните следующие шаги:

1. **Установка и настройка yc cli:** При первом запуске убедитесь, что у вас установлен и настроен yc cli.
2. **Добавление данных аккаунта:** Используйте следующие команды:

   ```bash
   yc config set cloud-id <cloud_id>
   yc config set folder-id <folder_id>
   yc config set service-account-key /path/to/authorized_key.json
   ```

3. **Настройка переменных окружения для Terraform:**

   ```bash
   export YC_TOKEN=$(yc iam create-token)
   export SA_KEY_FILE=$(yc config get service-account-key)
   export YC_CLOUD_ID=$(yc config get cloud-id)
   export YC_FOLDER_ID=$(yc config get folder-id)
   ```

## 📂 Пример Структуры

Ваша структура директорий может выглядеть следующим образом:

```
.
├── live  # Окружения (prod/pred/dev и т.д.)
│   ├── dev
│   └── prod
│       ├── data_stores  # Виртуальные машины баз данных
│       ├── k8s          # Kubernetes - программная часть
│       ├── mks          # Managed Service for Kubernetes - k8s-кластер - аппаратная часть
│       │   ├── cluster.tf
│       │   ├── data.tf
│       │   ├── main.tf
│       │   ├── outputs.tf
│       │   ├── terraform.tfvars
│       │   ├── variables.tf
│       │   └── versions.tf
│       └── vpc          # Сеть для баз данных и k8s-кластера
├── modules              # Собственные модули
├── storage.key          # Ключи доступа к удаленному хранилищу стейта
└── authorized_key.json  # Ключи сервисного аккаунта
```

## 📄 Генерация Документации

Для создания документации используйте:

```bash
terraform-docs markdown table path/to/module
```

---
