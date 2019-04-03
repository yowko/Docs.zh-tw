---
title: 以傳值或傳址方式傳遞引數的差別 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 1b85941c14721280a5025db442c4793930244ec8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837488"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>以傳值或傳址方式傳遞引數的差別 (Visual Basic)
當您將一或多個引數傳遞至程序時，每個引數會對應至基礎的程式設計項目，在呼叫程式碼。 您可以傳遞的值，這個基礎元素，或是它的參考。 這就所謂*傳遞機制*。  
  
## <a name="passing-by-value"></a>以傳值方式傳遞  
 傳遞引數*值所*藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序定義中的對應參數的關鍵字。 當您使用這個傳遞機制時，Visual Basic 會將基礎的程式設計元素的值複製至程序中的區域變數。 程序程式碼中呼叫的程式碼沒有任何存取的基礎項目。  
  
## <a name="passing-by-reference"></a>傳址方式傳遞  
 傳遞引數*傳址*藉由指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)程序定義中的對應參數的關鍵字。 當您使用這個傳遞機制時，Visual Basic 提供的程序的直接參考的基礎的程式設計項目中呼叫的程式碼。  
  
## <a name="passing-mechanism-and-element-type"></a>傳遞機制和項目類型  
 選擇的傳遞機制不相同的基礎項目類型分類。 傳值或傳址方式傳遞指的是 Visual Basic 提供的程序程式碼。 實值類型或參考型別是指程式設計項目儲存在記憶體中的方式。  
  
 不過，傳遞機制和項目型別是相互關聯。 參考類型的值是一個指向記憶體中的其他位置的資料。 這表示您傳值方式傳遞參考型別，當程序程式碼會有一個指標指向對應的項目資料，即使它不能存取對應的項目本身。 例如，如果項目陣列變數，程序程式碼沒有存取變數本身，但它可以存取陣列成員。  
  
## <a name="ability-to-modify"></a>若要修改的能力  
 當您將不可修改的項目傳遞做為引數時，程序可以永遠不會修改它呼叫的程式碼，是否傳遞`ByVal`或`ByRef`。  
  
 針對可修改的項目下, 表摘要說明的項目類型和傳遞機制之間的互動。  
  
|項目類型|傳遞 `ByVal`|傳遞 `ByRef`|  
|------------------|--------------------|--------------------|  
|實值型別 （只包含一個值）|程序無法變更該變數，或是它的任何成員。|變數和其成員，可以變更的程序。|  
|參考型別 （包含類別或結構的執行個體的指標）|無法變更變數的程序，但可以變更它所指向的執行個體的成員。|變數和它所指向的執行個體的成員，可以變更的程序。|  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [如何：程序引數的值變更](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：強制以傳值方式傳遞的引數](./how-to-force-an-argument-to-be-passed-by-value.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
