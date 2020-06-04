---
title: Let 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 4bf832651d9753c41ee5a02defec4adc55af1ff1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359757"
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
|`variable`|必要。 可以用來參考所提供運算式之結果的別名。|  
|`expression`|必要。 將評估並指派給指定之變數的運算式。|  
  
## <a name="remarks"></a>備註  
 `Let`子句可讓您計算每個查詢結果的值，並使用別名來參考它們。 別名可用於其他子句，例如 `Where` 子句。 `Let`子句可讓您建立更容易閱讀的查詢語句，因為您可以為查詢中包含的運算式子句指定別名，並在每次使用 expression 子句時替換別名。  
  
 您可以在子句中包含任意數目的 `variable` 和 `expression` 指派 `Let` 。 以逗號（，）分隔每個指派。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用 `Let` 子句來計算產品的10% 折扣。  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [Select 子句](select-clause.md)
- [From 子句](from-clause.md)
- [Where 子句](where-clause.md)
