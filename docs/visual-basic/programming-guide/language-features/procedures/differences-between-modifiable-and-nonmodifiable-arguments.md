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
ms.openlocfilehash: 662ad3039bb3fd5c44847d5b2a97a033a18ad063
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071955"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>可修改引數和不可修改引數之間的差異 (Visual Basic)

當您呼叫程式時，通常會將一個或多個引數傳遞給它。 每個引數都對應至基礎程式設計項目。 基礎元素和引數本身可以是可修改或不可修改的。  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>可修改和不可修改的元素  

 程式設計專案可以是可 *修改*的專案，其值可能會變更，或在建立之後具有固定值的 *不可修改元素*。  
  
 下表列出可修改和不可修改的程式設計項目。  
  
|可修改的元素|不可修改的元素|  
|-------------------------|----------------------------|  
|本機變數 (在程式) 內宣告，包括物件變數（唯讀除外）|唯讀變數、欄位和屬性|  
|欄位 (模組、類別和結構) 的成員變數，但唯讀除外|常數和常值|  
|除了唯讀以外的屬性|列舉成員|  
|陣列元素|運算式 (即使其元素可修改) |  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>可修改和不可修改的引數  

 可 *修改的引數* 是具有可修改基礎元素的引數。 呼叫程式碼可以隨時儲存新值，而且如果您傳遞引數 [ByRef](../../../language-reference/modifiers/byref.md)，程式中的程式碼也可以修改呼叫程式碼中的基礎元素。  
  
 *不可變引數*具有不可修改的基礎元素，或已傳遞[ByVal](../../../language-reference/modifiers/byval.md)。 程式無法修改呼叫程式碼中的基礎元素（即使它是可修改的專案）。 如果它是不可修改的元素，則呼叫程式碼本身無法修改它。  
  
 呼叫的程式可能會修改其不可變引數的本機複本，但該修改並不會影響呼叫程式碼中的基礎元素。  
  
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
