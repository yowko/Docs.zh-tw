---
title: Distinct 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: e8d3e38261a04c4d29faab351d24d6710413b09a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004799"
---
# <a name="distinct-clause-visual-basic"></a>Distinct 子句 (Visual Basic)
限制目前範圍變數的值，以排除後續查詢子句中的重複值。  
  
## <a name="syntax"></a>語法  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>備註  
 您可以使用 `Distinct` 子句來傳回唯一專案的清單。 @No__t 0 子句會導致查詢忽略重複的查詢結果。 @No__t-0 子句適用于 `Select` 子句所指定之所有傳回欄位的重複值。 如果未指定任何 `Select` 子句，則 `Distinct` 子句會套用至在 `From` 子句中識別之查詢的範圍變數。 如果範圍變數不是不可變的類型，則只有當類型的所有成員符合現有的查詢結果時，查詢才會忽略查詢結果。  
  
## <a name="example"></a>範例  
 下列查詢運算式會聯結客戶清單和客戶訂單清單。 包含的 `Distinct` 子句會傳回唯一客戶名稱和訂單日期的清單。  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
