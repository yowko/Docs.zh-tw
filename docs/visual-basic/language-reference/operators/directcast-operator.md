---
title: DirectCast 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9b81abea364e328b831ee98c3b847161c3f7dd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="directcast-operator-visual-basic"></a>DirectCast 運算子 (Visual Basic)
導入了根據繼承或實作的型別轉換作業。  
  
## <a name="remarks"></a>備註  
 `DirectCast`不會使用 Visual Basic 執行階段 helper 常式轉換，讓它可以提供稍微較佳的效能比`CType`資料型別進行來回轉換時`Object`。  
  
 您使用`DirectCast`關鍵字的使用方式類似於[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)和[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)關鍵字。 您提供的運算式做為第一個引數並將它轉換為做為第二個引數的型別。 `DirectCast`需要兩個引數的資料類型之間的繼承或實作關聯性。 這表示一個型別必須繼承自或實作的其他。  
  
## <a name="errors-and-failures"></a>錯誤和失敗  
 `DirectCast`如果它偵測到沒有繼承或實作關聯性存在，會產生編譯器錯誤。 但沒有編譯器錯誤並不保證成功的轉換。 如果所要的轉換縮小，它可能無法在執行階段。 如果發生這種情況，執行階段會擲回<xref:System.InvalidCastException>錯誤。  
  
## <a name="conversion-keywords"></a>轉換關鍵字  
 的類型轉換關鍵字比較，如下所示。  
  
|關鍵字|資料類型|引數關聯性|執行階段失敗|  
|---|---|---|---|  
|[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)|任何資料類型|兩個資料類型之間，則必須定義擴展或縮小轉換|擲回<xref:System.InvalidCastException>|  
|`DirectCast`|任何資料類型|一種類型必須繼承自或實作其他的型別|擲回<xref:System.InvalidCastException>|  
|[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)|只參考型別|一種類型必須繼承自或實作其他的型別|傳回[做任何動作](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>範例  
 下列範例會示範兩種用途`DirectCast`，無法在執行的階段，另一個的其中一個成功。  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 在上述範例中，執行階段輸入的`q`是`Double`。 `CType`會成功，因為`Double`可以轉換成`Integer`。 不過，第一個`DirectCast`會在執行階段失敗，因為執行階段類型的`Double`沒有與繼承關係`Integer`，即使有轉換。 第二個`DirectCast`會成功，因為它會從類型轉換<xref:System.Windows.Forms.Form>輸入<xref:System.Windows.Forms.Control>，從中<xref:System.Windows.Forms.Form>繼承。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>  
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
