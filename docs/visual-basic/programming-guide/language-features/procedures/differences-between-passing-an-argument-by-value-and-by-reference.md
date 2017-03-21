---
title: "傳遞引數以傳值或傳址 (Visual Basic) 之間的差異 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- procedures, passing arguments
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
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
ms.openlocfilehash: 93c515dd8524cde85555a27879baee00185f78e3
ms.lasthandoff: 03/13/2017

---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>以傳值或傳址方式傳遞引數的差別 (Visual Basic)
當您將一或多個引數傳遞至程序時，每個引數對應至呼叫程式碼基礎的程式設計項目。 您可以傳遞基礎項目的值，或者是它的參考。 這稱為*傳遞機制*。  
  
## <a name="passing-by-value"></a>以傳值方式傳遞  
 傳遞引數*值*藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序定義中的對應參數的關鍵字。 當您使用這個傳遞機制，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]基礎的程式設計項目的值複製程序中的區域變數。 程序程式碼中呼叫的程式碼沒有任何存取權的基礎項目。  
  
## <a name="passing-by-reference"></a>傳址方式傳遞  
 傳遞引數*傳*藉由指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)程序定義中的對應參數的關鍵字。 當您使用這個傳遞機制，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供程序呼叫的程式碼中直接參考的基礎的程式設計項目。  
  
## <a name="passing-mechanism-and-element-type"></a>傳遞機制和項目類型  
 選擇的傳遞機制不相同的基礎項目類型分類。 傳值或傳址方式傳遞是指什麼[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供給程序程式碼。 實值型別或參考型別是指程式設計項目儲存在記憶體中的方式。  
  
 不過，傳遞機制與項目型別是相互關聯。 參考類型的值是記憶體中的其他資料的指標。 這表示您傳值方式傳遞參考類型，當程序程式碼會有一個指標指向對應的項目資料，即使它無法存取對應的項目本身。 例如，如果項目是陣列變數，程序程式碼無法存取變數本身，但它可以存取陣列成員。  
  
## <a name="ability-to-modify"></a>若要修改的能力  
 傳遞時不可修改的項目做為引數，此程序可以永遠不會修改呼叫程式碼，是否傳遞`ByVal`或`ByRef`。  
  
 對於可修改的項目下, 表摘要說明項目型別和傳遞機制之間的互動。  
  
|項目類型|傳遞`ByVal`|傳遞`ByRef`|  
|------------------|--------------------|--------------------|  
|實值型別 （只包含一個值）|此程序無法變更或其任何成員的變數。|此程序可以變更變數和其成員。|  
|參考型別 （包含類別或結構的執行個體的指標）|無法變更變數的程序，但可以變更它所指向的執行個體的成員。|此程序可以變更變數和它所指向的執行個體的成員。|  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)   
 [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md)   
 [可修改和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [如何︰ 變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)   
 [如何︰ 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)   
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
