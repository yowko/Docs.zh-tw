---
title: <type1>'<typename>' 必須實作介面 '<interfacename>' 的 '<methodname>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 8bf8872277ec901e066a8b950aaf3e61babfcc48
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872108"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1>'\<typename>' 必須實作介面 '\<interfacename>' 的 '\<methodname>

類別或結構宣告來執行介面，但不會執行介面所定義的程式。 介面的每個成員都必須執行。  
  
 **錯誤識別碼：** BC30149  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 使用與介面中定義的相同名稱和簽章來宣告程式。 請務必至少包含 `End Function` 或 `End Sub` 語句。  
  
2. 將 `Implements` 子句加入至或語句的結尾 `Function` `Sub` 。 例如：  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>另請參閱

- [Implements 陳述式](../statements/implements-statement.md)
- [介面](../../programming-guide/language-features/interfaces/index.md)
