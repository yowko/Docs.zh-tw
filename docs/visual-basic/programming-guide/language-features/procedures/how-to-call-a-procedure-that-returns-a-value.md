---
title: HOW TO：呼叫程序傳回值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 10167075e903693df804cba044301e1f1bc6306e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974454"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>HOW TO：呼叫程序傳回值 (Visual Basic)
A`Function`程序傳回給呼叫程式碼的值。 您可以呼叫它藉由包含其名稱和引數在指派陳述式或運算式的右側。  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>呼叫運算式內的函式程序  
  
1.  使用`Function`程序的名稱相同的方式，您會使用變數。 您可以使用`Function`程序呼叫的運算式中使用的變數或常數的任何位置。  
  
2.  程序名稱後面加上括號括住的引數清單。 如果不有任何引數，您可以選擇性地省略括號。 不過，使用括號可讓您的程式碼更方便閱讀。  
  
3.  以括弧括住，並以逗號分隔的引數清單括住的引數。 確定您提供的相同順序的引數，`Function`程序會定義對應的參數。  
  
     或者，您可以依名稱傳遞一或多個引數。 如需詳細資訊，請參閱 <<c0> [ 傳遞引數依位置和名稱](./passing-arguments-by-position-and-by-name.md)。  
  
4.  程序所傳回的值加入運算式中只做為值的變數或常數。  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>若要在指派陳述式中呼叫函式程序  
  
1.  使用`Function`遵循相同的程序名稱 (`=`) 登入指派陳述式。  
  
2.  程序名稱後面加上括號括住的引數清單。 如果不有任何引數，您可以選擇性地省略括號。 不過，使用括號可讓您的程式碼更方便閱讀。  
  
3.  以括弧括住，並以逗號分隔的引數清單括住的引數。 確定您提供的相同順序的引數，`Function`程序會定義對應的參數，除非您依名稱傳遞它們。  
  
4.  程序所傳回的值儲存在變數或指派陳述式左邊的屬性。  
  
## <a name="example"></a>範例  
 下列範例會呼叫 Visual Basic<xref:Microsoft.VisualBasic.Interaction.Environ%2A>擷取的作業系統環境變數的值。 第一個明細項目呼叫`Environ`內使用運算式中，且第二個列中呼叫它的指派陳述式。 `Environ` 使用變數名稱做為其唯一引數。 呼叫程式碼，它就會傳回變數的值。  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>另請參閱
- [函式程序](./function-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)
- [如何：建立程序傳回值](./how-to-create-a-procedure-that-returns-a-value.md)
- [如何：從程序傳回值](./how-to-return-a-value-from-a-procedure.md)
- [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)
