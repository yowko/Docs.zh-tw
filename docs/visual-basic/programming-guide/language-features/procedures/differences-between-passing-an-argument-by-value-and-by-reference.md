---
title: 以傳值或傳址方式傳遞引數的差別
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 84ec3bac2532b2cef72ddda347251bc987801c3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341226"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>以傳值或傳址方式傳遞引數的差別 (Visual Basic)
當您將一或多個引數傳遞至程式時，每個引數都會對應至呼叫程式碼中的基礎程式設計項目。 您可以傳遞這個基礎元素的值，或它的參考。 這就是所謂的*傳遞機制*。  
  
## <a name="passing-by-value"></a>以傳值方式傳遞  
 您可以藉由在程序定義中指定對應參數的[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)關鍵字，以傳*值*方式傳遞引數。 當您使用這個傳遞機制時，Visual Basic 會將基礎程式設計項目的值複製到程式中的區域變數。 程式碼沒有呼叫程式碼中基礎元素的任何存取權。  
  
## <a name="passing-by-reference"></a>以傳址方式傳遞  
 您可以在程序定義中指定對應參數的[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字，以傳*址方式*傳遞引數。 當您使用這個傳遞機制時，Visual Basic 可讓程式直接參考呼叫程式碼中的基礎程式設計項目。  
  
## <a name="passing-mechanism-and-element-type"></a>傳遞機制和元素類型  
 傳遞機制的選擇與基礎元素類型的分類不同。 以傳值或傳址方式傳遞是指 Visual Basic 提供給程式碼的內容。 實值型別或參考型別是指程式設計專案在記憶體中的儲存方式。  
  
 不過，傳遞機制和元素類型是相互關聯的。 參考型別的值是記憶體中其他位置的資料指標。 這表示當您以傳值方式傳遞參考型別時，程式碼會有基礎專案資料的指標，即使它無法存取基礎元素本身也一樣。 例如，如果元素是陣列變數，程式碼就不會有變數本身的存取權，但它可以存取陣列成員。  
  
## <a name="ability-to-modify"></a>能夠修改  
 當您傳遞無法修改的元素做為引數時，不論是傳遞 `ByVal` 或 `ByRef`，程式都不能在呼叫程式碼中加以修改。  
  
 對於可修改的元素，下表摘要說明專案類型與傳遞機制之間的互動。  
  
|項目類型|已通過 `ByVal`|已通過 `ByRef`|  
|------------------|--------------------|--------------------|  
|實值型別（只包含值）|程式無法變更變數或其任何成員。|程式可以變更變數及其成員。|  
|參考型別（包含類別或結構實例的指標）|程式無法變更變數，但是可以變更它所指向之實例的成員。|此程式可以變更其指向之實例的變數和成員。|  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
