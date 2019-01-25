---
title: 隱含的轉換，從&#39; &lt;typename1&gt; &#39;至&#39; &lt;2&gt&gt; &#39;的值複製&#39;ByRef&#39;參數&#39; &lt;parametername&gt; &#39;回相符引數。
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 9f05a5fbcbef828b4ffa920d8cade475cedb64d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537229"
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>隱含的轉換，從&#39; &lt;typename1&gt; &#39;至&#39; &lt;2&gt&gt; &#39;的值複製&#39;ByRef&#39;參數&#39; &lt;parametername&gt; &#39;回相符引數。
與呼叫的程序[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)比其對應參數的不同類型的引數。  
  
 如果您傳遞的引數`ByRef`，Visual Basic 有時會將引數值複製至區域變數，而不是傳遞參考程序中。 在此情況下，此程序傳回時，Visual Basic 必須接著將本機變數的值複製回呼叫端程式碼中的引數。  
  
 如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。 但如果類型不同，Visual Basic 必須雙向轉換。 因為您無法使用`CType`或任何程序引數或參數，這類轉換上一個轉換關鍵字一律為隱含。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC41999  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   可能的話，因此不需要執行任何轉換 Visual Basic，請做為程序參數，使用相同類型的呼叫中引數。  
  
-   如果您需要呼叫引數類型與參數類型不同的程序，但不需要將值傳回給呼叫中引數，請將此參數定義為 [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) ，而非 `ByRef`。  
  
## <a name="see-also"></a>另請參閱
- [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [程序參數和引數](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [以傳值和傳址方式傳遞引數](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
