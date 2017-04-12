---
title: "Sub 程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Sub procedures, about Sub procedures
- statement blocks
- Sub procedures, calling
- procedures, calling
- Sub procedures, syntax
- Sub procedures
- procedures, Sub
- syntax, Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d224fa3338ca707070ee431380578a8fdde47e07
ms.lasthandoff: 03/13/2017

---
# <a name="sub-procedures-visual-basic"></a>Sub 程序 (Visual Basic)
A`Sub`程序是一系列的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]陳述式括住`Sub`和`End Sub`陳述式。 `Sub`程序執行的工作，然後將控制權還給呼叫的程式碼，但它不會傳回呼叫程式碼的值。  
  
 每次呼叫此程序時，其執行陳述式，從開始之後的第一個可執行陳述式`Sub`陳述式，直到第一個`End Sub`， `Exit Sub`，或`Return`陳述式時發生。  
  
 您可以定義`Sub`模組、 類別和結構中的程序。 根據預設，它是`Public`，這表示您可以呼叫從任何地方存取模組、 類別或結構定義它的應用程式中。 詞彙，*方法*，描述`Sub`或`Function`從其定義外部存取的程序模組、 類別或結構。 如需詳細資訊，請參閱[程序](./index.md)。  
  
 A`Sub`程序可以取得引數，例如常數、 變數或運算式，則呼叫程式碼傳遞給它。  
  
## <a name="declaration-syntax"></a>宣告語法  
 宣告的語法`Sub`程序如下︰  
  
 `[`*modifiers* `] Sub`*subname* `[(` *parameterlist*  `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers`可以指定存取層級和多載、 覆寫、 共用、 及遮蔽的相關資訊。 如需詳細資訊，請參閱[Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
## <a name="parameter-declaration"></a>參數宣告  
 您可以宣告類似於如何宣告變數，指定參數名稱和資料類型的每個程序參數。 您也可以指定傳遞機制，以及是否為選擇性參數或參數陣列。  
  
 參數清單中的每個參數的語法如下所示︰  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*`As`*資料型別    *  
  
 如果參數是選擇性的您也必須提供預設值，如其宣告的一部分。 指定預設值的語法如下所示︰  
  
 `Optional [ByVal | ByRef]`  *parametername*`As`*資料型別*`=`*預設值        *  
  
### <a name="parameters-as-local-variables"></a>本機變數與參數  
 當控制權會傳遞至程序時，每個參數會被視為本機變數中。 這表示，其存留期相同的程序，且其範圍是整個程序。  
  
## <a name="calling-syntax"></a>呼叫語法  
 您可以叫用`Sub`明確地用獨立呼叫的陳述式的程序。 您無法使用該名稱在運算式中呼叫它。 您必須提供值不是選擇性的所有引數，您必須將引數清單括在括號中。 如果已不提供任何引數，您可以省略括號。 使用`Call`關鍵字是選擇性的但不是建議使用。  
  
 呼叫語法`Sub`程序如下︰  
  
 `[Call]`  *subname* `[(` *argumentlist*`)]`  
  
 您可以呼叫`Sub`方法從其定義在類別之外。 首先，您必須使用`New`關鍵字來建立類別的執行個體或呼叫的方法會傳回類別的執行個體。 如需詳細資訊，請參閱[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)。 然後，您可以使用下列語法來呼叫`Sub`執行個體物件上的方法︰  
  
 *Object*.*methodname*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例  
 下列`Sub`程序會告知電腦運算子若要執行，應用程式的工作也會顯示時間戳記。 而不必重複此程式碼開頭的每項工作，應用程式只會呼叫`tellOperator`從不同位置。 每個呼叫會傳遞的字串`task`識別正在啟動工作的引數。  
  
 [!code-vb[VbVbcnProcedures #&2;](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 下列範例會示範一般呼叫`tellOperator`。  
  
 [!code-vb[VbVbcnProcedures #&3;](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [Function 程序](./function-procedures.md)   
 [Property 程序](./property-procedures.md)   
 [運算子程序](./operator-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [如何︰ 呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)   
 [如何︰ 在 Visual Basic 中呼叫事件處理常式](./how-to-call-an-event-handler.md)
