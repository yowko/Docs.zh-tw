---
title: <type1>'<typename>'必須實作'<membername>'的介面'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 86b0d46e0e27b2fd8d1fccb37f4a3c45e95f5f63
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295324"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 >'\<類型名稱 >' 必須實作 '\<成員名稱 >' 的介面'\<介面名稱 >'
'\<類型名稱 >' 必須實作'\<成員名稱 >' 的介面 '\<介面名稱 >'。 實作屬性必須比對 'ReadOnly '/' WriteOnly' 規範。  
  
 類別或結構宣告實作介面，但不會實作程序、 屬性或介面所定義的事件。 必須實作介面的每個成員。  
  
 **錯誤 ID:** BC30154  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 宣告具有相同的名稱和簽章的介面中所定義的成員。 務必要包含在至少`End Function`， `End Sub`，或`End Property`陳述式。  
  
2. 新增`Implements`子句來結束`Function`， `Sub`， `Property`，或`Event`陳述式。 例如：  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. 當實作的屬性，請確定`ReadOnly`或`WriteOnly`用於介面定義的相同方式。  
  
4. 當實作的屬性，宣告`Get`和`Set`程序，適當地。  
  
## <a name="see-also"></a>另請參閱

- [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
