# Translate Ragnarok (bRO pre-Renewal)

Web app + API para converter `itemInfo.lua` (EN) para padrão PT-BR **pre-Renewal**.

## Regras (MVP)
- Mantém **valores numéricos** do arquivo original (ex.: Defense 2 continua 2).
- Traduz apenas **rótulos** e termos de categoria:
  - `Class:` -> `Tipo:`
  - `Defense:` -> `Defesa:`
  - `Weight:` -> `Peso:`
  - `Jobs:` -> `Classes:`
  - `Footgear` -> `Calçado` (e outros mapeamentos simples)
- Mantém códigos de cor do Ragnarok (ex.: `^0000FF`).

## Rodar com Docker
```bash
docker compose up --build
```

- Web: http://localhost:5173
- API: http://localhost:8000

## Rodar local (sem Docker)

### API
```bash
cd api
python -m venv .venv
# Windows: .venv\Scripts\activate
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### Web
```bash
cd web
npm install
npm run dev
```

## Teste rápido
Você pode usar `sample/itemInfo_2404_en.lua` para validar.

## Próximos passos (opcional)
- Integrar consulta online (RagnaPlace / Latam / PBGO) com cache e rate-limit.
- Aumentar base de termos e exceções (All except Novice -> Todas, exceto Aprendizes, etc.).