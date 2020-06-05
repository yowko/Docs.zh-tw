---
title: 如何：呼叫傳回值的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: a110cf9f3b42c7244d8d5bf7b49d5e6dac8c2e21
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388760"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>如何：呼叫傳回值的程序 (Visual Basic)
程式會將 `Function` 值傳回給呼叫程式碼。 您可以將其名稱和引數包含在指派語句的右邊或運算式中，藉以呼叫它。  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>若要在運算式內呼叫函式程式  
  
1. 使用程式 `Function` 名稱的方式，與使用變數相同。 您可以 `Function` 在任何可在運算式中使用變數或常數的地方使用程序呼叫。  
  
2. 請在程式名稱後面加上括弧，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。 不過，使用括弧可讓您的程式碼更容易閱讀。  
  
3. 將引數放在括弧內的引數清單中，並以逗號分隔。 請務必依照程式定義對應參數的相同順序來提供引數 `Function` 。  
  
     或者，您可以依名稱傳遞一或多個引數。 如需詳細資訊，請參閱[依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)。  
  
4. 從程式傳回的值會參與運算式，就如同變數或常數的值一樣。  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>若要在指派語句中呼叫函數程式  
  
1. 請 `Function` 在指派語句中的等號（）後面使用程式名稱 `=` 。  
  
2. 請在程式名稱後面加上括弧，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。 不過，使用括弧可讓您的程式碼更容易閱讀。  
  
3. 將引數放在括弧內的引數清單中，並以逗號分隔。 請務必依照程式定義對應參數的順序來提供引數 `Function` ，除非您依名稱傳遞它們。  
  
4. 從程式傳回的值會儲存在指派語句左側的變數或屬性中。  
  
## <a name="example"></a>範例  
 下列範例會呼叫 Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> 來取出作業系統環境變數的值。 第一行會在 `Environ` 運算式內呼叫，而第二行則會在指派語句中呼叫它。 `Environ`將變數名稱當做其唯一引數使用。 它會將變數的值傳回給呼叫程式碼。  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- [Function 程序](./function-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Function 陳述式](../../../language-reference/statements/function-statement.md)
- [如何：建立傳回值的程序](./how-to-create-a-procedure-that-returns-a-value.md)
- [如何：傳回程序的值](./how-to-return-a-value-from-a-procedure.md)
- [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)
