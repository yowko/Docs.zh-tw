---
title: 使用字串名稱呼叫屬性或方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- passing operators [Visual Basic]
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls [Visual Basic], strings
- methods [Visual Basic], calling with string names
- calling methods [Visual Basic], string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
ms.openlocfilehash: e267c0c4d1d3e8f986348863d933c984f686b33b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842638"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>使用字串名稱呼叫屬性或方法 (Visual Basic)
在大部分情況下，您可以在設計階段探索的屬性和方法的物件和撰寫程式碼來處理它們。 不過，在某些情況下您可能不知道物件的屬性和方法事先，或者您可能只想讓使用者指定的屬性，或在執行階段執行方法的彈性。  
  
## <a name="callbyname-function"></a>CallByName 函式  
 比方說，假設用戶端應用程式所評估的使用者輸入傳遞至 COM 元件的運算子的運算式。 假設您要不斷地將新函式項目新增至需要新的運算子元件。 當您使用標準的物件存取技術時，您必須重新編譯，並重新發佈用戶端應用程式，才能將能夠使用新的運算子。 若要避免這個問題，您可以使用`CallByName`為字串，傳遞新的運算子，而不需要變更應用程式的函式。  
  
 `CallByName`函式可讓您使用在執行階段指定的屬性或方法的字串。 簽章`CallByName`函式看起來像這樣：  
  
 *結果* = `CallByName`(*物件*，*程序名稱*， *CallType*，*引數*（)）  
  
 第一個引數，*物件*，會使用您想要處理之物件的名稱。 *程序名稱*引數包含要叫用方法或屬性程序名稱的字串。 *CallType*引數的常數，表示要叫用的程序的類型： 一種方法 (`Microsoft.VisualBasic.CallType.Method`)，讀取的屬性 (`Microsoft.VisualBasic.CallType.Get`)，或將屬性設定 (`Microsoft.VisualBasic.CallType.Set`)。 *引數*引數，這是選擇性的採用陣列型別的`Object`，其中包含的程序的任何引數。  
  
 您可以使用`CallByName`類別中目前的方案中，但通常可用來存取 COM 物件或物件從[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件。  
  
 假設您將加入包含類別，名為組件的參考`MathClass`，其中包含新的函式，名為`SquareRoot`，如下列程式碼所示：  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 您的應用程式可以使用文字方塊控制項，以將呼叫哪一種方法的控制項和其引數。 比方說，如果`TextBox1`包含要評估的運算式並`TextBox2`是用來輸入函式的名稱，您可以使用下列程式碼來叫用`SquareRoot`函式中的運算式上`TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 如果您在中輸入"64 」 `TextBox1`，「 SquareRoot 」 中的`TextBox2`，然後呼叫`CallMath`程序、 數字的平方根`TextBox1`評估。 此範例中的程式碼會叫用`SquareRoot`函式 （其採用字串，包含評估為必要的引數的運算式），並傳回"8"中`TextBox1`（64 平方根）。 當然，如果使用者輸入無效的字串中`TextBox2`，如果字串包含名稱的屬性，而不是方法，或如果此方法會有其他必要的引數，就會發生執行階段錯誤。 您必須加入強固的錯誤處理程式碼，當您使用`CallByName`預期會發生這些或其他任何錯誤。  
  
> [!NOTE]
>  雖然`CallByName`函式可能會很有用，在某些情況下，您必須衡量其實用性，對效能的影響 — 使用`CallByName`叫用程序會稍微慢一點比晚期繫結呼叫。 如果您叫用會重複呼叫，例如在迴圈內的函式`CallByName`可能會造成嚴重影響效能。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [決定物件類型](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
