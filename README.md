# turnover
turnover analytics with data science

# turnover_mlops 
making a production process to our model


## Para rodar - Faça suas adequações

- Tenha um banco postgres rodando com os /sql rodados
- use os seguintes comandos


``` cmd
python -m mlflow server --host 127.0.0.1 --port 5000 --backend-store-uri postgresql://postgres:1234@127.0.0.1:5432/mlflow --default-artifact-root ./mlruns
```
---

``` cmd
´python -m uvicorn app.main:app --reload --port 8081´
```

