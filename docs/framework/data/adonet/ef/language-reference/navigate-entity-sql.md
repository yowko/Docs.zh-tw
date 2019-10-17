---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 09128a367a02e1f9b206a9cc068987166c76381b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319546"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)

在建立於實體之間的關聯性上巡覽。

## <a name="syntax"></a>語法

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>引數

`instance-expression` 實體的實例。

從概念結構定義語言（CSDL）檔案 `relationship-type` 關聯性的類型名稱。 @No__t_0 是以 \<namespace > 來限定。\<relationship 類型名稱 >。

`to` 關聯性的結尾。

`from` 關聯性的開頭。

## <a name="return-value"></a>傳回值

如果結束端的基數為 1，傳回值將會是 `Ref<T>`。 如果結束端的基數為 n，傳回值將會是 `Collection<Ref<T>>`。

## <a name="remarks"></a>備註

關聯性是實體資料模型（EDM）中的第一個類別結構。 您可在兩個以上的實體類型之間建立關聯性，讓使用者能夠巡覽其中一端 (實體) 到另一端的關聯性。 關聯性中的名稱解析沒有模稜兩可情況時，可以有條件地選擇`from` 和 `to` 。

NAVIGATE 在 O 和 C 空間中有效。

導覽建構的一般形式如下：

navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )

例如:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

其中 OrderCustomer 是 `relationship`，而 Customer 和 Order 則是關聯性的 `to-end` (客戶) 和 `from-end` (訂單)。 如果 OrderCustomer 是 n：1關聯性，則導覽運算式的結果類型為 Ref \<Customer >。

這個運算式更簡單的形式如下：

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

同樣地，在下列表單的查詢中，導覽運算式會產生 < Ref \<Order > > 的集合。

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

此執行個體運算式必須是實體/參考型別。

## <a name="example"></a>範例

以下 Entity SQL 查詢使用 NAVIGATE 運算子在建立於 Address 和 SalesOrderHeader 實體類型之間的關聯性上巡覽。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：

1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。

2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a>請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [How to：使用導覽運算子導覽關聯性](navigate-entity-sql.md)
