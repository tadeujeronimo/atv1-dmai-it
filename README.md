# DeliveryApp - Atividade 1 (DMAI)

Aplicativo Android nativo desenvolvido na Atividade 1 do curso Desenvolvimento Mobile Android Intermediario (iTalents).

O projeto simula um fluxo de delivery com autenticacao, listagem de produtos, carrinho, favoritos, pedidos e gerenciamento de usuarios/produtos.

## Funcionalidades

- Login de usuario com token JWT.
- Cadastro de cliente.
- Listagem de produtos.
- Cadastro, edicao e remocao de produtos.
- Marcacao de produtos favoritos (persistencia local).
- Carrinho de compras com atualizacao de itens.
- Finalizacao de pedido e historico de pedidos.
- Cadastro e selecao de enderecos (persistencia local).
- Listagem e gerenciamento de usuarios.

## Arquitetura e padroes

- Kotlin + Android Views (ViewBinding e DataBinding).
- MVVM com `ViewModel` e `LiveData`.
- Repositories para orquestrar fontes locais e remotas.
- Injeccao de dependencia com Hilt.
- Persistencia local com Room.
- Comunicacao HTTP com Retrofit + OkHttp + Gson.

## Tecnologias

- Android SDK 35 (minSdk 29).
- Kotlin 2.0.21.
- Gradle 8.7.3 (AGP).
- Hilt 2.52.
- Room 2.6.1.
- Retrofit 2.11.0.
- OkHttp 4.12.0.

## Estrutura resumida

```text
app/src/main/java/com/tadeujeronimo/deliveryapp
|- data
|  |- local        # Room (database, dao, entities)
|  |- remote       # data sources remotos
|  |- repositories # regra de acesso a dados
|  |- service      # interfaces Retrofit
|  |- util         # SharedPreferences, interceptor, converters
|- di              # modulos Hilt
|- ui              # Activities, adapters, menu, interfaces
|- DeliveryApplication.kt
```

## Pre-requisitos

- Android Studio (recomendado: versao recente com suporte ao AGP 8.7+).
- JDK 11.
- Gradle Wrapper (ja incluido no repositorio).
- API backend rodando em rede local.

## Configuracao da API

Atualmente a base URL esta fixa em:

```kotlin
http://10.0.2.2:3000/
```

Arquivo:

```text
app/src/main/java/com/tadeujeronimo/deliveryapp/di/ApiModule.kt
```

Se necessario, ajuste para o IP da maquina que esta executando o backend.

## Como executar

1. Clone o repositorio.
2. Abra no Android Studio.
3. Aguarde o sync do Gradle.
4. Configure a URL da API (se necessario).
5. Execute em emulador ou dispositivo fisico.

### Via terminal

```bash
./gradlew assembleDebug
./gradlew installDebug
```

Para executar testes:

```bash
./gradlew test
./gradlew connectedAndroidTest
```

## Fluxo basico do app

1. Usuario autentica em `LoginActivity`.
2. App salva token em `SharedPreferences`.
3. `AuthInterceptor` injeta o token no header `Authorization`.
4. Usuario navega por produtos, favoritos, carrinho e pedidos.
5. Enderecos, favoritos e pedidos locais sao persistidos via Room.

## Permissoes Android

- `android.permission.INTERNET`
- `android.permission.ACCESS_NETWORK_STATE`

## Licenca

[GNU](LICENSE)
