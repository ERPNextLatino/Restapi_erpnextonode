# restapi-erpnext 
Este modulo esta diseñado para consumir a la API REST de APIRESTERPNext V10+ usala para consumir los servicios de su APIRESTERPNext, esta libreria esta realizada apartir de la base y aporte de  pawanpandey4zip y pawangspandey,
basandonos en la documentacion de frape y dandole opcion a los desarrolladores MEAN se hace publica esta libreria con el fin de reusarla y mejorarla 

# Dice frappe en su Documentación
Frappe.io se envía con una API HTTP que se puede clasificar en Llamadas a procedimiento remoto (RPC), para llamar a los métodos de la lista blanca y la transferencia de estado representacional (REST), para manipular recursos.

La URL base es https: // {su instancia de frappe}. Todas las solicitudes que se muestran aquí deben agregarse al final de su URL base. Por ejemplo, si su instancia es demo.erpnext.com, GET / api / resource / User significa GET https://demo.erpnext.com/api/resource/User.

Todos los documentos en Frappe están disponibles a través de una API RESTful con el prefijo / api / resource /. Puede realizar todas las operaciones de CRUD en ellos:

## Crear

Puede crear un documento enviando una solicitud POST al punto final, / api / resource / {doctype}.

## Leer

Puede obtener un documento por su nombre utilizando el punto final, / api / resource / {doctype} / {name}

## Actualizar

Puede crear un documento enviando una solicitud PUT al punto final, / api / resource / {doctype} / {nombre}. Esto actúa como una solicitud de PATCH HTTP en la que no tiene que enviar todo el documento sino solo las partes que desea cambiar.

## Borrar

Puede eliminar un documento por su nombre enviando una solicitud DELETE al punto final, / api / resource / {doctype} / {name}.


```js
var APIRESTERPNext = require('restapi-erpnext');

var APIRESTERPNext = new APIRESTERPNext({
    username : 'username',
    password : 'password',
    baseUrl  : 'http://localhost:8000'
})

```

## Installation

```bash
$ npm install restapi-erpnext
```

## Customers

Get list of customers 

```js 

APIRESTERPNext.getCustomers().then(function(customers){
    console.log(customers);
})

```
Get customer's name list.

```js

APIRESTERPNext.getCustomersName().then(function(customers){
    console.log(customers);
})

```
Get customer's info by customer name

