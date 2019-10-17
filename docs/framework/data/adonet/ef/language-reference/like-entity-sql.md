---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: f9e33c78235f637e0aa0622d9d8cc30255722beb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319676"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
判斷特定字元 `String` 是否符合指定的模式。  
  
## <a name="syntax"></a>語法  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>引數  
 `match`  
 評估為 `String` 的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算式。  
  
 `pattern`  
 用來比對指定 `String` 的模式。  
  
 `escape`  
 逸出字元。  
  
 NOT  
 指定要否定 LIKE 的結果。  
  
## <a name="return-value"></a>傳回值  
 如果 `true` 符合此模式則為 `string`；否則為 `false`。  
  
## <a name="remarks"></a>備註  
 使用 LIKE 運算子 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算式的評估方式，與使用相等做為篩選準則的運算式大致相同。 不過，使用 LIKE 運算子 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 運算式可以同時包含常值和萬用字元。  
  
 下表所述為模式 `string` 的語法。  
  
|萬用字元|描述|範例|  
|------------------------|-----------------|-------------|  
|%|任何包含零個或多個字元的 `string`。|`title like '%computer%'` 會在標題中的任何位置尋找具有 `"computer"` 字的所有標題。|  
|_ (底線)|任何單一字元。|`firstname like '_ean'` 會尋找所有以 `"ean` 結尾的四個字母名字，例如 Dean 或小紅。|  
|[ ]|在指定範圍 ([a-f]) 或集合 ([abcdef]) 中的任何單一字元。|`lastname like '[C-P]arsen'` 會尋找結尾為 "arsen" 且開頭為 C 和 P 之間任何單一字元的姓氏，例如 Carsen 或 Larsen。|  
|[^]|不在指定範圍 ([^a-f]) 或集合 ([^abcdef]) 中的任何單一字元。|`lastname like 'de[^l]%'` 會尋找開頭為 "de" 且不包含 "l" 作為下列字母的所有姓氏。|  
  
> [!NOTE]
> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 運算子和 ESCAPE 子句不可套用到 `System.DateTime` 或 `System.Guid` 值。  
  
 LIKE 支援 ASCII 模式比對和 Unicode 模式比對。 如果所有參數都是 ASCII 字元，便會執行 ASCII 模式比對。 如果有任何引數不是 Unicode 資料類型，所有引數都會轉換成 Unicode，然後執行 Unicode 模式比對。 使用 Unicode 配合 LIKE 時，尾端空白是有意義的；但是對於非 Unicode，尾端空白就無關重要了。 @No__t_0 的模式字串語法與 Transact-sql 相同。  
  
 模式可包括一般字元和萬用字元。 在模式比對期間，一般字元必須與字元 `string` 中所指定的字元完全相符。 不過，萬用字元可以符合任意字元字串片段。 配合萬用字元使用時，LIKE 運算子會比 = 和 != 字串比較運算子更有彈性。  
  
> [!NOTE]
> 如果您要針對特定的提供者，可以使用提供者專用的運算式。 不過其他提供者可能會以不同方式處理這類建構。 SqlServer 支援 [first-last] 和 [^first-last] 模式，前者會在最前與最後範圍之間恰好符合一個字元 (只能有一個字元相符)，後者則是在最前與最後範圍之外恰好符合一個字元。  
  
### <a name="escape"></a>逸出字元  
 使用 ESCAPE 子句可以搜尋包含一或多個先前章節表格中所述特殊萬用字元的字元字串。 舉例來講，假設有幾份文件的標題包含常值 "100%"，而您想要搜尋所有這些文件。 因為百分比（%）字元是萬用字元，您必須使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE 子句來加以轉義，才能順利執行搜尋。 以下就是這項篩選的範例。  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 在這個搜尋運算式中，緊接在驚嘆號字元 (!) 後面的百分比萬用字元 (%) 會被視為常值，而不是萬用字元。 除了 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 萬用字元和方括弧（`[ ]`）字元以外，您可以使用任何字元做為 escape 字元。 在前一個範例中，驚嘆號 (!) 字元是逸出字元。  
  
## <a name="example"></a>範例  
 下列兩個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢會使用 LIKE 和 ESCAPE 運算子來判斷特定的字元字串是否符合指定的模式。 第一個查詢會搜尋以字元 `Down_` 開頭的 `Name`。 這個查詢使用了 ESCAPE 選項，因為底線 (`_`) 是萬用字元。 若未指定 ESCAPE 選項，查詢會搜尋以 `Down` 開頭的任何 `Name` 值，後面接著底線字元以外的任何單一字元。 這些查詢是以 AdventureWorks Sales Model 為基礎。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 依照[如何：執行傳回 PrimitiveType 結果的查詢](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的程式進行。  
  
2. 將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a>請參閱

- [Entity SQL 參考](entity-sql-reference.md)
