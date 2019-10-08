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
ms.openlocfilehash: 88166a040823cfefe623f672e556c364d652a7fc
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004724"
---
# <a name="let-clause-visual-basic"></a>Let 子句 (Visual Basic)
計算值，並將它指派給查詢中的新變數。  
  
## <a name="syntax"></a>語法  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`variable`|必要項。 可以用來參考所提供運算式之結果的別名。|  
|`expression`|必要項。 將評估並指派給指定之變數的運算式。|  
  
## <a name="remarks"></a>備註  
 @No__t-0 子句可讓您計算每個查詢結果的值，並使用別名來參考它們。 別名可用於其他子句，例如 `Where` 子句。 @No__t-0 子句可讓您建立更容易閱讀的查詢語句，因為您可以為查詢中包含的運算式子句指定別名，並在每次使用 expression 子句時替換該別名。  
  
 您可以在 `Let` 子句中包含任意數目的 `variable` 和 @no__t 1 指派。 以逗號（，）分隔每個指派。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用 `Let` 子句來計算產品的 10% 折扣。  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](../../../visual-basic/language-reference/queries/index.md)
- [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
