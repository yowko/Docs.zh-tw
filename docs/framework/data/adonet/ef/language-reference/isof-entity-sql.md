---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: dbea0c3a0087c88bf5ffda7b921764b8a0f9f21d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465443"
---
# <a name="isof-entity-sql"></a>ISOF (Entity SQL)
判斷運算式的型別是否不屬於所指定的型別或它的其中一個子型別。  
  
## <a name="syntax"></a>語法  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>引數  
 `expression`  
 任何用來判斷屬於何種型別的有效查詢運算式。  
  
 NOT  
 否定 IS OF 的 EDM.Boolean 結果。  
  
 ONLY  
 指定 IS OF 只在 `true` 為 `expression` 型別而非它的任何子型別時傳回 `type`。  
  
 `type`  
 要對它測試 `expression` 的型別。 此型別必須以命名空間限定。  
  
## <a name="return-value"></a>傳回值  
 如果 `true` 為 T 型別，且 T 為基底類型或 `expression` 的衍生型別，則為 `type`；如果 `expression` 在執行階段為 null 則為 null ；否則為 `false`。  
  
## <a name="remarks"></a>備註  
 運算式`expression IS NOT OF (type)`並`expression IS NOT OF (ONLY type)`語法上等同於`NOT (expression IS OF (type))`和`NOT (expression IS OF (ONLY type))`分別。  
  
 下表所示為 `IS OF` 運算子在某些一般及邊角模式中的行為。 所有例外狀況都是在叫用提供者之前從用戶端擲回：  
  
|模式|行為|  
|-------------|--------------|  
|null IS OF (EntityType)|擲回|  
|null IS OF (ComplexType)|擲回|  
|null IS OF (RowType)|擲回|  
|TREAT (null AS EntityType) IS OF (EntityType)|傳回 DBNull|  
|TREAT (null AS ComplexType) IS OF (ComplexType)|擲回|  
|TREAT (null AS RowType) IS OF (RowType)|擲回|  
|EntityType IS OF (EntityType)|傳回 true/false|  
|ComplexType IS OF (ComplexType)|擲回|  
|RowType IS OF (RowType)|擲回|  
  
## <a name="example"></a>範例  
 下列[!INCLUDE[esql](../../../../../../includes/esql-md.md)]查詢使用 IS OF 運算子來判斷查詢運算式的類型，然後使用 TREAT 運算子將 Course 型別的物件轉換成 onsitecourse 型別的物件的集合。 此查詢根據[School 模型](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac)。  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>另請參閱  
 [Entity SQL 參考](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
