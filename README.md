Uma fake API para uma aplicação de notícias

Base URL: https://blog-fake-api.onrender.com

## ROTAS

### Notícias /news GET

Padrão de resposta:

```json
[
   {
      "id": 1,
      "category": "economia",
      "title": "Entenda o que é o arcabouço fiscal, ponto a ponto",
      "content": "Conjunto de regras para substituir o teto de gastos foi divulgado nesta quinta-feira pela equipe econômica. Objetivo é permitir gastos considerados prioritários e possibilitar o aumento dos investimentos públicos, mas sem gerar descontrole nas contas do governo.",
      "author": "Raphael Martins"
   },
   {
      "id": 2,
      "category": "seguranca",
      "title": "Médico rastreia celular furtado e descobre prédio em SP com centenas de alertas de aparelhos roubados",
      "content": "Rastreio foi feito após amigo ter o celular levado; rastreadores de outros aparelhos levados por criminosos apontavam para o mesmo local no Centro da cidade. Espaço foi alvo de busca e apreensão na terça-feira.",
      "author": "Arthur Stabile e Camila Quaresma"
   },
   {
      "id": 3,
      "category": "mundo",     
      "title": "Piso de templo desaba na Índia e deixa 13 mortos; veja vídeo.",
      "content": "Chão, que tapava um poço, cedeu, e 25 pessoas caíram, segundo autoridades. Caso aconteceu em Indore, no centro do país, que celebra esta semana um festival hindu.",
      "author": "France Presse"
   },
   {
      "id": 4,
      "category": "economia",
      "title": "Imposto de Renda 2023: como declarar planos de previdência PGBL e VGBL.",
      "content": "Contribuições feitas para o PGBL são dedutíveis da base de cálculo do IR 2023 em até 12% da renda bruta tributável anual. Já o VGBL não permite o desconto.",
      "author": "Isabela Bolzani"
   }
]
```

### Notícias /news POST (Requer autorização)

Headers

```json
{
   'Authorization': 'Bearer token'
}
```

Padrão de corpo

```json
{ 
   "category": "economia",
   "title": "Imposto de Renda 2023: como declarar planos de previdência PGBL e VGBL.",
   "content": "Contribuições feitas para o PGBL são dedutíveis da base de cálculo do IR 2023 em até 12% da renda bruta tributável anual. Já o VGBL não permite o desconto.",
   "author": "Isabela Bolzani"
}
```

### Notícias /news/:newId PATCH (Requer autorização)

Headers

```json
{
   'Authorization': 'Bearer token'
}
```

Padrão de corpo

```json
{ 
   "category": "economia",
   "title": "Imposto de Renda 2023: como declarar planos de previdência PGBL e VGBL.",
   "content": "Contribuições feitas para o PGBL são dedutíveis da base de cálculo do IR 2023 em até 12% da renda bruta tributável anual. Já o VGBL não permite o desconto.",
   "author": "Isabela Bolzani"
}
```

Por se tratar de uma rota de patch nem todos as chaves são obrigatórias.


### Notícias /news/:newId DELETE (Requer autorização)

Headers

```json
{
   'Authorization': 'Bearer token'
}
```

### Categorias /categories GET

Padrão de resposta:

```json
[
  {
    "id": 1,
    "slug": "economia",
    "label": "Economia"
  },
  {
    "id": 2,
    "slug": "seguranca",
    "label": "Segurança"
  },
  {
    "id": 3,
    "slug": "mundo",
    "label": "Mundo"
  }
]
```

### Usuário (Cadastrar) /users POST 

Padrão de corpo

```json
{
   "name": "John Doe",
   "email": "johndoe@email.com",
   "password": "123456",
   "job": "Jornalista"
}
```

Padrão de resposta

```json
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImpvaG5kb2VAZW1haWwuY29tIiwiaWF0IjoxNjgxMjI2MzU1LCJleHAiOjE2ODEyMjk5NTUsInN1YiI6IjIifQ.HoHzAjg6luV9k6v8zHyewSTHsUnAKDBIbFiIS0r_joM",
	"user": {
		"email": "johndoe@email.com",
		"name": "John Doe",
		"id": 1,
		"job": "Jornalista"
	}
}
```

### Usuário (Login) /login POST 

```json
{
   "email": "johndoe@email.com",
   "password": "123456"
}
```

Padrão de resposta

```json
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImpvaG5kb2VAZW1haWwuY29tIiwiaWF0IjoxNjgxMjI2MzU1LCJleHAiOjE2ODEyMjk5NTUsInN1YiI6IjIifQ.HoHzAjg6luV9k6v8zHyewSTHsUnAKDBIbFiIS0r_joM",
	"user": {
		"email": "johndoe@email.com",
		"name": "John Doe",
		"job": "Jornalista",
		"id": 1
	}
}
```

### Usuário (Autologin) /users/:userId GET (Precisa de autorização)

Headers

```json
{
   'Authorization': 'Bearer token'
}
```

Padrão de resposta

```json
{
	"email": "johndoe@email.com",
	"name": "John Doe",
	"job": "Jornalista",
	"id": 1
}
```
