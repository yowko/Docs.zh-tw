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
ms.openlocfilehash: cb584f0dfbd905ca071f9a86b1eab231f3017538
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345214"
---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a>使用字串名稱呼叫屬性或方法 (Visual Basic)
在大部分的情況下，您可以在設計階段探索物件的屬性和方法，並撰寫程式碼來處理它們。 不過，在某些情況下，您可能不會事先知道物件的屬性和方法，或者您可能只想要讓使用者在執行時間指定屬性或執行方法的彈性。  
  
## <a name="callbyname-function"></a>CallByName 函式  
 例如，假設用戶端應用程式會將運算子傳遞至 COM 元件，以評估使用者所輸入的運算式。 假設您持續將新的函式加入至需要新運算子的元件。 當您使用標準物件存取技術時，必須先重新編譯和轉散發用戶端應用程式，才能使用新的運算子。 若要避免這種情況，您可以使用 `CallByName` 函式，以字串形式傳遞新的運算子，而不需要變更應用程式。  
  
 `CallByName` 函數可讓您在執行時間使用字串來指定屬性或方法。 `CallByName` 函數的簽章看起來像這樣：  
  
 *Result* = `CallByName`（*Object*、*程式名稱*、 *CallType*、 *Arguments*（））  
  
 第一個引數（ *Object*）會採用您想要採取動作的物件名稱。 *程式名稱*引數會採用包含要叫用之方法或屬性程式名稱的字串。 *CallType*引數會採用常數，代表要叫用的程式類型：方法（`Microsoft.VisualBasic.CallType.Method`）、屬性讀取（`Microsoft.VisualBasic.CallType.Get`）或屬性集（`Microsoft.VisualBasic.CallType.Set`）。 *引數*引數是選擇性的，它會採用類型 `Object` 的陣列，其中包含程式的任何引數。  
  
 您可以在目前的方案中使用 `CallByName` 搭配類別，但最常用來從 .NET Framework 元件存取 COM 物件或物件。  
  
 假設您新增的元件參考包含名為 `MathClass`的類別，其中具有名為 `SquareRoot`的新函式，如下列程式碼所示：  
  
 [!code-vb[VbVbalrOOP#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#53)]  
  
 您的應用程式可以使用文字方塊控制項來控制將呼叫的方法及其引數。 例如，如果 `TextBox1` 包含要評估的運算式，而 `TextBox2` 用來輸入函數的名稱，您可以使用下列程式碼，在 `TextBox1`的運算式上叫用 `SquareRoot` 函數：  
  
 [!code-vb[VbVbalrOOP#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#54)]  
  
 如果您在 `TextBox1`中輸入 "64"，`TextBox2`中的 "SquareRoot"，然後呼叫 `CallMath` 程式，則會評估 `TextBox1` 中數位的平方根。 範例中的程式碼會叫用 `SquareRoot` 函式（採用包含要評估為必要引數之運算式的字串），並在 `TextBox1` （64的平方根）中傳回 "8"。 當然，如果使用者在 `TextBox2`中輸入不正確字串，如果字串包含屬性（而不是方法）的名稱，或如果方法有額外的必要引數，就會發生執行階段錯誤。 當您使用 `CallByName` 來預期這些或任何其他錯誤時，您必須加入健全的錯誤處理常式代碼。  
  
> [!NOTE]
> 雖然在某些情況下，`CallByName` 函式可能很有用，但您必須對效能影響權衡其實用性，使用 `CallByName` 叫用程式比晚期繫結呼叫稍微慢一點。 如果您叫用重複呼叫的函式，例如在迴圈內，`CallByName` 可能會對效能造成嚴重的影響。  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>
- [決定物件類型](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)
