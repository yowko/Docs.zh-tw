---
title: "隱含轉換 &quot;&lt;typename1&gt;&quot;to&quot;&lt;typename2&gt;&quot;中的值複製 &quot;ByRef&quot; 參數&quot;&lt;parametername&gt;&quot; 回到相符的引數。 | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
dev_langs:
- VB
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 7
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e397241aab78e17ea4efde0ea682d0e237fb8f8a
ms.lasthandoff: 03/13/2017

---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a>隱含轉換 '&lt;typename1&gt;'to'&lt;typename2&gt;'中的值複製 'ByRef' 參數'&lt;parametername&gt;' 回到相符的引數。
呼叫程序時[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)比其對應的參數不同類型的引數。  
  
 如果引數傳遞`ByRef`，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]有時會將引數的值複製到本機變數中的程序，而不是傳遞參考。 在此情況下，此程序傳回時，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]必須再複製回呼叫程式碼中的引數的本機變數的值。  
  
 如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。 如果型別不同，但[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]必須進行雙向轉換。 因為您無法使用`CType`或任何其他轉換關鍵字，在程序引數或參數，這類轉換一律為隱含。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC41999  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   可能的話，做為呼叫的引數相同型別的程序參數，因此[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不需要執行任何轉換。  
  
-   如果您要呼叫的引數的程序輸入的參數型別不同，但不是需要將值傳回呼叫的引數，定義此參數[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)而不是`ByRef`。  
  
## <a name="see-also"></a>另請參閱  
 [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [程序參數和引數](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [傳遞引數以傳值或傳址](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
