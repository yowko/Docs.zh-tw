---
title: 可修改引數和不可修改引數之間的差異
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 733f92cc2cdaa6e923c57649774ceb64de172c18
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403339"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>可修改引數和不可修改引數之間的差異 (Visual Basic)
當您呼叫程式時，通常會傳遞一或多個引數給它。 每個引數都會對應至基礎程式設計項目。 基礎元素和引數本身都可以是可修改或不可修改的。  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>可修改和不可修改的元素  
 程式設計專案可以是可*修改的元素*，其值可能會變更，或無法修改的*元素*，其在建立後已有固定值。  
  
 下表列出可修改和不可修改的程式設計項目。  
  
|可修改的元素|不可修改元素|  
|-------------------------|----------------------------|  
|本機變數（在程式內宣告），包括物件變數（唯讀除外）|唯讀變數、欄位和屬性|  
|欄位（模組、類別和結構的成員變數），除了唯讀以外|常數和常值|  
|屬性，除了唯讀以外|列舉成員|  
|陣列元素|運算式（即使它們的元素是可修改的）|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>可修改和不可修改的引數  
 可*修改的引數*是一個具有可修改的基礎元素。 呼叫程式碼可以隨時儲存新的值，而且如果您傳遞引數[ByRef](../../../language-reference/modifiers/byref.md)，程式中的程式碼也可以修改呼叫程式碼中的基礎元素。  
  
 不可修改的*引數*具有無法修改的基礎元素，或已傳遞[ByVal](../../../language-reference/modifiers/byval.md)。 程式無法修改呼叫程式碼中的基礎元素，即使它是可修改的元素。 如果它是無法修改的元素，則呼叫程式碼本身無法加以修改。  
  
 被呼叫的程式可能會修改其不可變引數的本機複本，但該修改不會影響呼叫程式碼中的基礎元素。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [以傳值或傳址方式傳遞引數的差別](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [如何：變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)
- [如何：防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [如何：強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [Value Types and Reference Types](../data-types/value-types-and-reference-types.md)
