---
title: DirectCast 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 4b8ffbe018872c3ae467fb9bf15e3b03595fd640
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659770"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast 運算子 (Visual Basic)
採用根據繼承或實作的型別轉換作業。  
  
## <a name="remarks"></a>備註  
 `DirectCast` 不會使用 Visual Basic 執行階段 helper 常式，進行轉換，因此它可以提供稍微較佳的效能比`CType`資料型別來回轉換時`Object`。  
  
 您使用`DirectCast`關鍵字與您所使用的方式類似[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)並[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)關鍵字。 您提供的運算式，做為第一個引數並將它轉換成做為第二個引數的型別。 `DirectCast` 需要兩個引數的資料類型之間的繼承或實作關聯性。 這表示一種類型必須繼承自或實作其他。  
  
## <a name="errors-and-failures"></a>錯誤和失敗  
 `DirectCast` 偵測到沒有繼承或實作關聯性存在時，會產生編譯器錯誤。 但是沒有編譯器錯誤並不保證成功的轉換。 如果所需的轉換縮小，它可能無法在執行階段。 如果發生這種情況，執行階段會擲回<xref:System.InvalidCastException>時發生錯誤。  
  
## <a name="conversion-keywords"></a>轉換關鍵字  
 類型轉換關鍵字的比較如下所示。  
  
|關鍵字|資料類型|引數的關聯性|執行階段失敗|  
|---|---|---|---|  
|[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)|任何資料類型|兩個資料類型之間，則必須定義擴展或縮小轉換|會擲回 <xref:System.InvalidCastException>|  
|`DirectCast`|任何資料類型|一種類型必須繼承自或實作另一個型別|會擲回 <xref:System.InvalidCastException>|  
|[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)|僅參考型別|一種類型必須繼承自或實作另一個型別|傳回[Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>範例  
 下列範例示範兩種用法`DirectCast`，無法在執行的階段，另一個的其中一個成功。  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 在上述範例中，執行階段類型`q`是`Double`。 `CType` 成功，因為`Double`可轉換成`Integer`。 不過，第一個`DirectCast`在執行階段失敗，因為執行階段類型的`Double`沒有與繼承關係`Integer`，即使有轉換。 第二個`DirectCast`成功，因為它將從類型轉換<xref:System.Windows.Forms.Form>鍵入<xref:System.Windows.Forms.Control>，從中<xref:System.Windows.Forms.Form>繼承。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
