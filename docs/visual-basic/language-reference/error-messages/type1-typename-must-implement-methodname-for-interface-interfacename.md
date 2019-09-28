---
title: <type1>'<typename>' 必須實作介面 '<interfacename>' 的 '<methodname>
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591588"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>@no__t 0type1 > ' \<typename > ' 必須為介面 ' \<interfacename > ' 執行 ' \<methodname > '
類別或結構宣告，用來執行介面，但不會執行介面所定義的程式。 介面的每個成員都必須實作為。  
  
 **錯誤識別碼：** BC30149  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 使用與介面中所定義相同的名稱和簽章來宣告程式。 請務必至少包含 `End Function` 或 `End Sub` 語句。  
  
2. 將 `Implements` 子句加入至 `Function` 或 @no__t 2 語句的結尾。 例如:  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>另請參閱

- [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
