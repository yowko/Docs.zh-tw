---
title: "Calling a Property or Method Using a String Name (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "passing operators"
  - "strings [Visual Basic], passing new operators as"
  - "objects [Visual Basic], setting properties"
  - "setting properties, object properties at run time"
  - "method calls, strings"
  - "methods [Visual Basic], calling with string names"
  - "calling methods, string names"
  - "properties [Visual Basic], setting at run time"
  - "CallByName function"
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Calling a Property or Method Using a String Name (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

在大多數的情況下，您可以在設計階段發現物件的屬性及方法，然後寫入程式碼來處理它們。  然而在某些情況下，您可能無法預知物件的屬性及方法，或是您可能只是希望讓使用者能有彈性的在執行階段指定屬性或執行方法。  
  
## CallByName 函式  
 仔細想想以下這種情況，用戶端應用程式所評估的運算式是由使用者傳遞運算子至 COM 元件的方式來輸入。  假設您經常要將新函式加入需要新運算子的元件。  使用標準的物件存取方法時，您必須先重新編譯並重新散發用戶端應用程式，才能夠使用新的運算子。  為避免以上情況，您可以使用 `CallByName` 函式以字串的方式傳遞新運算子，而不必變更應用程式。  
  
 `CallByName` 函式可讓您在執行階段使用字串來指定屬性或方法。  `CallByName` 函式的簽章看起來如下：  
  
 *Result* \= `CallByName`\(*Object*, *ProcedureName*, *CallType*, *Arguments*\(\)\)  
  
 第一個引數 *Object* 放入您要執行動作的物件名稱。  *ProcedureName* 引數使用的字串包含要叫用的方法或屬性程序名稱。  *CallType* 引數使用的常數表示要叫用的程序型別：方法 \(`Microsoft.VisualBasic.CallType.Method`\)、屬性讀取 \(`Microsoft.VisualBasic.CallType.Get`\) 或屬性設定 \(`Microsoft.VisualBasic.CallType.Set`\)。  *Arguments* 是選擇性引數，所使用的 `Object` 型別陣列包含程序的任何引數。  
  
 您可以將 `CallByName` 使用在目前方案中的類別，但它最常用來存取 COM 物件或來自 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 組件的物件。  
  
 假設您所加入的組件參考包含稱為 `MathClass` 的類別，而此類別又有稱為 `SquareRoot` 的新函式，如以下程式碼所示：  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#53)]  
  
 您的應用程式可使用文字方塊控制項，以控制將要呼叫哪個方法及其引數。  例如，如果 `TextBox1` 包含要評估的運算式，而 `TextBox2` 用於輸入函式的名稱，則可使用以下程式碼來叫用 `TextBox1` 中運算式的 `SquareRoot` 函式：  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#54)]  
  
 如果在 `TextBox1` 中輸入 "64"，在 `TextBox2` 中輸入 "SquareRoot"，然後呼叫 `CallMath` 程序，便會求出 `TextBox1` 中數字的平方根。  範例中的程式碼會叫用 `SquareRoot` 函式 \(使用的字串包含做為必要引數以求其值的運算式\)，並在 `TextBox1` 中傳回 "8" \(64 的平方根\)。  當然，如果使用者在 `TextBox2` 輸入無效字串，字串包含屬性的名稱而非方法的名稱，或是如果方法具有其他必要引數，則將會發生執行階段錯誤。  在預期會發生這些或任何其他錯誤的情況下，使用 `CallByName` 時必須加入穩固的錯誤處理程式碼。  
  
> [!NOTE]
>  雖然 `CallByName` 函式在某些情況下很有用，但您還是必須考量其使用性與效能影響；使用 `CallByName` 來叫用程序會比晚期繫結呼叫來得稍慢。  如果您叫用重複呼叫的函式 \(例如在迴圈內的函式\)，則 `CallByName` 會嚴重拖慢效能。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>   
 [Determining Object Type](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)