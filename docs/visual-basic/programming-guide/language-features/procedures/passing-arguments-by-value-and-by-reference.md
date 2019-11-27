---
title: 以傳值和傳址方式傳遞引數
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: 28e59753a35ab67b15fbc549df5bb8a3489aba5a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352611"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>以傳值和傳址方式傳遞引數 (Visual Basic)
在 Visual Basic 中，您可以透過*值*或傳*址*方式將引數傳遞給程式。 這就是所謂的*傳遞機制*，它會判斷程式是否可以修改呼叫程式碼中引數基礎的程式設計項目。 程式宣告會藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字，來判斷每個參數的傳遞機制。  
  
## <a name="distinctions"></a>加以  
 將引數傳遞至程式時，請留意幾個彼此互動的不同區別：  
  
- 基礎程式設計項目是否為可修改或不可修改  
  
- 引數本身是否為可修改或不可變  
  
- 引數是以傳值方式或依參考方式傳遞  
  
- 引數資料類型是否為實數值型別或參考型別  
  
 如需詳細資訊，請參閱可[修改的和不可變的引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)，以及透過[值和傳址方式傳遞引數的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## <a name="choice-of-passing-mechanism"></a>選擇傳遞機制  
 您應該針對每個引數仔細選擇傳遞機制。  
  
- **保護**。 在兩個傳遞機制之間選擇時，最重要的條件是公開呼叫變數以進行變更。 傳遞引數 `ByRef` 的優點是程式可以透過該引數將值傳回給呼叫程式碼。 傳遞引數 `ByVal` 的優點是它會保護變數，使其不會被程式變更。  
  
- **效能**。 雖然傳遞機制可能會影響您程式碼的效能，但兩者之間的差異通常不明顯。 其中一個例外狀況是傳遞 `ByVal`的實值型別。 在此情況下，Visual Basic 會複製引數的整個資料內容。 因此，對於大型實數值型別（例如結構），將它傳遞 `ByRef`會更有效率。  
  
     針對參考型別，只會複製資料的指標（32位平臺上的四個位元組，64位平臺上為8個位元組）。 因此，您可以將類型 `String` 或 `Object` 的引數傳遞給值，而不會犧牲效能。  
  
## <a name="determination-of-the-passing-mechanism"></a>判斷傳遞機制  
 程式宣告會指定每個參數的傳遞機制。 呼叫程式碼無法覆寫 `ByVal` 機制。  
  
 如果參數是使用 `ByRef`所宣告，則呼叫程式碼可以藉由在呼叫的括弧中括住引數名稱，強制將機制 `ByVal`。 如需詳細資訊，請參閱[如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
 Visual Basic 中的預設值是以傳值方式傳遞引數。  
  
## <a name="when-to-pass-an-argument-by-value"></a>以傳值方式傳遞引數的時機  
  
- 如果引數基礎的呼叫程式碼元素是無法修改的元素，請宣告對應的參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 沒有任何程式碼可以變更無法修改的元素值。  
  
- 如果基礎元素是可修改的，但您不想讓程式能夠變更其值，請 `ByVal`宣告參數。 只有呼叫程式碼可以變更以傳值方式傳遞之可修改元素的值。  
  
## <a name="when-to-pass-an-argument-by-reference"></a>以傳址方式傳遞引數的時機  
  
- 如果程式確實需要變更呼叫程式碼中的基礎元素，請宣告對應的參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。  
  
- 如果程式碼的正確執行取決於變更呼叫程式碼中基礎元素的程式，請 `ByRef`宣告參數。 如果您以傳值方式傳遞它，或是呼叫程式碼藉由以括弧括住引數來覆寫 `ByRef` 傳遞機制，則程序呼叫可能會產生非預期的結果。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例說明何時以傳值方式傳遞引數，以及何時以傳址方式傳遞。 程式 `Calculate` 同時具有 `ByVal` 和 `ByRef` 參數。 假設有利率、`rate`和 money 的總和，`debt`，程式的工作就是為 `debt` 計算新的值，這是將利率套用至原始 `debt`值的結果。 因為 `debt` 是 `ByRef` 參數，所以新的總計會反映在呼叫程式碼中對應至 `debt`的引數值。 參數 `rate` 是 `ByVal` 參數，因為 `Calculate` 不應變更其值。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
