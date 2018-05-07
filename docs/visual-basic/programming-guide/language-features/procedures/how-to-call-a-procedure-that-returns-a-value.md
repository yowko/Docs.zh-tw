---
title: 如何：呼叫傳回值的程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 35f757609b6d0b36652db3b14e62ecd299a063ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>如何：呼叫傳回值的程序 (Visual Basic)
A`Function`程序傳回給呼叫程式碼的值。 您可以呼叫它藉由其名稱和引數右側在指派陳述式或運算式中。  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>若要呼叫的函式程序，在運算式內  
  
1.  使用`Function`程序的名稱相同的方式，您會使用變數。 您可以使用`Function`程序呼叫的運算式中使用變數或常數的任何地方。  
  
2.  請依照下列程序名稱與括號來括住的引數清單。 如果有任何引數，您可以選擇性地省略括號。 不過，使用括號可讓您的程式碼更方便閱讀。  
  
3.  將引數放在括號，並以逗號分隔的引數清單。 確定您提供的相同順序的引數，`Function`程序所定義的對應參數。  
  
     或者，您可以依名稱傳遞一個或多個引數。 如需詳細資訊，請參閱[傳遞引數依位置和名稱](./passing-arguments-by-position-and-by-name.md)。  
  
4.  程序所傳回的值加入運算式中只做為值的變數或常數。  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>在指派陳述式中呼叫的函式程序  
  
1.  使用`Function`之後等程序名稱 (`=`) 登入指派陳述式。  
  
2.  請依照下列程序名稱與括號來括住的引數清單。 如果有任何引數，您可以選擇性地省略括號。 不過，使用括號可讓您的程式碼更方便閱讀。  
  
3.  將引數放在括號，並以逗號分隔的引數清單。 確定您提供的相同順序的引數，`Function`程序所定義的對應參數，除非您依名稱傳遞它們。  
  
4.  程序所傳回的值會儲存在變數或指派陳述式左邊的屬性。  
  
## <a name="example"></a>範例  
 下列範例會呼叫 Visual Basic<xref:Microsoft.VisualBasic.Interaction.Environ%2A>擷取作業系統的環境變數的值。 第一列呼叫`Environ`內使用運算式中，且第二個列中呼叫它的指派陳述式。 `Environ` 使用變數名稱做為其唯一的引數。 它會傳回呼叫程式碼的變數的值。  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [函式程序](./function-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [如何：建立傳回值的程序](./how-to-create-a-procedure-that-returns-a-value.md)  
 [如何：傳回程序的值](./how-to-return-a-value-from-a-procedure.md)  
 [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)
