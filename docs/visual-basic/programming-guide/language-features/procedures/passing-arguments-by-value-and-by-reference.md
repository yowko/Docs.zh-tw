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
ms.openlocfilehash: b7430b209f53a0a924ec587a0097178baf0075e3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059210"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>以傳值和傳址方式傳遞引數 (Visual Basic)

在 Visual Basic 中，您可以透過傳 *值* 或傳 *址*方式將引數傳遞給程式。 這就是所謂的 *傳遞機制*，它會判斷程式是否可以修改呼叫程式碼中引數的基礎程式設計項目。 程式聲明會藉由指定 [ByVal](../../../language-reference/modifiers/byval.md) 或 [ByRef](../../../language-reference/modifiers/byref.md) 關鍵字來判斷每個參數的傳遞機制。  
  
## <a name="distinctions"></a>區別  

 將引數傳遞給程式時，請注意幾個不同的差異，這些差異會彼此互動：  
  
- 基礎程式設計專案是否可修改或不可修改  
  
- 引數本身是否可修改或不可修改  
  
- 引數是否以傳值或傳址方式傳遞  
  
- 引數資料類型是否為實值型別或參考型別  
  
 如需詳細資訊，請參閱可 [修改和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md) ，以及透過 [傳值和傳址方式傳遞引數之間的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## <a name="choice-of-passing-mechanism"></a>傳遞機制的選擇  

 您應該為每個引數選擇謹慎的傳遞機制。  
  
- **保護**。 在兩個傳遞機制之間進行選擇時，最重要的準則是暴露呼叫變數以進行變更。 傳遞引數的優點是，程式 `ByRef` 可以透過該引數將值傳回給呼叫程式碼。 傳遞引數的優點 `ByVal` 是它會保護變數，使其無法被程式變更。  
  
- **效能**。 雖然傳遞機制可能會影響程式碼的效能，但差異通常不重要。 其中一個例外狀況是傳遞的實值型別 `ByVal` 。 在此情況下，Visual Basic 會複製引數的整個資料內容。 因此，針對大型數值型別（例如結構），傳遞它可能更有效率 `ByRef` 。  
  
     若為參考型別，則只會將資料指標複製到32位平臺上的四個位元組 (四個位元組，) 64 位平臺上的8個位元組。 因此，您可以傳遞類型或傳值的引數， `String` `Object` 而不會犧牲效能。  
  
## <a name="determination-of-the-passing-mechanism"></a>判斷傳遞機制  

 程式聲明會指定每個參數的傳遞機制。 呼叫程式碼無法覆寫 `ByVal` 機制。  
  
 如果以宣告參數 `ByRef` ，呼叫程式碼可以在 `ByVal` 呼叫中將引數名稱括在括弧中，以強制執行機制。 如需詳細資訊，請參閱 [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
 Visual Basic 中的預設值是以傳值方式傳遞引數。  
  
## <a name="when-to-pass-an-argument-by-value"></a>以傳值方式傳遞引數的時機  
  
- 如果引數基礎的呼叫程式碼專案是不可修改的元素，請宣告對應的參數 [ByVal](../../../language-reference/modifiers/byval.md)。 沒有任何程式碼可以變更不可變更元素的值。  
  
- 如果基礎元素是可修改的，但您不想讓程式變更其值，請宣告參數 `ByVal` 。 只有呼叫程式碼可以變更以傳值方式傳遞的可修改元素值。  
  
## <a name="when-to-pass-an-argument-by-reference"></a>以傳址方式傳遞引數的時機  
  
- 如果程式真的需要變更呼叫程式碼中的基礎元素，請宣告對應的參數 [ByRef](../../../language-reference/modifiers/byref.md)。  
  
- 如果正確的程式碼執行取決於變更呼叫程式碼中基礎專案的程式，請宣告參數 `ByRef` 。 如果您以傳值方式傳遞，或呼叫 `ByRef` 程式碼以括弧括住引數來覆寫傳遞機制，則程序呼叫可能會產生非預期的結果。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  

 下列範例說明何時以傳值方式傳遞引數，以及何時以傳址方式傳遞引數。 程式 `Calculate` 同時有 `ByVal` 和 `ByRef` 參數。 如果有利率和 money 的總和，程式的工作 `rate` `debt` 就是計算的新值， `debt` 這是將利率套用至原始值的結果 `debt` 。 因為 `debt` 是 `ByRef` 參數，所以新的總計會反映在呼叫程式碼中對應至的引數值 `debt` 。 參數 `rate` 是 `ByVal` 參數，因為 `Calculate` 不應該變更其值。  
  
### <a name="code"></a>程式碼  

 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [Value Types and Reference Types](../data-types/value-types-and-reference-types.md)
