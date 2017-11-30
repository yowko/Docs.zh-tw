---
title: "TryCast 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords: TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6be11b49eb3b9d98e3bf147e9b1026d4ffc860c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="trycast-operator-visual-basic"></a>TryCast 運算子 (Visual Basic)
導入了沒有擲回例外狀況的類型轉換作業。  
  
## <a name="remarks"></a>備註  
 如果嘗試的轉換失敗，`CType`和`DirectCast`同時擲回<xref:System.InvalidCastException>錯誤。 這可能會影響應用程式的效能。 `TryCast`傳回[Nothing](../../../visual-basic/language-reference/nothing.md)，如此一來，而不必處理可能的例外狀況，您只需要測試傳回的結果，針對`Nothing`。  
  
 您使用`TryCast`關鍵字您使用的相同方式[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)和[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)關鍵字。 您提供的運算式做為第一個引數並將它轉換為做為第二個引數的型別。 `TryCast`只在參考類型，例如類別和介面上的作業。 它需要兩個類型之間的繼承或實作關聯性。 這表示一個型別必須繼承自或實作的其他。  
  
## <a name="errors-and-failures"></a>錯誤和失敗  
 `TryCast`如果它偵測到沒有繼承或實作關聯性存在，會產生編譯器錯誤。 但沒有編譯器錯誤並不保證成功的轉換。 如果所要的轉換縮小，它可能無法在執行階段。 如果發生這種情況，`TryCast`傳回[Nothing](../../../visual-basic/language-reference/nothing.md)。  
  
## <a name="conversion-keywords"></a>轉換關鍵字  
 的類型轉換關鍵字比較，如下所示。  
  
|關鍵字|資料類型|引數關聯性|執行階段失敗|  
|---|---|---|---|  
|[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)|任何資料類型|兩個資料類型之間，則必須定義擴展或縮小轉換|擲回<xref:System.InvalidCastException>|  
|[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)|任何資料類型|一種類型必須繼承自或實作其他的型別|擲回<xref:System.InvalidCastException>|  
|`TryCast`|只參考型別|一種類型必須繼承自或實作其他的型別|傳回[做任何動作](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `TryCast`。  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
