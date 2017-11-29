---
title: "以傳值或傳址方式傳遞引數的差別 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3efd4f41184287cdcd3d499712a857bee997c1a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>以傳值或傳址方式傳遞引數的差別 (Visual Basic)
當您將一或多個引數傳遞至程序時，每個引數會對應至基礎的程式設計項目，呼叫程式碼中。 您可以將這個基礎元素的值，或者是它的參考傳遞。 這稱為*傳遞機制*。  
  
## <a name="passing-by-value"></a>以傳值方式傳遞  
 傳遞引數*值*藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序定義中的對應參數的關鍵字。 當您使用這個傳遞機制，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]基礎的程式設計項目的值複製至程序中的區域變數。 程序程式碼呼叫的程式碼中沒有任何存取的基礎項目。  
  
## <a name="passing-by-reference"></a>傳址方式傳遞  
 傳遞引數*傳*藉由指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)程序定義中的對應參數的關鍵字。 當您使用這個傳遞機制，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]呼叫的程式碼中提供的程序的直接參考的基礎的程式設計項目。  
  
## <a name="passing-mechanism-and-element-type"></a>傳遞機制以及項目類型  
 選擇的傳遞機制並不相同的基礎項目類型分類。 傳值方式或傳址方式傳遞是指什麼[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供給程序程式碼。 實值類型或參考型別是指程式設計項目儲存在記憶體中的方式。  
  
 不過，傳遞機制以及項目類型是相互關聯。 參考類型的值是記憶體中的其他資料的指標。 這表示當傳值方式傳遞參考類型，程序程式碼會有一個指標指向基礎項目的資料，即使它無法存取對應的項目本身。 例如，如果項目是陣列變數，程序程式碼並沒有變數本身的存取權，但它可以存取陣列成員。  
  
## <a name="ability-to-modify"></a>若要修改的能力  
 當您將不可修改的項目傳遞做為引數時，程序可以永遠不會修改它呼叫的程式碼，是否在傳遞`ByVal`或`ByRef`。  
  
 對於可修改的項目下, 表摘要說明的項目類型與傳遞機制之間的互動。  
  
|項目類型|傳遞`ByVal`|傳遞`ByRef`|  
|------------------|--------------------|--------------------|  
|實值型別 （只包含一個值）|程序無法變更變數或它的任何成員。|變數和其成員，可以變更程序。|  
|參考類型 （包含的類別或結構的執行個體的指標）|無法變更變數的程序，但可以變更它所指向的執行個體的成員。|此程序可以變更的變數和它所指向的執行個體的成員。|  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)  
 [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)  
 [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)  
 [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
