---
title: Skip While 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 9d95dc4a9f61a9ec3a50f9d594b31d673c2d3764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="skip-while-clause-visual-basic"></a>Skip While 子句 (Visual Basic)
只要指定的條件為 `true`，即略過集合中的項目，然後傳回其餘項目。  
  
## <a name="syntax"></a>語法  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`expression`|必要。 表示要測試的項目條件的運算式。 此運算式必須傳回`Boolean`值或功能的同等權限，例如`Integer`評估成`Boolean`。|  
  
## <a name="remarks"></a>備註  
 `Skip While`子句會略過的項目從查詢結果的開始，直到提供`expression`傳回`false`。 之後`expression`傳回`false`，此查詢會傳回所有其餘的項目。 `expression`會忽略其餘的結果。  
  
 `Skip While`子句不同於`Where`中的子句`Where`子句可以用來排除不符合特定條件的查詢中的所有項目。 `Skip While`子句不滿足條件的第一次只到排除項目。 `Skip While`子句是最有用，當您正在使用已排序的查詢結果。  
  
 您可以藉由略過特定數目的開頭的查詢結果的結果`Skip`子句。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用`Skip While`子句來略過的結果，直到找到第一個客戶於美國。  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
