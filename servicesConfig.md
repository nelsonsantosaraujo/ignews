# Serviços

## Stripe

Após criar seu estabelecimento crie o produto "subscription" com pelo menos nome e valor.

---

## FaunaDB

Após criar a DataBase será necessário criar as Collections e Indexes

### **Collections**

```js
  {
    name: "subscriptions",
    history_days: 30,
    ttl_days: null
  }

  {
    name: "users",
    history_days: 30,
    ttl_days: null
  }
```

### **Indexes**

```js
  {
    name: "subscription_by_id",
    unique: false,
    serialized: true,
    source: "subscriptions",
    terms: [
      {
        field: ["data", "id"]
      }
    ]
  }

  {
    name: "subscription_by_status",
    unique: false,
    serialized: true,
    source: "subscriptions",
    terms: [
      {
        field: ["data", "status"]
      }
    ]
  }

  {
    name: "subscription_by_user_ref",
    unique: false,
    serialized: true,
    source: "subscriptions",
    terms: [
      {
        field: ["data", "userId"]
      }
    ]
  }

  {
    name: "user_by_email",
    unique: true,
    serialized: true,
    source: "users",
    terms: [
      {
        field: ["data", "email"]
      }
    ]
  }

  {
    name: "user_by_stripe_customer_id",
    unique: false,
    serialized: true,
    source: "users",
    terms: [
      {
        field: ["data", "stripe_customer_id"]
      }
    ]
  }
```

---

## Prismic CMS

Após criar o seu repositório vá até a aba de "Custom Types", adicione um novo com as seguintes configurações

Tipo: Repeatable Type

Name: publication

Campos:

 - UID
 - Title como H1
 - RichText permitindo múltiplos parágrafos e blank for links

Na aba "Documents" será possível adicionar os posts.
