---
title: Distinct 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 49eaab2e6a8c48d61518ea51ef2f644b6eb48314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875278"
---
# <a name="distinct-clause-visual-basic"></a>Distinct 子句 (Visual Basic)

限制目前範圍變數的值，以消除後續查詢子句中的重複值。  
  
## <a name="syntax"></a>語法  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a>備註  

 您可以使用 `Distinct` 子句來傳回唯一專案的清單。 `Distinct`子句會讓查詢忽略重複的查詢結果。 `Distinct`子句會套用至子句所指定之所有傳回欄位的重複值 `Select` 。 如果未 `Select` 指定子句，則 `Distinct` 會將子句套用至子句中所識別之查詢的範圍變數 `From` 。 如果範圍變數不是不可變的型別，則只有當型別的所有成員都符合現有的查詢結果時，查詢才會忽略查詢結果。  
  
## <a name="example"></a>範例  

 下列查詢運算式會聯結客戶清單和客戶訂單清單。 `Distinct`包含的子句會傳回唯一客戶名稱和訂單日期的清單。  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [From 子句](from-clause.md)
- [Select 子句](select-clause.md)
- [Where 子句](where-clause.md)
