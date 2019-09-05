---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: fbe27f6e25c9d69f092a060fa2c3fbf0abc93318
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250505"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
判斷特定字元 `String` 是否符合指定的模式。  
  
## <a name="syntax"></a>語法  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>引數  
 `match`  
 評估為的`String`運算式。[!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
 `pattern`  
 用來比對指定 `String` 的模式。  
  
 `escape`  
 逸出字元。  
  
 NOT  
 指定要否定 LIKE 的結果。  
  
## <a name="return-value"></a>傳回值  
 如果 `true` 符合此模式則為 `string`；否則為 `false`。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]使用 LIKE 運算子的運算式, 其評估方式與使用等式做為篩選準則的運算式大致相同。 不過, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]使用 LIKE 運算子的運算式可以同時包含常值和萬用字元。  
  
 下表所述為模式 `string` 的語法。  
  
|萬用字元|說明|範例|  
|------------------------|-----------------|-------------|  
|%|任何包含零個或多個字元的 `string`。|`title like '%computer%'`尋找標題中任何位置有`"computer"`單字的所有標題。|  
|_ (底線)|任何單一字元。|`firstname like '_ean'`尋找所有四個字母的名字, 其結尾`"ean`為 ", 例如 Dean 或小紅。|  
|[ ]|在指定範圍 ([a-f]) 或集合 ([abcdef]) 中的任何單一字元。|`lastname like '[C-P]arsen'`尋找結尾為 "arsen" 且開頭為 C 和 P 之間任何單一字元的姓氏, 例如 Carsen 或 Larsen。|  
|[^]|不在指定範圍 ([^a-f]) 或集合 ([^abcdef]) 中的任何單一字元。|`lastname like 'de[^l]%'`尋找所有開頭為 "de" 且不包含 "l" 作為下列字母的姓氏。|  
  
> [!NOTE]
> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 運算子和 ESCAPE 子句不可套用到 `System.DateTime` 或 `System.Guid` 值。  
  
 LIKE 支援 ASCII 模式比對和 Unicode 模式比對。 如果所有參數都是 ASCII 字元，便會執行 ASCII 模式比對。 如果有任何引數不是 Unicode 資料類型，所有引數都會轉換成 Unicode，然後執行 Unicode 模式比對。 使用 Unicode 配合 LIKE 時，尾端空白是有意義的；但是對於非 Unicode，尾端空白就無關重要了。 的模式字串語法[!INCLUDE[esql](../../../../../../includes/esql-md.md)]與 transact-sql 相同。  
  
 模式可包括一般字元和萬用字元。 在模式比對期間，一般字元必須與字元 `string` 中所指定的字元完全相符。 不過，萬用字元可以符合任意字元字串片段。 配合萬用字元使用時，LIKE 運算子會比 = 和 != 字串比較運算子更有彈性。  
  
> [!NOTE]
> 如果您要針對特定的提供者，可以使用提供者專用的運算式。 不過其他提供者可能會以不同方式處理這類建構。 SqlServer 支援 [first-last] 和 [^first-last] 模式，前者會在最前與最後範圍之間恰好符合一個字元 (只能有一個字元相符)，後者則是在最前與最後範圍之外恰好符合一個字元。  
  
### <a name="escape"></a>逸出字元  
 使用 ESCAPE 子句可以搜尋包含一或多個先前章節表格中所述特殊萬用字元的字元字串。 舉例來講，假設有幾份文件的標題包含常值 "100%"，而您想要搜尋所有這些文件。 因為百分比 (%)字元是萬用字元, 您必須使用[!INCLUDE[esql](../../../../../../includes/esql-md.md)] escape 子句來加以轉義, 才能順利執行搜尋。 以下就是這項篩選的範例。  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 在這個搜尋運算式中，緊接在驚嘆號字元 (!) 後面的百分比萬用字元 (%) 會被視為常值，而不是萬用字元。 除了[!INCLUDE[esql](../../../../../../includes/esql-md.md)]萬用字元和方括弧 (`[ ]`) 字元以外, 您可以使用任何字元做為 escape 字元。 在前一個範例中，驚嘆號 (!) 字元是逸出字元。  
  
## <a name="example"></a>範例  
 下列兩個[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢使用 LIKE 和 ESCAPE 運算子來判斷特定的字元字串是否符合指定的模式。 第一個查詢會搜尋以`Name`字元`Down_`開頭的。 這個查詢使用了 ESCAPE 選項，因為底線 (`_`) 是萬用字元。 若未指定 ESCAPE 選項, 查詢會搜尋任何`Name`以單字`Down`開頭, 後面接著底線字元以外之任何單一字元的值。 這些查詢是以 AdventureWorks Sales Model 為基礎。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. [遵循 how to:執行可傳回 PrimitiveType 結果](../how-to-execute-a-query-that-returns-primitivetype-results.md)的查詢。  
  
2. 將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](entity-sql-reference.md)
