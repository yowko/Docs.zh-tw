---
title: "可修改引數和不可修改引數之間的差異 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab108d064f5c6740f80328a9b6db4785334550ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>可修改引數和不可修改引數之間的差異 (Visual Basic)
當您呼叫程序時，通常會傳遞一或多個引數給它。 每個引數會對應至基礎的程式設計項目。 基礎項和引數本身可以是可修改或不可修改。  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>可修改和不可修改的項目  
 程式設計項目可以是*可修改的項目*，且可以包含其值已變更，或*不可修改的項目*，一旦建立之後具有固定的值。  
  
 下表列出可修改和不可修改的程式設計項目。  
  
|可修改的項目|不可修改的項目|  
|-------------------------|----------------------------|  
|區域變數 （程序內宣告），包括物件變數，但唯讀|唯讀變數、 欄位和屬性|  
|除了唯讀欄位 （模組、 類別和結構的成員變數，）|常數和常值|  
|除了唯讀屬性，|列舉型別成員|  
|陣列項目|運算式 （即使其項目是可修改）|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>可修改和不可修改引數  
 A*可修改引數*是具有可修改的對應項目。 呼叫程式碼可以在任何時候，儲存新的值，如果您要傳入的引數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，程序中的程式碼也可以修改呼叫程式碼中對應的項目。  
  
 A*不可修改引數*具有不可修改的對應項目或是傳遞[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 此程序無法修改呼叫程式碼中，對應的項目，即使它是可修改的項目。 如果是不可修改的項目，呼叫程式碼本身不能修改它。  
  
 呼叫的程序可能會修改為不可修改引數，其本機副本，但修改不會影響呼叫的程式碼中對應的項目。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)  
 [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)  
 [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)  
 [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
