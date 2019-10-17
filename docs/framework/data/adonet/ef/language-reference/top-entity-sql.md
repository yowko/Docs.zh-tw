---
title: TOP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 16be25336bac386c993eae7527c9377be1073d1e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319280"
---
# <a name="top-entity-sql"></a>TOP (Entity SQL)

SELECT 子句在選擇性 ALL/DISTINCT 修飾詞之後可以有選擇性 TOP 子項子句。 TOP 子項子句指定只會從查詢結果傳回第一組資料列。

## <a name="syntax"></a>語法

```sql
[ TOP (n) ]
```

## <a name="arguments"></a>引數

`n` 指定要傳回之資料列數目的數值運算式。 `n` 可以是單一數字常值或單一參數。

## <a name="remarks"></a>備註

TOP 運算式必須是單一數值常值或單一參數。 如果使用常數常值，此常值型別必須可隱含提升為 Edm.Int64 (byte、int16、int32 或 int64 或是對應到可提升為 Edm.Int64 之型別的任何提供者型別)，而且它的值必須大於或等於零。 否則將會引發例外狀況。 如果參數是當做運算式使用，此參數型別也必須可隱含提升為 Edm.Int64，但是在編譯期間並不會驗證實際的參數值，因為參數值是晚期繫結的。

以下是常數 TOP 運算式的範例：

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

以下是參數化 TOP 運算式的範例：

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

除非查詢已排序，否則 TOP 將不具決定性。 如果您要查詢具有決定性的結果，請在 [ORDER BY](skip-entity-sql.md) 子句中使用 [SKIP](limit-entity-sql.md) 和 [LIMIT](order-by-entity-sql.md) 次子句。 TOP 和 SKIP/LIMIT 會互斥。

## <a name="example"></a>範例

下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 TOP，指定從查詢結果傳回的頂端第一行資料列。 此查詢是根據 AdventureWorks Sales Model。 若要編譯及執行此查詢，請遵循以下步驟：

1. 遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。

2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：

    [!code-sql[DP EntityServices Concepts#TOP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#top)]

## <a name="see-also"></a>請參閱

- [SELECT](select-entity-sql.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [ORDER BY](order-by-entity-sql.md)
- [Entity SQL 參考](entity-sql-reference.md)
