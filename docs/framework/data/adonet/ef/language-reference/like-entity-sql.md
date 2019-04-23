---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 9463a5cb522a3d3dab7725c4b71a5970d1bdf19d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302253"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
判斷特定字元 `String` 是否符合指定的模式。  
  
## <a name="syntax"></a>語法  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>引數  
 `match`  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]評估為運算式`String`。  
  
 `pattern`  
 用來比對指定 `String` 的模式。  
  
 `escape`  
 逸出字元。  
  
 NOT  
 指定要否定 LIKE 的結果。  
  
## <a name="return-value"></a>傳回值  
 如果 `true` 符合此模式則為 `string`；否則為 `false`。  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 使用 LIKE 運算子的運算式會評估大致與使用等號比較做為篩選準則的運算式相同的方式。 不過，[!INCLUDE[esql](../../../../../../includes/esql-md.md)]使用 LIKE 運算子的運算式可以包含常值和萬用字元。  
  
 下表所述為模式 `string` 的語法。  
  
|萬用字元|描述|範例|  
|------------------------|-----------------|-------------|  
|%|任何包含零個或多個字元的 `string`。|`title like '%computer%'` 尋找與單字的所有項目`"computer"`標題中的任何位置。|  
|_ (底線)|任何單一字元。|`firstname like '_ean'` 尋找所有四個字母第一個名稱結尾為`"ean`，「 例如 Dean 或 Sean。|  
|[ ]|在指定範圍 ([a-f]) 或集合 ([abcdef]) 中的任何單一字元。|`lastname like '[C-P]arsen'` 尋找姓氏"arsen"，以 C 和 P，例如 Carsen 或 Larsen 之間任何單一字元開頭。|  
|[^]|不在指定範圍 ([^a-f]) 或集合 ([^abcdef]) 中的任何單一字元。|`lastname like 'de[^l]%'` 尋找所有以"de"開頭，而且不包含下列字母"l"的最後一個名稱。|  
  
> [!NOTE]
>  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 運算子和 ESCAPE 子句不可套用到 `System.DateTime` 或 `System.Guid` 值。  
  
 LIKE 支援 ASCII 模式比對和 Unicode 模式比對。 如果所有參數都是 ASCII 字元，便會執行 ASCII 模式比對。 如果有任何引數不是 Unicode 資料類型，所有引數都會轉換成 Unicode，然後執行 Unicode 模式比對。 使用 Unicode 配合 LIKE 時，尾端空白是有意義的；但是對於非 Unicode，尾端空白就無關重要了。 模式字串語法[!INCLUDE[esql](../../../../../../includes/esql-md.md)]的相同[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]。  
  
 模式可包括一般字元和萬用字元。 在模式比對期間，一般字元必須與字元 `string` 中所指定的字元完全相符。 不過，萬用字元可以符合任意字元字串片段。 配合萬用字元使用時，LIKE 運算子會比 = 和 != 字串比較運算子更有彈性。  
  
> [!NOTE]
>  如果您要針對特定的提供者，可以使用提供者專用的運算式。 不過其他提供者可能會以不同方式處理這類建構。 SqlServer 支援 [first-last] 和 [^first-last] 模式，前者會在最前與最後範圍之間恰好符合一個字元 (只能有一個字元相符)，後者則是在最前與最後範圍之外恰好符合一個字元。  
  
### <a name="escape"></a>逸出字元  
 使用 ESCAPE 子句可以搜尋包含一或多個先前章節表格中所述特殊萬用字元的字元字串。 舉例來講，假設有幾份文件的標題包含常值 "100%"，而您想要搜尋所有這些文件。 由於百分比 （%）字元是萬用字元，您必須使用逸出它[!INCLUDE[esql](../../../../../../includes/esql-md.md)]逸出子句，以順利執行搜尋。 以下就是這項篩選的範例。  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 在這個搜尋運算式中，緊接在驚嘆號字元 (!) 後面的百分比萬用字元 (%) 會被視為常值，而不是萬用字元。 您可以使用任何字元做為逸出字元，除了[!INCLUDE[esql](../../../../../../includes/esql-md.md)]萬用字元和方括號 (`[ ]`) 字元。 在前一個範例中，驚嘆號 (!) 字元是逸出字元。  
  
## <a name="example"></a>範例  
 下列兩個[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢使用 LIKE 和 ESCAPE 運算子來判斷特定的字元字串是否符合指定的模式。 第一個查詢會搜尋`Name`以字元為開頭的`Down_`。 這個查詢使用了 ESCAPE 選項，因為底線 (`_`) 是萬用字元。 如果不指定 ESCAPE 選項，查詢會搜尋任何`Name`這個字為開頭的值`Down`後面接著底線字元除外的任何單一字元。 這些查詢是以 AdventureWorks Sales Model 為依據。 若要編譯及執行此查詢，請遵循以下步驟：  
  
1. 請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。  
  
2. 將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a>另請參閱

- [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
