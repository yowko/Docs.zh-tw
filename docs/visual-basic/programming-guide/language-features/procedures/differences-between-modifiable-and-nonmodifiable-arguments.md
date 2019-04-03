---
title: 可修改引數和不可修改引數之間的差異 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: a880ae8c13eebd5d9d325468098e058f58d3fa71
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826661"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>可修改引數和不可修改引數之間的差異 (Visual Basic)
當您呼叫程序時，您通常會傳遞一或多個引數給它。 每個引數會對應至基礎的程式設計項目。 基礎元素及引數本身可以是可修改或不可修改。  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>可修改和不可修改的項目  
 程式設計項目可以是*可修改的項目*，且可以包含它的值變更，或有*不可修改的項目*，一旦建立之後，其中會包含固定的值。  
  
 下表列出可修改和不可修改的程式設計項目。  
  
|可修改的項目|不可修改的項目|  
|-------------------------|----------------------------|  
|本機變數 （在程序宣告），包括物件的變數，但唯讀除外|唯讀變數、 欄位和屬性|  
|除了唯讀的欄位 （模組、 類別和結構的成員變數，）|常數和常值|  
|屬性，除了唯讀|列舉型別成員|  
|陣列項目|運算式 （即使其元素都是可修改）|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>可修改和不可修改引數  
 A*可修改引數*是具有可修改的基礎項目。 呼叫端程式碼可以在任何時間，儲存新的值，如果您傳遞的引數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，程序中的程式碼也可以修改呼叫程式碼對應的項目。  
  
 A*不可修改引數*已經不可修改的基礎項目，或傳遞[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 此程序無法修改呼叫程式碼中，對應的項目，即使它是可修改的項目。 如果它是不可修改的項目時，呼叫程式碼本身無法加以修改。  
  
 呼叫的程序可能會修改為不可修改引數，其本機複本，但該修改並不會影響呼叫端程式碼對應的項目。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：程序引數的值變更](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：強制以傳值方式傳遞的引數](./how-to-force-an-argument-to-be-passed-by-value.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
