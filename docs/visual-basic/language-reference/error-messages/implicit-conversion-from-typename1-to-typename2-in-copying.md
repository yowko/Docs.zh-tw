---
title: 從隱含轉換&#39; &lt;typename1&gt; &#39;至&#39; &lt;2>&gt; &#39;中的值複製&#39;ByRef&#39;參數&#39; &lt;參數名稱&gt;&#39;回對應的引數。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 86a618206bcfd932e41410e80c12bc166a3f67f3
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>從隱含轉換&#39; &lt;typename1&gt; &#39;至&#39; &lt;2>&gt; &#39;中的值複製&#39;ByRef&#39;參數&#39; &lt;參數名稱&gt;&#39;回對應的引數。
與呼叫的程序[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)類型不同於其對應參數的引數。  
  
 如果您要傳入的引數`ByRef`，Visual Basic 有時會將引數值複製至區域變數，而不是傳遞參考程序中。 在這種情況下，當程序傳回時，Visual Basic 必須接著將區域變數值複製回呼叫程式碼中的引數。  
  
 如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。 但如果類型不同，Visual Basic 必須進行雙向轉換。 因為您無法使用`CType`或任何其他轉換關鍵字，在上一個程序的引數或參數，這類轉換永遠是隱含。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC41999  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   可能的話，請使用相同類型的呼叫中引數與程序參數，因此 Visual Basic 就不需要執行任何轉換。  
  
-   如果您要呼叫的程序的引數類型的參數類型不同，但不是需要將值傳回呼叫的引數，定義此參數[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)而不是`ByRef`。  
  
## <a name="see-also"></a>另請參閱  
 [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [程序參數和引數](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [以傳值和傳址方式傳遞引數](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
