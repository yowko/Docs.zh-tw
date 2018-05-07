---
title: 以傳值和傳址方式傳遞引數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: 2d333bc873ba055d7a7b53c50fcfeec4cc0f9491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>以傳值和傳址方式傳遞引數 (Visual Basic)
在 Visual Basic 中，您可以將引數傳遞至程序*值*或*傳*。 這稱為*傳遞機制*，且它會判斷該程序是否可以修改呼叫程式碼中的引數的基礎的程式設計項目。 程序宣告指定決定每個參數的傳遞機制[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字。  
  
## <a name="distinctions"></a>區別  
 當傳遞至程序的引數，應注意彼此互動的數個不同區別：  
  
-   基礎的程式設計項目是否為可修改  
  
-   引數本身是否為可修改  
  
-   值或傳參考方式傳遞引數是否  
  
-   引數資料類型是否為實值類型或參考類型  
  
 如需詳細資訊，請參閱[修改之間的差異和不可修改引數](./differences-between-modifiable-and-nonmodifiable-arguments.md)和[差異之間傳遞引數的值和依參考](./differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## <a name="choice-of-passing-mechanism"></a>選擇的傳遞機制  
 您應該選擇仔細每個引數的傳遞機制。  
  
-   **保護**。 在兩種傳遞機制之間做選擇，最重要的準則是呼叫變數來變更的風險。 傳遞引數的好處`ByRef`程序可以透過該引數呼叫的程式碼會傳回值。 傳遞引數的好處`ByVal`是它可以避免變數變更程序。  
  
-   **效能**。 雖然傳遞機制可能會影響程式碼的效能，差別在於通常並不顯著。 一個例外是傳遞實值類型`ByVal`。 在此情況下，Visual Basic 會複製整個資料內容的引數。 因此，對於大數值類型，例如結構，它可以是更有效率，將它傳遞`ByRef`。  
  
     參考類型的資料指標會是複製 （四個位元組 32 位元平台上，在 64 位元平台上的 8 個位元組）。 因此，您可以將類型引數傳遞`String`或`Object`由不含損害效能值。  
  
## <a name="determination-of-the-passing-mechanism"></a>判斷的傳遞機制  
 程序宣告指定的每個參數的傳遞機制。 呼叫程式碼不能覆寫`ByVal`機制。  
  
 如果參數以宣告`ByRef`，呼叫程式碼可以強制執行機制`ByVal`包圍呼叫中的括號括住的引數名稱。 如需詳細資訊，請參閱[如何： 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
 在 Visual Basic 中的預設值是以傳值方式傳遞引數。  
  
## <a name="when-to-pass-an-argument-by-value"></a>傳值方式傳遞引數的時機  
  
-   如果引數呼叫的程式碼項目是不可修改的項目，將對應的參數宣告[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 程式碼不可以變更不可修改元素的值。  
  
-   如果對應的項目是可修改，但您不想要能夠變更其值的程序，將參數宣告`ByVal`。 呼叫程式碼可以變更可修改的項目，以傳值方式傳遞的值。  
  
## <a name="when-to-pass-an-argument-by-reference"></a>傳址方式傳遞引數的時機  
  
-   如果程序確實需要變更呼叫的程式碼中對應的項目，將對應的參數宣告[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。  
  
-   如果正確執行的程式碼相依於程序來變更呼叫的程式碼中對應的項目，將參數宣告`ByRef`。 如果它傳值方式傳遞，或如果呼叫程式碼會覆寫`ByRef`傳遞機制，將引數括在括號內，由程序呼叫可能會產生非預期的結果。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例說明以傳值方式傳遞引數和時機傳址方式傳遞它們。 程序`Calculate`同時具有`ByVal`和`ByRef`參數。 指定利率， `rate`，與總金額， `debt`，程序的工作是計算的新值`debt`也就是套用利率的原始值的結果`debt`。 因為`debt`是`ByRef`參數對應至呼叫程式碼中引數的值會反映新的總數`debt`。 參數`rate`是`ByVal`參數因為`Calculate`不應該變更它的值。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)  
 [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)  
 [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
