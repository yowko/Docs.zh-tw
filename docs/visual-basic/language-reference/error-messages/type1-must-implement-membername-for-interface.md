---
title: <type1>'<typename>' 必須實作介面 '<interfacename>' 的 '<membername>
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 4ffe18e11c388a8c69ef0592bde1b78f5b219680
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386850"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1>'\<typename>' 必須實作介面 '\<interfacename>' 的 '\<membername>
' \<typename> ' 必須 \<membername> 為介面 ' ' 執行 ' ' \<interfacename> 。 執行屬性必須有相符的 ' ReadOnly '/' WriteOnly ' 規範。  
  
 類別或結構宣告，用來執行介面，但不會執行介面所定義的程式、屬性或事件。 介面的每個成員都必須實作為。  
  
 **錯誤識別碼：** BC30154  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 宣告具有與介面中所定義相同名稱和簽章的成員。 請務必至少包含 `End Function` 、 `End Sub` 或 `End Property` 語句。  
  
2. 將 `Implements` 子句加入至 `Function` 、 `Sub` 、 `Property` 或 `Event` 語句的結尾。 例如：  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. 在執行屬性時，請確定 `ReadOnly` 使用或的 `WriteOnly` 方式與在介面定義中相同。  
  
4. 在執行屬性時，請 `Get` 適當地宣告和 `Set` 程式。  
  
## <a name="see-also"></a>另請參閱

- [Implements 陳述式](../statements/implements-statement.md)
- [介面](../../programming-guide/language-features/interfaces/index.md)
