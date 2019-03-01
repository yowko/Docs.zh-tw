---
title: HOW TO：建立程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 0f3b0a793b2751b0ec9bb2b7cd6fedc12ae19e18
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970801"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>HOW TO：建立程序 (Visual Basic)
您將開始的宣告陳述式之間的程序 (`Sub`或是`Function`) 和結束的宣告陳述式 (`End Sub`或`End Function`)。 這些陳述式之間，位於所有程序的程式碼。  
  
 程序不能包含另一個程序，因此其開始和結束的陳述式必須是任何其他程序之外。  
  
 如果您有不同的地方執行相同工作的程式碼時，您可以撰寫一次做為程序的工作，然後依照從不同的地方在程式碼中呼叫它。  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>若要建立的程序，不會傳回值  
  
1.  任何其他程序外, 使用`Sub`陳述式，後面接著`End Sub`陳述式。  
  
2.  在 `Sub`陳述式中，遵循`Sub`關鍵字的程序中，則參數清單括號括住名稱。  
  
3.  放置程序的程式碼陳述式之間`Sub`和`End Sub`陳述式。  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>若要建立傳回值的程序  
  
1.  任何其他程序外, 使用`Function`陳述式，後面接著`End Function`陳述式。  
  
2.  在`Function`陳述式，請依照下列`Function`關鍵字與程序中，則參數清單括號中的名稱，然後`As`子句指定的傳回值的資料類型。  
  
3.  放置程序的程式碼陳述式之間`Function`和`End Function`陳述式。  
  
4.  使用`Return`陳述式來將值傳回給呼叫程式碼。  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>連接新的程序利用舊的重複性的區塊的程式碼  
  
1.  請確定您在舊的程式碼，能夠存取它的地方定義新的程序。  
  
2.  在舊的重複性的程式碼區塊中，取代執行重複性工作，呼叫以單一陳述式的陳述式`Sub`或`Function`程序。  
  
3.  如果您的程序是`Function`所傳回的值，請確保您呼叫的陳述式會執行的動作傳回的值，例如將它儲存在變數中，否則此值將會遺失。  
  
## <a name="example"></a>範例  
 下列`Function`程序會計算已知值的其他兩個邊直角三角形斜邊的最長的側邊。  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [函式程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [遞迴程序](./recursive-procedures.md)
- [程序多載化](./procedure-overloading.md)
- [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [物件導向程式設計 (Visual Basic)](../../concepts/object-oriented-programming.md)