```js

 APIRESTERPNext.getCustomerByName('ram').then(function(customer){
     console.log(customer);
 })

```
Create customer for parameters follow [this](https://frappe.github.io/APIRESTERPNext/api/resource/selling/customer).

```js

  APIRESTERPNext.createCustomer({
    "naming_series": "CUST-",
    "customer_group": "Commercial",
    "doctype": "Customer",
    "communications": [],
    "customer_type": "Company",
    "accounts": [],
    "docstatus": 0,
    "territory": "Colombia",
    "sales_team": [],
    "customer_name": "ram"
  })

```
update customer by name. for parameters follow [this](https://frappe.github.io/APIRESTERPNext/api/resource/selling/customer).

```js

  APIRESTERPNext.updateCustomerByName('ram',{
    "customer_name": "fredy teheran",
  })

```

## Customer Group

Create a new customer group.
For parameters follow [this](https://frappe.github.io/APIRESTERPNext/api/resource/setup/customer_group).

```js

  APIRESTERPNext.createCustomerGroup({
     'customer_group_name' : 'Nuevo Grupo',
    'parent_customer_group': 'Todos los grupos de clientes',
    'is_group': 'No'
  })

```

update an existing customer group by group name.
For parameters follow [this](https://frappe.github.io/APIRESTERPNext/api/resource/setup/customer_group).

```js

  APIRESTERPNext.updateCustomerGroupByName('Nuevo Grupo',{
    'customer_group_name' : 'Nuevo Grupo',
    'parent_customer_group': 'Todos los grupos de clientes',
    'is_group': 'No'
  })

```

Get list of customer groups.

```js 

APIRESTERPNext.getCustomerGroups().then(function(customerGroups){
    console.log(customerGroups);
})

```
Get customer group's name list.

```js

APIRESTERPNext.getCustomerGroupsName().then(function(customerGroups){
    console.log(customerGroups);
})

```
Get customer group's info by group name

```js

 APIRESTERPNext.getCustomerGroupByName('Nuevo Grupo').then(function(customerGroups){
     console.log(customerGroups);
 })

```

 ## Sales Order


Create a Sales Order.
For parameters follow [this](https://frappe.github.io/APIRESTERPNext/api/resource/selling/sales_order).

```js

  APIRESTERPNext.createSalesOrder({
    "status": "Borrador",
    "naming_series": "SO-",
    "currency": "COP",
    "billing_status": "No facturado",
    "order_type": "Sales",
    "transaction_date": "2017-05-10",
    "territory": "Colombia",
    "delivery_status": "No enviado",
    "customer": "Camelport Internal",
    "items": [
      {
        "qty": 5,
        "rate": 2000,
        "stock_uom": "Nos",
        "item_code": "i01",
        "parentfield": "items"
      }
    ],
    "delivery_date": "2018-12-07",
    "sales_team": []
  })

```

update an existing sales order by sales order name.
For parameters follow [this](https://frappe.github.io/APIRESTERPNext/api/resource/selling/sales_order).
```js

  APIRESTERPNext.updateSalesOrderByName('SO-00003',{
    "status": "Enviado",
    "docstatus" : 1
  })

```

Get list of sales order.

```js 

APIRESTERPNext.getSalesOrder().then(function(salesOrder){
    console.log(salesOrder);
})

```
Get sales order's name list.

```js

APIRESTERPNext.getSalesOrdersName().then(function(salesOrder){
    console.log(salesOrder);
})

```
Get sales order's info by order name

```js

 APIRESTERPNext.getSalesOrderByName('Nuevo Grupo').then(function(customer){
     console.log(customer);
 })

```

## Item

Create an Item.
For param follow https://frappe.github.io/APIRESTERPNext/api/resource/accounts/sales_invoice_item.

```js

  APIRESTERPNext.createAnItem({
    "has_variants": 0,
    "is_stock_item": "No",
    "valuation_method": "",
    "min_order_qty": 0,
    "is_asset_item": "No",
    "has_batch_no": "No",
    "has_serial_no": "No",
    "is_purchase_item": "Yes",
    "is_sales_item": "Yes",
    "is_service_item": "No",
    "inspection_required": "No",
    "item_code": "item code",
    "item_name": "item name",
    "description": "description",
    "item_group": "Services"
  })

```

Update an Item.
For param follow https://frappe.github.io/APIRESTERPNext/api/resource/selling/sales_order

```js

APIRESTERPNext.updateItemByName("item code",{
    "has_variants": 0,
    "is_stock_item": "No",
    "valuation_method": "",
    "min_order_qty": 0,
    "is_asset_item": "No",
    "has_batch_no": "No",
    "has_serial_no": "No",
    "is_purchase_item": "Yes",
    "is_sales_item": "Yes",
    "is_service_item": "No",
    "inspection_required": "No",
    "item_code": "item code",
    "item_name": "item name",
    "description": "description",
    "item_group": "Services"
})

```

## Supplier

Create a Supplier.
For param follow https://frappe.github.io/APIRESTERPNext/api/resource/buying/supplier.

```js

APIRESTERPNext.createSupplier({"supplier_type":"Services","supplier_name":"ram"});

```
Update Supplier.
For param follow https://frappe.github.io/APIRESTERPNext/api/resource/buying/supplier.

```js

  APIRESTERPNext.updateSupplierByName("ram",{
    "supplier_type":"Services",
    "supplier_name":"ram"
  })

```

## Purchase Invoice

Create a Purchase Invoice
For param follow https://frappe.github.io/APIRESTERPNext/api/resource/accounts/purchase_invoice

```js

  APIRESTERPNext.createPurchaseInvoice({
      "supplier": "ram",

      "items": [{
              "item_code": "item code",
              "qty": 4,
              "price_list_rate": 5000,
              "schedule_date": "2017-05-31"
          }]
  })

```

Update Purchase Invoice.
For param follow https://frappe.github.io/APIRESTERPNext/api/resource/accounts/purchase_invoice.

```js

  APIRESTERPNext.updatePurchaseInvoiceByName("name",{
    "supplier": "ram"
  })

```

## Sales Invoice

Create a Sales Invoice.
For param follow https://frappe.github.io/APIRESTERPNext/api/resource/accounts/sales_invoice

```js

  APIRESTERPNext.createSalesInvoice(
    {
    "due_date": "2017-05-14",
     "customer": "ram",
    "items":[{
        "item_code": "item code",
        "rate": 15000,
        "qty": 3
    }]
  }
)

```
 Update Sales Invoice.
 For param follow https://frappe.github.io/APIRESTERPNext/api/resource/accounts/sales_invoice

```js

  APIRESTERPNext.updateSalesInvoiceByName(
    "Sales Invoice",

    {
    "due_date": "2017-05-14",
     "customer": "ram",
    "items":[{
        "item_code": "item code",
        "rate": 15000,
        "qty": 3
    }]
  }
)

```
## Purchase Order

Create a Purchase Order.
For param follow https://frappe.github.io/APIRESTERPNext/api/resource/buying/purchase_order

```js

  APIRESTERPNext.createPurchaseOrder({
     "supplier": "ram",
     "items": [{

             "item_code": "item code",
             "qty": 4,
             "price_list_rate": 5000,
             "schedule_date": "2017-05-31"
         }
     ]
  })

```

 Update Purchase Order.
 For param follow https://frappe.github.io/APIRESTERPNext/api/resource/buying/purchase_order

 ```js

  APIRESTERPNext.updatePurchaseOrderByName("name",{
         "supplier": "ram",
          "items": [{

                  "item_code": "item code",
                  "qty": 4,
                  "price_list_rate": 5000,
                  "schedule_date": "2017-05-31"
              }
          ]
  })

 ```

 Get All Purchase Order.

 ```js

  APIRESTERPNext.getPurchaseOrders()
  .then(function(data){ console.log(data) })

 ```

 Get Info of a Purchase Order by name.

 ```js

  APIRESTERPNext.getPurchaseOrderByName('PO-00003')
  .then(function(data){ console.log(data) })

 ```

Get List of purchase orders 

```js

APIRESTERPNext.getPurchaseOrdersName()
.then(function(data){ console.log(data) })

```

