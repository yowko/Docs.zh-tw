---
title: <type1>'<typename>' 必須實作介面 '<interfacename>' 的 '<membername>
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 7b74ee3a05000f5d6cd94176b48dea116b647a2a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872176"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1>'\<typename>' 必須實作介面 '\<interfacename>' 的 '\<membername>

' \<typename> ' 必須 \<membername> 針對介面 ' ' 執行 ' ' \<interfacename> 。 執行屬性必須有相符的 ' ReadOnly '/' WriteOnly ' 規範。  
  
 類別或結構宣告來執行介面，但不會執行介面所定義的程式、屬性或事件。 介面的每個成員都必須執行。  
  
 **錯誤識別碼：** BC30154  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 使用與介面中定義的相同名稱和簽章來宣告成員。 請務必至少包含 `End Function` 、 `End Sub` 或 `End Property` 語句。  
  
2. 將 `Implements` 子句加入至 `Function` 、 `Sub` 、 `Property` 或 `Event` 語句的結尾。 例如：  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. 在執行屬性時，請確定 `ReadOnly` 使用和 `WriteOnly` 介面定義中的相同方式來使用或。  
  
4. 在執行屬性時，請 `Get` `Set` 視需要宣告和程式。  
  
## <a name="see-also"></a>另請參閱

- [Implements 陳述式](../statements/implements-statement.md)
- [介面](../../programming-guide/language-features/interfaces/index.md)
