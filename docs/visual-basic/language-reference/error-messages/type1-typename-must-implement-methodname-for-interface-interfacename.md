---
title: <type1>'<typename>'必須實作'<methodname>'的介面'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 432f089bc77928308820d7456d930fba8dc513f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304905"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 >'\<類型名稱 >' 必須實作 '\<方法名稱 >' 的介面'\<介面名稱 >'
類別或結構宣告實作介面，但不會實作該介面所定義的程序。 必須實作介面的每個成員。  
  
 **錯誤 ID:** BC30149  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 宣告具有相同的名稱與簽章的介面中所定義的程序。 務必要包含在至少`End Function`或`End Sub`陳述式。  
  
2. 新增`Implements`子句來結束`Function`或`Sub`陳述式。 例如:   
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>另請參閱

- [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
