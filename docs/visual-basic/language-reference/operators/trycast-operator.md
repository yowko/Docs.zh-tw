---
title: TryCast 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: dd50a23f09fa5dd49b86eefe163cea20430e2360
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981279"
---
# <a name="trycast-operator-visual-basic"></a>TryCast 運算子 (Visual Basic)
採用的型別轉換作業不會擲回例外狀況。  
  
## <a name="remarks"></a>備註  
 如果嘗試的轉換失敗，`CType`並`DirectCast`同時擲回<xref:System.InvalidCastException>時發生錯誤。 這可能會影響您的應用程式的效能。 `TryCast` 會傳回[Nothing](../../../visual-basic/language-reference/nothing.md)，如此一來，而不必處理可能的例外狀況，您只需要測試傳回的結果，對`Nothing`。  
  
 您使用`TryCast`關鍵字您所使用的相同方式[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)並[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)關鍵字。 您提供的運算式，做為第一個引數並將它轉換成做為第二個引數的型別。 `TryCast` 僅操作於參考類型，例如類別和介面。 它需要兩個類型之間的繼承或實作關聯性。 這表示一種類型必須繼承自或實作其他。  
  
## <a name="errors-and-failures"></a>錯誤和失敗  
 `TryCast` 偵測到沒有繼承或實作關聯性存在時，會產生編譯器錯誤。 但是沒有編譯器錯誤並不保證成功的轉換。 如果所需的轉換縮小，它可能無法在執行階段。 如果發生這種情況`TryCast`會傳回[Nothing](../../../visual-basic/language-reference/nothing.md)。  
  
## <a name="conversion-keywords"></a>轉換關鍵字  
 類型轉換關鍵字的比較如下所示。  
  
|關鍵字|資料類型|引數的關聯性|執行階段失敗|  
|---|---|---|---|  
|[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)|任何資料類型|兩個資料類型之間，則必須定義擴展或縮小轉換|會擲回 <xref:System.InvalidCastException>|  
|[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)|任何資料類型|一種類型必須繼承自或實作另一個型別|會擲回 <xref:System.InvalidCastException>|  
|`TryCast`|僅參考型別|一種類型必須繼承自或實作另一個型別|傳回[Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `TryCast`。  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱
- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
