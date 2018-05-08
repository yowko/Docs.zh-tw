---
title: 如何：建立程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: da4cc299fbe35702990a62b5bf824e3ac71d5902
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-procedure-visual-basic"></a>如何：建立程序 (Visual Basic)
您將開始的宣告陳述式之間的程序 (`Sub`或`Function`) 和結束的宣告陳述式 (`End Sub`或`End Function`)。 所有程序的程式碼都位於這些陳述式之間。  
  
 程序不能包含另一個程序，因此其開始和結束的陳述式必須是其他程序之外。  
  
 如果您在不同的地方執行相同工作的程式碼，您可以撰寫一次做為程序工作，然後依照從不同的地方程式碼中呼叫它。  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>若要建立程序不會傳回值  
  
1.  任何其他程序，之外使用`Sub`陳述式，後面接著`End Sub`陳述式。  
  
2.  在`Sub`陳述式，請遵循`Sub`關鍵字的程序，則參數清單括號括住名稱。  
  
3.  放置程序的程式碼陳述式之間`Sub`和`End Sub`陳述式。  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>若要建立程序傳回值  
  
1.  任何其他程序，之外使用`Function`陳述式，後面接著`End Function`陳述式。  
  
2.  在`Function`陳述式，請遵循`Function`關鍵字的程序，則參數清單括號中，名稱，然後`As`子句指定的傳回值的資料類型。  
  
3.  放置程序的程式碼陳述式之間`Function`和`End Function`陳述式。  
  
4.  使用`Return`陳述式來將值傳回給呼叫程式碼。  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>連接新的程序與舊重複區塊的程式碼  
  
1.  請確定您在舊的程式碼可以存取它的其中一個位置中定義新的程序。  
  
2.  在舊而重複的程式碼區塊中，取代執行呼叫的單一陳述式的重複性工作的陳述式`Sub`或`Function`程序。  
  
3.  如果您的程序是`Function`傳回值，請確定您呼叫的陳述式執行的動作，以傳回的值，例如儲存在變數中，否則值將會遺失。  
  
## <a name="example"></a>範例  
 下列`Function`已知值的其他兩個邊直角三角形斜邊的最長邊，程序會計算。  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a>另請參閱

 [程序](./index.md)  
 [Sub 程序](./sub-procedures.md)  
 [函式程序](./function-procedures.md)  
 [屬性程序](./property-procedures.md)  
 [運算子程序](./operator-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [遞迴程序](./recursive-procedures.md)  
 [程序多載化](./procedure-overloading.md)  
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [物件導向程式設計 (Visual Basic)](../../concepts/object-oriented-programming.md)  
