---
title: 從隱含轉換 &#39;&lt;typename1&gt;&#39; 加入 &#39;&lt;2>&gt;&#39; 複製的值 &#39;ByRef &#39;參數 &#39;&lt;parametername&gt;&#39; 後，對應的引數。
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
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>從隱含轉換 &#39;&lt;typename1&gt;&#39; 加入 &#39;&lt;2>&gt;&#39; 複製的值 &#39;ByRef &#39;參數 &#39;&lt;parametername&gt;&#39; 後，對應的引數。
與呼叫的程序[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)類型不同於其對應參數的引數。  
  
 如果您要傳入的引數`ByRef`，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]有時會將引數值複製至區域變數，而不是傳遞參考程序中。 在這類情況下，此程序傳回時， [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 接著必須將區域變數值複製回呼叫中程式碼中的引數。  
  
 如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。 但是，如果類型不同，則 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 必須進行雙向轉換。 因為您無法使用`CType`或任何其他轉換關鍵字，在上一個程序的引數或參數，這類轉換永遠是隱含。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC41999  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果可能，請使用類型與程序參數相同的呼叫中引數，這樣 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 就不需要執行任何轉換。  
  
-   如果您要呼叫的程序的引數類型的參數類型不同，但不是需要將值傳回呼叫的引數，定義此參數[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)而不是`ByRef`。  
  
## <a name="see-also"></a>另請參閱  
 [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [程序參數和引數](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [以傳值和傳址方式傳遞引數](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
