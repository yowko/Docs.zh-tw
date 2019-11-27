---
title: 子程序
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
ms.openlocfilehash: 7848dc07d6462622685cdbea92202585f4d5d2c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352529"
---
# <a name="sub-procedures-visual-basic"></a>Sub 程序 (Visual Basic)
`Sub` 程式是以 `Sub` 和 `End Sub` 語句括住的一系列 Visual Basic 語句。 `Sub` 程式會執行工作，然後將控制權傳回給呼叫程式碼，但不會將值傳回給呼叫程式碼。  
  
 每次呼叫程式時，都會執行其語句，從 `Sub` 語句後面的第一個可執行語句開始，並以遇到的第一個 `End Sub`、`Exit Sub`或 `Return` 語句為結尾。  
  
 您可以在模組、類別和結構中定義 `Sub` 程式。 根據預設，它是 `Public`的，這表示您可以從應用程式的任何位置呼叫它，以存取您在其中定義它的模組、類別或結構。 「*方法*」一詞描述從其定義模組、類別或結構外部存取的 `Sub` 或 `Function` 程式。 如需詳細資訊，請參閱[程序](./index.md)。  
  
 `Sub` 程式可以接受引數，例如常數、變數或運算式，由呼叫程式碼傳遞給它。  
  
## <a name="declaration-syntax"></a>宣告語法  
 宣告 `Sub` 程式的語法如下：  
  
 `] Sub` *`[`* 修飾*詞*`[(` *p t*的修飾詞 `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` 可以指定有關多載、覆寫、共用和遮蔽的存取層級和資訊。 如需詳細資訊，請參閱[Sub 語句](../../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
## <a name="parameter-declaration"></a>參數宣告  
 您可以宣告每個程式參數，類似于宣告變數的方式，指定參數名稱和資料類型。 您也可以指定傳遞機制，以及參數是否為選擇性或參數陣列。  
  
 參數清單中每個參數的語法如下：  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`*parametername*`As`*datatype*  
  
 如果參數是選擇性的，您也必須提供預設值做為其宣告的一部分。 指定預設值的語法如下：  
  
 `Optional [ByVal | ByRef]`*parametername*`As`*datatype*`=`*defaultvalue*  
  
### <a name="parameters-as-local-variables"></a>參數作為區域變數  
 當控制項傳遞至程式時，會將每個參數視為本機變數。 這表示它的存留期與程式相同，而且其範圍為整個程式。  
  
## <a name="calling-syntax"></a>呼叫語法  
 您可以使用獨立的呼叫語句來明確叫用 `Sub` 程式。 您不能在運算式中使用它的名稱來呼叫它。 您必須提供所有非選擇性引數的值，而且必須將引數清單括在括弧中。 如果未提供任何引數，您可以選擇性地省略括弧。 `Call` 關鍵字是選擇性的，但不建議使用。  
  
 呼叫 `Sub` 程式的語法如下所示：  
  
 `[Call]`*的*`[(` *argumentlist* `)]`  
  
 您可以從定義它的類別外部呼叫 `Sub` 方法。 首先，您必須使用 `New` 關鍵字來建立類別的實例，或呼叫方法來傳回類別的實例。 如需詳細資訊，請參閱[New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)。 然後，您可以使用下列語法，在實例物件上呼叫 `Sub` 方法：  
  
 *物件*。*方法名稱*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例  
 下列 `Sub` 程式會告訴電腦操作員應用程式即將執行哪一項工作，同時也會顯示時間戳記。 應用程式只會從不同位置呼叫 `tellOperator`，而不是在每個工作開始時複製此程式碼。 每個呼叫都會在 `task` 引數中傳遞一個字串，以識別要啟動的工作。  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 下列範例顯示 `tellOperator`的一般呼叫。  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [函式程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [如何：在 Visual Basic 中呼叫事件處理常式](./how-to-call-an-event-handler.md)
