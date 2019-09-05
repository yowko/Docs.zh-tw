---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 2c6c2ae4c593da1d5fe8cdf3015eb0e31e4b12b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249944"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)

在建立於實體之間的關聯性上巡覽。

## <a name="syntax"></a>語法

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>引數

`instance-expression`實體的實例。

`relationship-type`概念結構定義語言 (CSDL) 檔案中關聯性的類型名稱。 會限定為\<命名空間 >。\< `relationship-type`關聯性類型名稱 >。

`to`關聯性的結尾。

`from`關聯性的開頭。

## <a name="return-value"></a>傳回值

如果結束端的基數為 1，傳回值將會是 `Ref<T>`。 如果結束端的基數為 n，傳回值將會是 `Collection<Ref<T>>`。

## <a name="remarks"></a>備註

關聯性是實體資料模型 (EDM) 中的第一個類別結構。 您可在兩個以上的實體類型之間建立關聯性，讓使用者能夠巡覽其中一端 (實體) 到另一端的關聯性。 關聯性中的名稱解析沒有模稜兩可情況時，可以有條件地選擇`from` 和 `to` 。

NAVIGATE 在 O 和 C 空間中有效。

導覽建構的一般形式如下：

navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )

例如：

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

其中 OrderCustomer 是 `relationship`，而 Customer 和 Order 則是關聯性的 `to-end` (客戶) 和 `from-end` (訂單)。 如果 OrderCustomer 是 n:1 關聯性, 則導覽運算式的結果類型會是 Ref\<Customer >。

這個運算式更簡單的形式如下：

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

同樣地, 在下列表單的查詢中, 導覽運算式會產生 < Ref\<Order > > 的集合。

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

此執行個體運算式必須是實體/參考型別。

## <a name="example"></a>範例

以下 Entity SQL 查詢使用 NAVIGATE 運算子在建立於 Address 和 SalesOrderHeader 實體類型之間的關聯性上巡覽。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：

1. [遵循 how to:執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。

2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
- [如何：使用導覽運算子導覽關聯性](navigate-entity-sql.md)
