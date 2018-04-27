---
title: 函式程序 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad4f55a9dd9fbd68c36dd53a01f97ddb03c2bb9b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="function-procedures-visual-basic"></a>函式程序 (Visual Basic)
A`Function`程序是一系列的 Visual Basic 陳述式加上`Function`和`End Function`陳述式。 `Function`程序執行的工作，並再將控制權傳回給呼叫程式碼。 當它傳回控制項時，它也會傳回值，呼叫程式碼。  
  
 每次程序呼叫時，執行時，其陳述式開頭之後的第一個可執行陳述式`Function`陳述式，並與第一個結束`End Function`， `Exit Function`，或`Return`出現陳述式。  
  
 您可以定義`Function`模組、 類別或結構中的程序。 它是`Public`根據預設，這表示您可以從任何位置呼叫它可存取模組、 類別或結構定義它的應用程式中。  
  
 A`Function`程序可以接受引數，例如常數、 變數或運算式，則呼叫程式碼傳遞給它。  
  
## <a name="declaration-syntax"></a>宣告語法  
 宣告的語法`Function`程序如下所示：  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *修飾詞*可以指定存取層級和多載，覆寫、 共用、 與遮蔽的相關資訊。 如需詳細資訊，請參閱[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。  
  
 您每個參數宣告相同的方式[Sub 程序](./sub-procedures.md)。  
  
### <a name="data-type"></a>資料類型  
 每個`Function`程序中的資料類型，只為每個變數。 此資料類型，由指定`As`中的子句`Function`陳述式，並決定函式傳回給呼叫程式碼之值的資料類型。 下列範例宣告來說明這點。  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 如需詳細資訊，請參閱 「 部分 」 中[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。  
  
## <a name="returning-values"></a>傳回值  
 值`Function`程序會傳送回到呼叫的程式碼會呼叫它的傳回值。 程序會傳回此值中有兩種：  
  
-   它會使用`Return`陳述式來指定傳回值，並傳回控制立即呼叫程式。 下列範例將說明這點。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   它會將值指派給自己的程序的一個或多個陳述式中的函式名稱。 控制項不會傳回給呼叫程式直到`Exit Function`或`End Function`執行陳述式。 下列範例將說明這點。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 將傳回的值指派給函式名稱的優點是，控制項不會傳回從程序直到它遇到`Exit Function`或`End Function`陳述式。 這可讓您指派初步的值，並視需要稍後調整它。  
  
 如需傳回值的詳細資訊，請參閱[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。 傳回陣列的相關資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="calling-syntax"></a>呼叫語法  
 您可以叫用`Function`藉由包含其名稱和引數在右側，即在指派陳述式或運算式中的程序。 您必須提供值給不是選擇性的所有引數，您必須將引數清單括在括號中。 如果已不提供任何引數，您可以選擇性地省略括號。  
  
 若要呼叫的語法`Function`程序如下所示：  
  
 *左值*`=`*functionname* `[(` *argumentlist*  `)]`  
  
 `If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`*運算式*  `) Then`  
  
 當您呼叫`Function`程序中，您不必使用它的傳回值。 如果未指定，會執行的函式的所有動作，但已忽略傳回值。 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 通常稱為以這種方式。  
  
### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例  
 下列`Function`已知值的其他兩個邊直角三角形斜邊的最長邊，程序會計算。  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 下列範例會示範一般呼叫`hypotenuse`。  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [Sub 程序](./sub-procedures.md)  
 [屬性程序](./property-procedures.md)  
 [運算子程序](./operator-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [如何：建立傳回值的程序](./how-to-create-a-procedure-that-returns-a-value.md)  
 [如何：傳回程序的值](./how-to-return-a-value-from-a-procedure.md)  
 [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)
