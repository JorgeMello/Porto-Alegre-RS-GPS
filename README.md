# Spotly - CodeIgniter 4

<p align="center">
  <img src="docs/screenshots/demo.gif" alt="Spotly Demo" width="100%">
</p>

> Explore bairros como um morador local, não como turista.

---

## 📋 Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Funcionalidades](#funcionalidades)
- [Conta Demo](#conta-demo)
- [Mapa Demo vs Mapa do Usuário](#mapa-demo-vs-mapa-do-usuário)
- [lugares Turísticos de Porto Alegre](#lugares-turísticos-de-porto-alegre)
- [Tecnologias](#tecnologias)
- [Instalação](#instalação)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Rotas da Aplicação](#rotas-da-aplicação)
- [Endpoints da API](#endpoints-da-api)
- [Notas de Performance](#notas-de-performance)
- [Traduções](#traduções)
- [Licença](#licença)
- [Créditos](#créditos)

---

## Sobre o Projeto

O **Spotly** é um aplicativo de mapa para viajantes慢 (slow travelers). Em vez de mostrar os pontos turísticos genéricos habituais, ele ajuda você a descobrir o bairro onde está: onde comer, onde trabalhar, onde fazer compras, onde pegar transporte público — tudo filtrado por categoria com dados em tempo real do OpenStreetMap.

Este projeto foi **forkado do [spotly](https://github.com/eugeniogiusti/spotly)** (originalmente construído com Laravel + Vue.js) e **convertido para CodeIgniter 4** com banco de dados **MySQL**.

---

## Funcionalidades

### 🗺️ Mapa Interativo
- Visualização de mapa com **Leaflet.js** + OpenStreetMap
- **Toggle de camadas por categoria** — ative/desative categorias com um clique
- Marcadores em cluster para melhor performance em áreas com muitos pontos
- Memória de posição persistente entre sessões
- Animação suave ao navegar para diferentes locais

### 🔍 Busca de Cidades
- Busca inteligente via **Nominatim API** (geocodificação do OpenStreetMap)
- Digite qualquer cidade, bairro ou endereço
- Navegação automática até o local com animações suaves

### 📍 Cards de Pontos de Interesse (POI)
Ao clicar em um marcador, um card elegante exibe:
- Nome e categoria do local
- Telefone (se disponível)
- Website (se disponível)
- Endereço (se disponível)
- Horário de funcionamento (se disponível)
- Tags da comunidade
- Botão para abrir direções no Google Maps

### ❤️ Salvar Lugares
- Salve seus lugares favoritos com um clique
- Adicione **notas pessoais** a cada lugar salvo
- Acesse todos os seus lugares salvos a qualquer momento
- Obtenha direções para qualquer lugar salvo

### 🏷️ Tags da Comunidade
Sistema colaborativo onde usuários podem adicionar tags aos pontos:
- 💻 **Laptop Friendly** — bom para trabalhar com notebook
- 📶 **WiFi** — possui internet sem fio
- 🔌 **Power Outlets** — tomadas disponíveis
- 🤫 **Quiet** — ambiente tranquilo
- 💸 **Budget Friendly** — acessível financeiramente
- ⚠️ **Tourist Trap** — armadilha para turistas

### 📊 Dashboard Pessoal
- Total de lugares salvos
- Cidades exploradas
- Categoria favorita (mais salva)
- Lugares recentes
- Estatísticas visuais

### 📋 Meus Lugares
- Lista paginada de lugares salvos
- Filtros por categoria e cidade
- Busca por nome
- Visualização em cards com notas

### 🌍 Multilíngue
Interface disponível em **6 idiomas**:
- 🇺🇸 Inglês (en) - Padrão
- 🇧🇷 Português (pt-BR)
- 🇪🇸 Espanhol (es)
- 🇮🇹 Italiano (it)
- 🇫🇷 Francês (fr)
- 🇩🇪 Alemão (de)

---

## Conta Demo

Para testar o Spotly sem precisar se cadastrar, utilize a conta demo:

| Campo | Valor |
|-------|-------|
| **Email** | `demo@spotly.app` |
| **Senha** | `demo123` |

> ⚠️ **Importante:** A senha é `demo123` (minúsculas).

### Como acessar a conta demo:
1. Acesse a página de login: `/login`
2. Digite o email: `demo@spotly.app`
3. Digite a senha: `demo123`
4. Clique em "Entrar"

---

## Mapa Demo vs Mapa do Usuário

O Spotly possui **dois modos de visualização** do mapa:

### 🗺️ Mapa Demo (Não Logado)

Quando você acessa o mapa **sem estar logado**, o Spotly exibe:

- **Banner distintivo** no topo da página indicando "Modo Demo"
- **12 lugares turísticos de Porto Alegre, RS** já pré-carregados no mapa
- Mapa centralizado em Porto Alegre com todos os marcadores visíveis
- Botão "Cadastre-se Grátis" convidando o usuário a criar uma conta
- **Categorias desativadas** — não é possível buscar por outras categorias
- Ao clicar em um lugar, aparece a opção de se cadastrar para salvar

> 💡 **Ideal para:** Quem quer conhecer o app sem compromisso ou para demonstrações rápidas.

### 👤 Mapa do Usuário Logado

Quando você acessa o mapa **logado com sua conta**, o Spotly oferece:

- **Seus próprios lugares salvos** exibidos no mapa
- **Categorias ativas** — você pode buscar pontos de qualquer categoria usando a API do OpenStreetMap
- **Busca por cidade** — pesquise qualquer lugar no mundo
- **Salvamento de lugares** — clique em qualquer POI para salvar
- **Tags da comunidade** — adicione tags colaborativas aos lugares
- **Direções** — abra Google Maps para navegar até o local
- **Meus Lugares** — visualize todos os seus lugares salvos
- **Dashboard** — estatísticas personalizadas da sua conta

> 💡 **Ideal para:** Usuários registrados que querem descobrir e salvar seus próprios lugares.

---

## Lugares Turísticos de Porto Alegre

O Spotly vem **pré-carregado com 12 lugares turísticos** do centro histórico de Porto Alegre, Rio Grande do Sul, Brasil. Estes lugares servem como demonstração inicial e podem ser visualizados no **Modo Demo**.

### Lista dos Lugares Cadastrados

| # | Nome | Categoria | Descrição |
|---|------|-----------|-----------|
| 1 | Mercado Público de Porto Alegre | Alimentação | Mercado histórico com culinária gaúcha e artesanato |
| 2 | Bar do Museu | Alimentação | Restaurante tradicional no centro histórico |
| 3 | Parque Farroupilha (Redenção) | Parques | Parque histórico com áreas de lazer e alimentação |
| 4 | Café de la Paixão | Alimentação | Café aconchegante na Rua da Praia |
| 5 | Churrascaria Galpão Crioulo | Alimentação | Melhor churrascaria tradicional da cidade |
| 6 | Café do Mercado | Alimentação | Café dentro do Mercado Público |
| 7 | Boulangerie de Porto Alegre | Alimentação | Padaria francesa com ótima massa folhada |
| 8 | Restaurante Dona Lurdes | Alimentação | Comida caseira mineira e gaucha |
| 9 | Bar do Bife | Alimentação | Bar tradicional com bifão e chopp gelado |
| 10 | Spoleto Mercado Público | Alimentação | Massas frescas e saladas no mercado |
| 11 | Café do Artesanato | Alimentação | Café na região do shopping |
| 12 | Jardim Botânico de Porto Alegre | Parques | Belíssimo jardim com trilhas e estufa de orquídeas |

### Coordenadas

- **Centro do mapa:** Porto Alegre, RS
- **Latitude:** -30.0285
- **Longitude:** -51.2287
- **Zoom inicial:** 14

---

## Tecnologias

| Camada | Tecnologia |
|--------|------------|
| Backend | PHP 8.2+ + CodeIgniter 4.7.2 |
| Frontend | PHP Views + JavaScript (Vanilla) |
| Estilização | Tailwind CSS |
| Mapa | Leaflet.js + OpenStreetMap |
| Dados de POIs | Overpass API (OpenStreetMap) |
| Geocodificação | Nominatim API |
| Autenticação | CodeIgniter Authentication (sessões) |
| Banco de Dados | MySQL |
| Cache | MySQL (24h TTL) |

---

## Instalação

### 1. Pré-requisitos

- PHP 8.2 ou superior
- MySQL 5.7+ ou MariaDB 10.3+
- Composer
- Servidor web (Apache/Nginx) ou servidor embutido do PHP

### 2. Clonar o repositório

```bash
git clone https://github.com/seu-usuario/spotly-ci4.git
cd spotly-ci4
```

### 3. Instalar dependências

```bash
composer install
```

### 4. Configurar o ambiente

```bash
cp .env.example .env
```

Edite o arquivo `.env` com suas configurações:

```env
CI_ENVIRONMENT = development

database.default.hostname = localhost
database.default.database = leaflet
database.default.username = root
database.default.password = 
database.default.DBDriver = MySQLi
database.default.port = 3306
```

### 5. Criar o banco de dados

```sql
CREATE DATABASE leaflet CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### 6. Executar as migrações

```bash
php spark migrate
```

### 7. Popular dados demo (opcional mas recomendado)

```bash
php spark db:seed UserSeeder
php spark db:seed PortoAlegreSeeder
```

Isso criará:
- Usuário demo: `demo@spotly.app` / `demo123`
- 12 lugares turísticos de Porto Alegre

### 8. Iniciar o servidor

```bash
php spark serve
```

Acesse `http://localhost:8080` no seu navegador.

---

## Estrutura do Projeto

```
spotly/
├── app/
│   ├── Config/
│   │   ├── Layers.php          # Configuração de camadas/categorias de POI
│   │   ├── Routes.php         # Rotas da aplicação
│   │   ├── Services.php       # Registro de serviços customizados
│   │   └── Filters.php        # Filtros de autenticação
│   ├── Controllers/
│   │   ├── Api/
│   │   │   ├── GeocodingController.php    # Busca de endereços
│   │   │   ├── PoisController.php         # API de pontos de interesse
│   │   │   ├── PoiTagsController.php      # Tags da comunidade
│   │   │   └── SavedPoisController.php   # Lugares salvos
│   │   ├── AuthController.php            # Login, registro, logout
│   │   ├── DashboardController.php        # Painel do usuário
│   │   ├── Home.php                       # Landing page
│   │   ├── MapController.php              # Mapa interativo
│   │   └── MyPlacesController.php        # Meus lugares
│   ├── Database/
│   │   ├── Migrations/                   # Migrações do banco
│   │   └── Seeds/                        # Dados iniciais (demo)
│   │       ├── UserSeeder.php             # Usuário demo
│   │       └── PortoAlegreSeeder.php      # Lugares de Porto Alegre
│   ├── Filters/
│   │   ├── AuthFilter.php                # Filtro de autenticação
│   │   └── GuestFilter.php               # Filtro para guests
│   ├── Language/
│   │   ├── en/                           # Inglês
│   │   │   ├── app.php                   # Traduções da aplicação
│   │   │   └── layers.php                # Traduções das camadas
│   │   ├── pt/                          # Português
│   │   ├── pt-BR/                       # Português do Brasil
│   │   │   └── home/                    # Landing page em PT-BR
│   │   ├── es/                          # Espanhol
│   │   ├── it/                          # Italiano
│   │   ├── fr/                          # Francês
│   │   └── de/                          # Alemão
│   ├── Models/
│   │   ├── User.php                     # Modelo de usuário
│   │   ├── Poi.php                      # Modelo de POI (cache)
│   │   ├── PoiModel.php                 # Cache de POIs
│   │   ├── SavedPoi.php                 # Lugares salvos
│   │   ├── PoiTag.php                   # Tags da comunidade
│   │   ├── PoiTagModel.php              # Modelo de tags
│   │   ├── PoiQuery.php                 # Queries de API
│   │   └── PoiQueryModel.php            # Cache de queries
│   ├── Services/
│   │   ├── NominatimService.php         # Serviço de geocodificação
│   │   ├── OverpassService.php         # Serviço da API Overpass
│   │   ├── PoiCacheService.php          # Serviço de cache de POIs
│   │   ├── PoiTagService.php           # Serviço de tags
│   │   └── SavedPoiService.php          # Serviço de lugares salvos
│   └── Views/
│       ├── auth/                        # Páginas de autenticação
│       │   ├── login.php
│       │   └── register.php
│       ├── dashboard/                    # Painel do usuário
│       │   └── index.php
│       ├── home/                         # Landing pages
│       │   ├── index.php                # Landing em inglês
│       │   └── pt-BR/                   # Landing em PT-BR
│       │       └── index.php
│       ├── layouts/                      # Layouts principais
│       │   ├── app.php
│       │   └── auth.php
│       ├── map/                         # Visualização do mapa
│       │   └── index.php
│       └── my_places/                   # Meus lugares
│           └── index.php
├── public/
│   └── assets/
│       ├── css/
│       │   ├── app.css
│       │   └── auth.css
│       └── project_origin/              # Código original do Laravel
├── docs/
│   └── screenshots/                     # Screenshots do projeto
├── writable/                            # Arquivos temporários do CodeIgniter
├── .env                                 # Configurações de ambiente
├── .env.example                         # Template de configurações
├── composer.json                        # Dependências PHP
└── README.md                            # Este arquivo (em inglês)
```

---

## Rotas da Aplicação

### Autenticação

| Método | Endpoint | Descrição |
|--------|----------|-------------|
| GET | `/login` | Página de login |
| POST | `/login` | Realizar login |
| GET | `/register` | Página de registro |
| POST | `/register` | Realizar registro |
| GET | `/logout` | Sair (logout) |

### Páginas

| Método | Endpoint | Descrição |
|--------|----------|-------------|
| GET | `/` | Landing page |
| GET | `/map` | Mapa interativo |
| GET | `/my-places` | Lista de lugares salvos |
| GET | `/dashboard` | Painel do usuário |

### API

| Método | Endpoint | Descrição |
|--------|----------|-------------|
| GET | `/api/pois` | Buscar POIs por bbox e camada |
| GET | `/api/geocode` | Geocodificar endereço |
| POST | `/saved-pois` | Salvar um POI |
| PATCH | `/saved-pois/{id}/notes` | Atualizar notas |
| DELETE | `/saved-pois/{id}` | Remover POI salvo |
| GET | `/api/pois/{id}/tags` | Obter tags do POI |
| POST | `/api/pois/{id}/tags` | Alternar tag do POI |

---

## Endpoints da API

### GET /api/pois

Busca pontos de interesse por área geográfica e categoria.

**Parâmetros:**
- `bbox` (string, obrigatório): Bounding box no formato `south,west,north,east`
- `layer` (string, obrigatório): Categoria do POI

**Categorias disponíveis:**
- `food` - Alimentação
- `coffee` - Cafés
- `supermarket` - Supermercados
- `parks` - Parques
- `transit` - Transporte público
- `coworking` - Coworking
- `pharmacy` - Farmácias
- `laundry` - Lavanderias
- `atm` - Caixas eletrônicos
- `gym` - Academias
- `wellness` - Bem-estar

### GET /api/geocode

Busca coordenadas geográficas para um endereço.

**Parâmetros:**
- `q` (string, obrigatório): Endereço ou nome da cidade

### POST /saved-pois

Salva um ponto de interesse para o usuário logado.

**Corpo da requisição:**
```json
{
  "poi_external_id": "osm:node:123456",
  "layer": "food",
  "name": "Nome do Estabelecimento",
  "lat": -30.0277,
  "lng": -51.2287
}
```

### POST /api/pois/{id}/tags

Alterna uma tag em um ponto de interesse.

**Corpo da requisição:**
```json
{
  "tag": "laptop_friendly"
}
```

---

## Notas de Performance

### Primeira carga de camada

Na **primeira vez** que você ativa uma camada em uma nova área, o Spotly busca dados em tempo real da **Overpass API** (OpenStreetMap). Esta requisição pode levar até ~10 segundos dependendo da carga do servidor Overpass.

Requisições subsequentes para a mesma área são atendidas pelo **cache local do banco de dados** (TTL de 24 horas) e são praticamente instantâneas.

### Cache de POIs

- POIs são cacheados no banco de dados por **24 horas**
- Parâmetros de bbox são registrados para evitar requisições duplicadas à API externa
- O cache é automaticamente invalidado após o TTL

### Modo Demo

O modo demo (**não logado**) **não faz requisições à Overpass API**, mostrando apenas os 12 lugares pré-carregados de Porto Alegre. Isso garante:
- Carregamento instantâneo
- Zero consumo de API externa
- Experiência fluida para novos usuários

---

## Traduções

O projeto suporta os seguintes idiomas:

| Idioma | Código | Status |
|--------|--------|--------|
| 🇺🇸 Inglês | `en` | Padrão |
| 🇧🇷 Português | `pt` | ✅ Completo |
| 🇧🇷 Português do Brasil | `pt-BR` | ✅ Landing page |
| 🇪🇸 Espanhol | `es` | ✅ Completo |
| 🇮🇹 Italiano | `it` | ✅ Completo |
| 🇫🇷 Francês | `fr` | ✅ Completo |
| 🇩🇪 Alemão | `de` | ✅ Completo |

### Arquivos de Tradução

- `app/Language/{locale}/app.php` — Traduções gerais da aplicação
- `app/Language/{locale}/layers.php` — Traduções das categorias de POI
- `app/Views/home/{locale}/index.php` — Landing pages localizadas

---

## Licença

Este projeto é software de código aberto sob a licença **MIT**. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## Créditos

- **Projeto Original:** [eugeniogiusti/spotly](https://github.com/eugeniogiusti/spotly)
- **Dados do Mapa:** [OpenStreetMap](https://www.openstreetmap.org/)
- **Dados de POIs:** [Overpass API](https://overpass-api.de/)
- **Geocodificação:** [Nominatim](https://nominatim.openstreetmap.org/)
- **Ícones de Mapas:** [Leaflet.js](https://leafletjs.com/)

---

## Contribuindo

Contribuições são bem-vindas! Por favor, abra uma issue primeiro para discutir quaisquer mudanças que você gostaria de fazer.

---

<p align="center">
  Feito com ❤️ para viajantes慢
</p>
