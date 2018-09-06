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
ms.openlocfilehash: a3c0749560d8cea1e46d96298347ce54f0bf9185
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863370"
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
|`expression`|必要。 表示要測試的元素的條件運算式。 此運算式必須傳回`Boolean`值或功能對等項目，例如`Integer`評估為`Boolean`。|  
  
## <a name="remarks"></a>備註  
 `Skip While`子句會略過從查詢結果的開始，直到所提供的項目`expression`傳回`false`。 在後`expression`傳回`false`，查詢會傳回所有剩餘的項目。 `expression`會忽略其餘的結果。  
  
 `Skip While`子句不同`Where`中的子句`Where`子句可以用來排除不符合特定條件的查詢中的所有項目。 `Skip While`子句會排除項目只會保存未滿足條件的第一次。 `Skip While`子句在當您正在使用的已排序的查詢結果時十分實用。  
  
 您可以使用連線，略過特定數目的查詢結果的結果從一開始`Skip`子句。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用`Skip While`子句來略過的結果，直到找到第一個客戶，從美國傳為止。  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/index.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
