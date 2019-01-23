---
title: Sub 程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: f558c61d2e81471e167e97816ff47bc4465c5f51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638115"
---
# <a name="sub-procedures-visual-basic"></a>Sub 程序 (Visual Basic)
A`Sub`程序是一系列的 Visual Basic 陳述式加上`Sub`和`End Sub`陳述式。 `Sub`程序執行的工作，然後將控制權傳回呼叫的程式碼，但它不會傳回呼叫程式碼的值。  
  
 每次呼叫此程序時，其會執行陳述式，從開始之後的第一個可執行陳述式`Sub`陳述式，並與第一個結束`End Sub`， `Exit Sub`，或`Return`陳述式時發生。  
  
 您可以定義`Sub`模組、 類別和結構中的程序。 根據預設，它是`Public`，這表示您可以呼叫它從任何地方存取模組、 類別或結構定義它的應用程式中。 詞彙*方法*，說明`Sub`或`Function`從其定義外部存取的程序模組、 類別或結構。 如需詳細資訊，請參閱[程序](./index.md)。  
  
 A`Sub`程序可以取得引數，例如常數、 變數或運算式，這會傳遞給它所呼叫的程式碼。  
  
## <a name="declaration-syntax"></a>宣告語法  
 宣告的語法`Sub`程序如下所示：  
  
 `[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers`可以指定存取層級和多載、 覆寫，將分享，與遮蔽的相關資訊。 如需詳細資訊，請參閱 < [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
## <a name="parameter-declaration"></a>參數宣告  
 您宣告類似於如何宣告變數，指定參數名稱和資料類型的每個程序參數。 您也可以指定傳遞機制，以及是否為選擇性參數或參數陣列。  
  
 參數清單中的每個參數的語法如下所示：  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*  
  
 如果參數是選擇性的您還必須提供預設值做為其宣告的一部分。 指定預設值的語法如下所示：  
  
 `Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*  
  
### <a name="parameters-as-local-variables"></a>本機變數與參數  
 當控制權會傳遞至程序時，當做本機變數來處理每個參數。 這表示，其存留期與相同的程序，其範圍是整個程序。  
  
## <a name="calling-syntax"></a>呼叫語法  
 您可以叫用`Sub`明確地使用獨立的呼叫陳述式的程序。 您無法在運算式中使用它的名稱來呼叫它。 您必須提供值不是選擇性的所有引數，您必須將引數清單括在括號中。 如果已不提供任何引數，您可以選擇性地省略括號。 使用`Call`關鍵字是選擇性的但不是建議使用。  
  
 呼叫語法`Sub`程序如下所示：  
  
 `[Call]`  *subname* `[(` *argumentlist* `)]`  
  
 您可以呼叫`Sub`方法外定義它的類別。 首先，您必須使用`New`關鍵字來建立類別的執行個體，或呼叫方法會傳回類別的執行個體。 如需詳細資訊，請參閱 < [New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)。 然後，您可以使用下列語法來呼叫`Sub`執行個體物件上的方法：  
  
 *物件*。*methodname*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例  
 下列`Sub`程序會告訴電腦運算子的應用程式即將執行的工作，也會顯示時間戳記。 而不必重複此程式碼開頭的每項工作，應用程式只會呼叫`tellOperator`從各種不同的位置。 每個呼叫會傳遞的字串`task`識別啟動之工作的引數。  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 下列範例示範的典型呼叫`tellOperator`。  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>另請參閱
- [程序](./index.md)
- [函式程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [如何：在 Visual Basic 中呼叫事件處理常式](./how-to-call-an-event-handler.md)
