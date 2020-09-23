---
title: 如何：強制以傳值方式傳遞引數
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 0be49e7d4aacbb30956bda7f6ee8494a7ded8b78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071621"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>如何：強制以傳值方式傳遞引數 (Visual Basic)

程式聲明會決定傳遞機制。 如果參數宣告為 [ByRef](../../../language-reference/modifiers/byref.md)，Visual Basic 預期會以傳址方式傳遞對應的引數。 這可讓程式變更呼叫程式碼中引數的基礎程式設計項目值。 如果您想要針對這類變更保護基礎元素，您可以藉 `ByRef` 由將引數名稱括在括弧中，以覆寫程序呼叫中的傳遞機制。 這些括弧除了括住呼叫中的引數清單的括弧之外。  
  
 呼叫程式碼無法覆寫 [ByVal](../../../language-reference/modifiers/byval.md) 機制。  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>強制以傳值方式傳遞引數  
  
- 如果在程式中宣告對應的參數 `ByVal` ，您就不需要採取任何額外的步驟。 Visual Basic 已經預期以傳值方式傳遞引數。  
  
- 如果在程式中宣告對應的參數 `ByRef` ，請將引數括在程序呼叫的括弧中。  
  
## <a name="example"></a>範例  

 下列範例會覆寫 `ByRef` 參數宣告。 在強制的呼叫中 `ByVal` ，請注意兩個層級的括弧。  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 當 `str` 以引數清單中的額外括弧括住時，程式 `setNewString` 無法在呼叫程式碼中變更其值，而且會 `MsgBox` 顯示「如果傳遞的 ByVal 無法取代」。 當未 `str` 以額外括弧括住時，程式可以變更它，並 `MsgBox` 顯示 "This 是 inString 引數的新值"。  
  
## <a name="compile-the-code"></a>編譯程式碼  

 當您以傳址方式傳遞變數時，您必須使用 `ByRef` 關鍵字來指定此機制。  
  
 Visual Basic 中的預設值是以傳值方式傳遞引數。 不過，最好的程式設計作法是在每個宣告的參數中包含 [ByVal](../../../language-reference/modifiers/byval.md) 或 [ByRef](../../../language-reference/modifiers/byref.md) 關鍵字。 這可讓您的程式碼更容易閱讀。  
  
## <a name="robust-programming"></a>穩固程式設計  

 如果程式宣告參數 [ByRef](../../../language-reference/modifiers/byref.md)，正確的程式碼執行可能會取決於是否能夠變更呼叫程式碼中的基礎元素。 如果呼叫程式碼以括弧括住引數來覆寫此呼叫機制，或是傳遞不可修改的引數，則程式無法變更基礎元素。 這可能會在呼叫程式碼中產生非預期的結果。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  

 在允許程式變更呼叫程式碼中引數的基礎值時，一律會有潛在的風險。 請確定您預期會變更此值，並在使用它之前準備好檢查其有效性。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [可修改引數和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [Value Types and Reference Types](../data-types/value-types-and-reference-types.md)
