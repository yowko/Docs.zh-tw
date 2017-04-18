---
title: "呼叫屬性或方法使用字串名稱 (Visual Basic) |Microsoft 文件"
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
- passing operators
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls, strings
- methods [Visual Basic], calling with string names
- calling methods, string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: 17
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
ms.openlocfilehash: 87af2816ba42e2901c53bec5e9c19f34c676ed5c
ms.lasthandoff: 03/13/2017

---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>使用字串名稱呼叫屬性或方法 (Visual Basic)
在大部分情況下，可以在設計階段探索的屬性和方法的物件，並撰寫程式碼來處理它們。 不過，在某些情況下您可能不知道物件的屬性和方法的相關事先，或者您可能只想讓使用者指定的屬性，或在執行階段執行方法的彈性。  
  
## <a name="callbyname-function"></a>CallByName 函式  
 例如，假設用戶端應用程式評估使用者輸入傳遞至 COM 元件的運算子的運算式。 假設您經常要將新函式需要新的運算子的元件。 當您使用標準的物件存取方法時，您必須重新編譯並重新發佈用戶端應用程式，才能夠使用新的運算子。 若要避免這個問題，您可以使用`CallByName`而不需要變更應用程式將新運算子傳遞為字串，函式。  
  
 `CallByName`函式可讓您指定的屬性或方法，在執行階段使用的字串。 簽章`CallByName`函式看起來像這樣︰  
  
 *Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())  
  
 第一個引數，*物件*，會想要作用的物件名稱。 *m e*引數會接受字串，包含要叫用方法或屬性程序的名稱。 *CallType*引數為常數，表示叫用的程序的類型︰ 一種方法 (`Microsoft.VisualBasic.CallType.Method`)，讀取屬性 (`Microsoft.VisualBasic.CallType.Get`)，或將屬性設定 (`Microsoft.VisualBasic.CallType.Set`)。 *引數*引數是選擇性的會採用型別的陣列`Object`，其中包含的程序的任何引數。  
  
 您可以使用`CallByName`中目前的方案，但它的類別最常用來存取 COM 物件或物件從[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件。  
  
 假設您將加入包含名為的類別的組件的參考`MathClass`，其具有名為的新函數`SquareRoot`，如下列程式碼所示︰  
  
 [!code-vb[VbVbalrOOP #&53;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 您的應用程式可以使用文字方塊控制項，以控制將要呼叫哪一種方法和其引數。 例如，如果`TextBox1`其中包含要評估的運算式和`TextBox2`是用來輸入函式的名稱，您可以使用下列程式碼來叫用`SquareRoot`函式之運算式上的`TextBox1`:  
  
 [!code-vb[VbVbalrOOP #&54;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 如果您在輸入"64" `TextBox1`，「 SquareRoot 」 在`TextBox2`，然後呼叫`CallMath`程序、 數字的平方根`TextBox1`評估。 此範例中的程式碼會叫用`SquareRoot`函式 （這是一個字串，包含評估為必要的引數的運算式），並傳回"8"中`TextBox1`（64 平方根）。 當然，如果使用者輸入無效的字串中`TextBox2`，如果字串包含而不是一種方法，屬性的名稱，或如果方法具有其他必要的引數，就會發生執行階段錯誤。 您必須加入強固的錯誤處理程式碼，當您使用`CallByName`預期會發生這些或其他錯誤。  
  
> [!NOTE]
>  雖然`CallByName`函式可能會很有用，在某些情況下，您必須衡量效能影響針對其可用性 — 使用`CallByName`叫用程序會稍微慢一點比晚期繫結呼叫。 如果您叫用的函式會重複呼叫，例如在迴圈內`CallByName`可能會嚴重影響效能。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A></xref:Microsoft.VisualBasic.Interaction.CallByName%2A>   
 [決定物件類型](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
