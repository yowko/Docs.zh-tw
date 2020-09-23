---
title: 使用字串名稱呼叫屬性或方法
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
ms.openlocfilehash: 9f28548c27545d94dde38cef3e9c56f98a69b259
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086084"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>使用字串名稱呼叫屬性或方法 (Visual Basic)

在大部分的情況下，您可以在設計階段探索物件的屬性和方法，並撰寫程式碼來處理它們。 不過，在某些情況下，您可能不會事先知道物件的屬性和方法，或者您可能只想要讓使用者在執行時間指定屬性或執行方法的彈性。  
  
## <a name="callbyname-function"></a>CallByName 函式  

 例如，假設用戶端應用程式會藉由將運算子傳遞給 COM 元件，來評估使用者所輸入的運算式。 假設您不斷地將新的函式加入需要新操作員的元件中。 當您使用標準物件存取技術時，您必須先重新編譯和轉散發用戶端應用程式，才能使用新的操作員。 若要避免這種情況，您可以使用函式 `CallByName` 以字串的形式傳遞新的運算子，而不需要變更應用程式。  
  
 `CallByName`函數可讓您在執行時間使用字串來指定屬性或方法。 函數的簽 `CallByName` 章看起來像這樣：  
  
 *Result*  =  結果 `CallByName` (*物件*、*程式名稱*、 *CallType*、*引數* ( # A2 # A3  
  
 第一個引數（ *Object*）接受您想要採取動作的物件名稱。 *程式名稱*引數會採用包含要叫用之方法或屬性程式名稱的字串。 *CallType*引數會使用常數來表示要叫用的程式類型：方法 (`Microsoft.VisualBasic.CallType.Method`) 、屬性讀取 (`Microsoft.VisualBasic.CallType.Get`) 或屬性集 (`Microsoft.VisualBasic.CallType.Set`) 。 *引數*引數是選擇性的，會採用類型的陣列， `Object` 其中包含程式的任何引數。  
  
 您可以使用 `CallByName` 與目前方案中的類別，但最常用來從 .NET Framework 元件存取 COM 物件或物件。  
  
 假設您加入的元件參考包含名為的類別 `MathClass` ，該類別具有名為的新函式 `SquareRoot` ，如下列程式碼所示：  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 您的應用程式可以使用文字方塊控制項來控制所要呼叫的方法及其引數。 例如，如果 `TextBox1` 包含要評估的運算式，而且 `TextBox2` 用來輸入函式的名稱，您可以使用下列程式碼， `SquareRoot` 在中的運算式上叫用函數 `TextBox1` ：  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 如果您在中輸入 "64" `TextBox1` ，並在中輸入 "SquareRoot"， `TextBox2` 然後呼叫 `CallMath` `TextBox1` 程式，則會評估中數位的平方根。 範例中的程式碼會叫用函式 `SquareRoot` (它會採用包含要評估為必要引數之運算式的字串) 並在 `TextBox1` 64) 的平方根 (中傳回 "8"。 當然，如果使用者在中輸入不正確字串 `TextBox2` ，則如果字串包含屬性的名稱而非方法，或如果方法有額外的必要引數，則會發生執行階段錯誤。 當您使用 `CallByName` 來預測這些或任何其他錯誤時，必須加入健全的錯誤處理常式代碼。  
  
> [!NOTE]
> 雖然函式 `CallByName` 在某些情況下可能會很有用，但您必須針對效能含意來權衡其實用性（使用 `CallByName` 來叫用程式的速度會比晚期繫結呼叫稍微慢一點）。 如果您叫用重複呼叫的函式（例如在迴圈內部）， `CallByName` 可能會對效能產生嚴重的影響。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [決定物件類型](determining-object-type.md)
