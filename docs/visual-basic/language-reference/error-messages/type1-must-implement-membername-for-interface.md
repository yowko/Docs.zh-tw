---
title: <type1>'<typename>' 必須實作介面 '<interfacename>' 的 '<membername>
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a824b66eaad964049ced5cae5eb2cc370d00ba7f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696887"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>@no__t 0type1 > ' \<typename > ' 必須為介面 ' \<interfacename > ' 執行 ' \<membername > '
' @no__t 0typename > ' 必須為介面 ' \<interfacename > ' 實執行 ' \<membername > '。 執行屬性必須有相符的 ' ReadOnly '/' WriteOnly ' 規範。  
  
 類別或結構宣告，用來執行介面，但不會執行介面所定義的程式、屬性或事件。 介面的每個成員都必須實作為。  
  
 **錯誤識別碼：** BC30154  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 宣告具有與介面中所定義相同名稱和簽章的成員。 請務必至少包含 `End Function`、`End Sub` 或 @no__t 2 語句。  
  
2. 將 `Implements` 子句加入至 `Function`、`Sub`、`Property` 或 @no__t 4 語句的結尾。 例如:  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. 在執行屬性時，請確定 `ReadOnly` 或 `WriteOnly` 的使用方式與在介面定義中相同。  
  
4. 在執行屬性時，請視需要宣告 `Get` 和 @no__t 1 程式。  
  
## <a name="see-also"></a>另請參閱

- [Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
