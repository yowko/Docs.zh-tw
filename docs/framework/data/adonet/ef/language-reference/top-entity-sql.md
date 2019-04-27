---
title: TOP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: e7c6cf6b67dc3af29f7ca8fb22af419235a9b833
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879758"
---
# <a name="top-entity-sql"></a>TOP (Entity SQL)

SELECT 子句在選擇性 ALL/DISTINCT 修飾詞之後可以有選擇性 TOP 子項子句。 TOP 子項子句指定只會從查詢結果傳回第一組資料列。

## <a name="syntax"></a>語法

```
[ TOP (n) ]
```

## <a name="arguments"></a>引數

`n` 指定要傳回的資料列數目的數值運算式。 `n` 可以是單一數字常值或單一參數。

## <a name="remarks"></a>備註

TOP 運算式必須是單一數值常值或單一參數。 如果使用常數常值，此常值型別必須可隱含提升為 Edm.Int64 (byte、int16、int32 或 int64 或是對應到可提升為 Edm.Int64 之型別的任何提供者型別)，而且它的值必須大於或等於零。 否則將會引發例外狀況。 如果參數是當做運算式使用，此參數型別也必須可隱含提升為 Edm.Int64，但是在編譯期間並不會驗證實際的參數值，因為參數值是晚期繫結的。

以下是常數 TOP 運算式的範例：

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

參數化 TOP 運算式的範例如下：

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

除非查詢已排序，否則 TOP 將不具決定性。 如果您要查詢具有決定性的結果，請在 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) 子句中使用 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) 和 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) 次子句。 TOP 和 SKIP/LIMIT 會互斥。

## <a name="example"></a>範例

下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 TOP，指定從查詢結果傳回的頂端第一行資料列。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：

1. 請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。

2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a>另請參閱

- [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
