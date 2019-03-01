---
title: Let 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 545eefc67d52428470c19b62085fd87927505c7e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972699"
---
# <a name="let-clause-visual-basic"></a>Let 子句 (Visual Basic)
計算值，並將它指派給在查詢中的新變數。  
  
## <a name="syntax"></a>語法  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`variable`|必要項。 別名可以用來參考提供運算式的結果。|  
|`expression`|必要項。 運算式，會進行評估，並指派給指定的變數。|  
  
## <a name="remarks"></a>備註  
 `Let`子句可讓您計算值，每個查詢結果，並使用別名來參考它們。 別名可用於其他子句，例如`Where`子句。 `Let`子句可讓您建立可以更輕鬆地讀取，因為您可以指定包含在查詢運算式子句的別名，並以別名取代每次使用運算式子句的查詢陳述式。  
  
 您可以包含任意數目的`variable`並`expression`中的指派`Let`子句。 請以逗號 （，） 分隔每個指派。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用`Let`子句來計算產品的 10%折扣。  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
