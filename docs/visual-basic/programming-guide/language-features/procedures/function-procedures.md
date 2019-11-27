---
title: 函式程序
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b62a730e8ade211821826afbb55fa8858ea311a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341093"
---
# <a name="function-procedures-visual-basic"></a>函式程序 (Visual Basic)
`Function` 程式是以 `Function` 和 `End Function` 語句括住的一系列 Visual Basic 語句。 `Function` 程式會執行工作，然後將控制權傳回給呼叫程式碼。 當它傳回 control 時，它也會將值傳回給呼叫程式碼。  
  
 每次呼叫程式時，其語句都會執行，從 `Function` 語句後面的第一個可執行語句開始，並以遇到的第一個 `End Function`、`Exit Function`或 `Return` 語句為結尾。  
  
 您可以在模組、類別或結構中定義 `Function` 程式。 預設為 `Public`，這表示您可以從應用程式的任何位置呼叫它，以存取您在其中定義的模組、類別或結構。  
  
 `Function` 程式可以接受引數，例如常數、變數或運算式，由呼叫程式碼傳遞給它。  
  
## <a name="declaration-syntax"></a>宣告語法  
 宣告 `Function` 程式的語法如下：  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 修飾*詞可以指定*有關多載、覆寫、共用和遮蔽的存取層級和資訊。 如需詳細資訊，請參閱[Function 語句](../../../../visual-basic/language-reference/statements/function-statement.md)。  
  
 您可以用與[Sub 程式](./sub-procedures.md)相同的方式宣告每個參數。  
  
### <a name="data-type"></a>資料類型  
 每個 `Function` 程式都有一種資料類型，就像每個變數一樣。 這個資料類型是由 `Function` 語句中的 `As` 子句所指定，它會判斷函式傳回給呼叫程式碼之值的資料類型。 下列範例宣告說明這種情況。  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 如需詳細資訊，請參閱[Function 語句](../../../../visual-basic/language-reference/statements/function-statement.md)中的「元件」。  
  
## <a name="returning-values"></a>傳回值  
 `Function` 程式傳回給呼叫端程式碼的值稱為其傳回值。 程式會以下列兩種方式的其中一種傳回此值：  
  
- 它會使用 `Return` 語句來指定傳回值，並將控制權立即傳回給呼叫程式。 下列範例將說明這點。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- 它會在程式的一個或多個語句中，將值指派給它自己的函數名稱。 在執行 `Exit Function` 或 `End Function` 語句之前，控制項不會回到呼叫程式。 下列範例將說明這點。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 將傳回值指派給函數名稱的優點是，控制項不會從程式傳回，直到遇到 `Exit Function` 或 `End Function` 語句為止。 這可讓您指派初步值，並在稍後視需要進行調整。  
  
 如需傳回值的詳細資訊，請參閱[Function 語句](../../../../visual-basic/language-reference/statements/function-statement.md)。 如需傳回陣列的詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="calling-syntax"></a>呼叫語法  
 您可以藉由在指派語句的右邊或運算式中包含其名稱和引數來叫用 `Function` 程式。 您必須提供所有非選擇性引數的值，而且必須將引數清單括在括弧中。 如果未提供任何引數，您可以選擇性地省略括弧。  
  
 呼叫 `Function` 程式的語法如下所示：  
  
 *左*值`=`*functionname* `[(` *argumentlist* `)]`  
  
 `If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`*expression* `) Then`  
  
 當您呼叫 `Function` 程式時，不需要使用其傳回值。 如果不這麼做，則會執行函式的所有動作，但會忽略傳回值。 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 通常是以這種方式呼叫。  
  
### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例  
 下列 `Function` 程式會計算直角三角形的最長邊（或斜邊），並指定其他兩邊的值。  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 下列範例顯示 `hypotenuse`的一般呼叫。  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)
- [如何：建立傳回值的程序](./how-to-create-a-procedure-that-returns-a-value.md)
- [如何：傳回程序的值](./how-to-return-a-value-from-a-procedure.md)
- [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)
