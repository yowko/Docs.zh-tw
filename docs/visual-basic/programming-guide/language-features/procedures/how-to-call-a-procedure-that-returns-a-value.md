---
title: 如何：呼叫傳回值的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 53589f84c6675d1e7ae2a593341e5dac747132a9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083973"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>如何：呼叫傳回值的程序 (Visual Basic)

程式會將 `Function` 值傳回給呼叫程式碼。 您可以將其名稱和引數包含在指派語句的右邊或運算式中，來呼叫它。  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>若要呼叫運算式內的函數程式  
  
1. 使用程式 `Function` 名稱的方式與使用變數的方式相同。 您可以 `Function` 在任何可在運算式中使用變數或常數的位置使用程序呼叫。  
  
2. 請以括弧括住程式名稱，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。 不過，使用括弧可讓您的程式碼更容易閱讀。  
  
3. 將引數清單中的引數放在括弧內，並以逗號分隔。 請務必以程式定義對應參數的相同順序提供引數 `Function` 。  
  
     或者，您可以依名稱傳遞一個或多個引數。 如需詳細資訊，請參閱 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)。  
  
4. 從程式傳回的值會參與運算式，就如同變數或常數的值一樣。  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>若要在指派語句中呼叫函數程式  
  
1. 在 `Function` `=` 指派語句中) 登入之後，使用 (的程式名稱。  
  
2. 請以括弧括住程式名稱，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。 不過，使用括弧可讓您的程式碼更容易閱讀。  
  
3. 將引數清單中的引數放在括弧內，並以逗號分隔。 請務必以程式定義對應參數的相同順序提供引數 `Function` ，除非您以名稱傳遞這些引數。  
  
4. 從程式傳回的值會儲存在指派語句左邊的變數或屬性中。  
  
## <a name="example"></a>範例  

 下列範例會呼叫 Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> ，以取得作業系統環境變數的值。 第一行呼叫運算式內的第一行 `Environ` ，而第二行則是在指派語句中呼叫它。 `Environ` 採用變數名稱做為其唯一的引數。 它會將變數的值傳回給呼叫程式碼。  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- [Function 程序](./function-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Function 陳述式](../../../language-reference/statements/function-statement.md)
- [如何：建立傳回值的程序](./how-to-create-a-procedure-that-returns-a-value.md)
- [如何：傳回程序的值](./how-to-return-a-value-from-a-procedure.md)
- [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)
