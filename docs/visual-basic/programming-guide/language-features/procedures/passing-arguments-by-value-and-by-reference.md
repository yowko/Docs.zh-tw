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
ms.openlocfilehash: eb2260c6547d4f1cd7d9c23445ac38ac600e3535
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638871"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>以傳值和傳址方式傳遞引數 (Visual Basic)
在 Visual Basic 中，您可以將引數傳遞至程序*值所*或是*傳址*。 這就所謂*傳遞機制*，它決定程序是否可以修改基礎呼叫程式碼中的引數的程式設計項目。 程序宣告會決定每個參數的傳遞機制，藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字。  
  
## <a name="distinctions"></a>差異  
 將引數傳遞至程序時, 留意彼此互動的數個不同差異：  
  
- 基礎的程式設計項目是否為可修改  
  
- 引數本身是否為可修改  
  
- 傳值或傳址是否傳遞引數  
  
- 引數資料類型是否為實值類型或參考型別  
  
 如需詳細資訊，請參閱 <<c0> [ 修改之間的差異和不可修改引數](./differences-between-modifiable-and-nonmodifiable-arguments.md)並[差異之間傳遞的引數的值和傳址](./differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## <a name="choice-of-passing-mechanism"></a>選擇的傳遞機制  
 您應該選擇仔細的每個引數的傳遞機制。  
  
- **保護**。 在選擇兩種傳遞機制之間，最重要的準則會是呼叫來變更變數的風險。 傳遞引數的好處`ByRef`是程序可以傳回呼叫的程式碼，透過該引數的值。 傳遞引數的好處`ByVal`是無法變更程序所保護的變數。  
  
- **效能**。 雖然的傳遞機制可能會影響您的程式碼的效能，差別在於通常並不顯著。 唯一的例外是傳遞實值型別`ByVal`。 在此情況下，Visual Basic 會複製整個資料內容的引數。 因此，對於大數值類型，例如結構，它可能會更有效率，將它傳遞`ByRef`。  
  
     若是參考類型，資料指標是複製 （四位元組在 32 位元平台，在 64 位元平台上的八個位元組）。 因此，您可以在其中傳遞的型別引數`String`或`Object`值而不損害效能。  
  
## <a name="determination-of-the-passing-mechanism"></a>判斷的傳遞機制  
 程序宣告會指定每個參數的傳遞機制。 呼叫端程式碼無法覆寫`ByVal`機制。  
  
 如果參數以宣告`ByRef`，呼叫程式碼可以強制機制`ByVal`方法中呼叫中的括號括住引數名稱。 如需詳細資訊，請參閱[如何：強制以傳值方式傳遞的引數](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
 在 Visual Basic 中的預設值是以傳值方式傳遞引數。  
  
## <a name="when-to-pass-an-argument-by-value"></a>傳值方式傳遞引數的時機  
  
- 如果引數呼叫的程式碼項目是不可修改的項目，將宣告對應的參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 程式碼不可以變更不可修改元素的值。  
  
- 如果對應的項目是可修改，但您不想要能夠將其值變更的程序，將參數宣告`ByVal`。 呼叫程式碼可以變更可修改的項目，以傳值方式傳遞的值。  
  
## <a name="when-to-pass-an-argument-by-reference"></a>傳址方式傳遞引數的時機  
  
- 如果程序確實需要變更呼叫程式碼對應的項目，將對應的參數宣告[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。  
  
- 如果正確執行的程式碼相依於程序來變更呼叫程式碼對應的項目，將參數宣告`ByRef`。 如果您傳遞的值，或如果呼叫程式碼會覆寫`ByRef`傳遞機制，藉由將引數括在括號中的程序呼叫可能會產生非預期的結果。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會說明何時以傳值方式傳遞引數，以及何時傳址方式傳遞它們。 程序`Calculate`同時具有`ByVal`和`ByRef`參數。 指定的利率， `rate`，和總金額， `debt`，程序的工作是計算的新值`debt`結果的原始值上套用利率的`debt`。 因為`debt`已`ByRef`參數，對應至呼叫端程式碼中的引數的值會反映新的總數`debt`。 參數`rate`已`ByVal`參數因為`Calculate`不應該變更其值。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [如何：程序引數的值變更](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：強制以傳值方式傳遞的引數](./how-to-force-an-argument-to-be-passed-by-value.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
