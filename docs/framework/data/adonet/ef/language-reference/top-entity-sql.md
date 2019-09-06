---
title: TOP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 8b55519b7f95deb6463af4c0a6a2a53975e5b5a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248978"
---
# <a name="top-entity-sql"></a>TOP (Entity SQL)

SELECT 子句在選擇性 ALL/DISTINCT 修飾詞之後可以有選擇性 TOP 子項子句。 TOP 子項子句指定只會從查詢結果傳回第一組資料列。

## <a name="syntax"></a>語法

```
[ TOP (n) ]
```

## <a name="arguments"></a>引數

`n`數值運算式，指定要傳回的資料列數目。 `n` 可以是單一數字常值或單一參數。

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

1. [遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。

2. 將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a>另請參閱

- [SELECT](select-entity-sql.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [ORDER BY](order-by-entity-sql.md)
- [Entity SQL 參考](entity-sql-reference.md)
