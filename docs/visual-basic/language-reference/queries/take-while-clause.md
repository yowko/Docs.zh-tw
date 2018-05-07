---
title: Take While 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 7e0a6bd77ca2594e9d74e669fcd9cddf91ee1cad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="take-while-clause-visual-basic"></a>Take While 子句 (Visual Basic)
只要指定的條件為 `true`，即包含集合中的項目，並略過其餘項目。  
  
## <a name="syntax"></a>語法  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`expression`|必要。 表示要測試的項目條件的運算式。 此運算式必須傳回`Boolean`值或功能的同等權限，例如`Integer`評估成`Boolean`。|  
  
## <a name="remarks"></a>備註  
 `Take While`子句會包含從查詢結果的開始項目，直到提供`expression`傳回`false`。 之後`expression`傳回`false`，查詢將會略過所有其餘的項目。 `expression`會忽略其餘的結果。  
  
 `Take While`子句不同於`Where`中的子句`Where`子句可以用來包含查詢中所有符合特定條件的項目。 `Take While`子句之前不滿足條件的第一次只包含項目。 `Take While`子句是最有用，當您正在使用已排序的查詢結果。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用`Take While`子句用來擷取結果，直到找到沒有任何訂單的第一個客戶。  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
