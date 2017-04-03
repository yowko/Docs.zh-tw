---
title: "when (C# 參考) | Microsoft Docs"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- when_CSharpKeyword
- when
dev_langs:
- CSharp
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f6218eed8afa7d71429b72be86ab7cc426029e92
ms.lasthandoff: 03/13/2017

---
 # <a name="when-c-reference"></a>when (C# 參考)

您可以使用 `when` 內容關鍵字，在兩個內容中指定篩選條件︰

- 在 [try/catch](try-catch.md) 或 [try/catch/finally](try-catch-finally.md) 區塊的 `catch` 陳述式中。
- 在 [switch](switch.md) 陳述式的 `case` 標籤中。

## <a name="when-in-a-catch-statement"></a>`catch` 陳述式中的 `when`

從 C# 6 開始，`When` 可以用於 `catch` 陳述式中，來指定必須符合才能執行特定例外狀況的處理常式的條件。 它的語法為：

```csharp
catch ExceptionType [e] when (expr)
```
其中，*expr* 是可評估為布林值的運算式。 如果它傳回 `true`，則會執行例外狀況處理常式；如果 `false` 則否。 

下列範例使用 `when` 關鍵字，根據例外狀況訊息的文字，有條件地執行 @System.Net.HttpRequestException 的處理常式。

 [!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a>`switch` 陳述式中的 `when`

從 7 開始，`case` 標籤不再需要互斥，而且 `case` 標籤在 `switch` 陳述式中的出現順序可以判斷要執行的 switch 區塊。 `when` 關鍵字可以用來指定篩選條件，使其相關聯的 case 標籤只有在篩選條件也是為 true 時才為 true。 它的語法為：

```csharp
case (expr) where (when-condition):
```
其中，*expr* 是與比對運算式進行比較的常數模式或類型模式，而 *when-condition* 是任何布林運算式。 

下列範例使用 `when` 關鍵字來測試是否有具有零區域的 `Shape` 物件，以及測試是否有具有大於零的區域的各種 `Shape` 物件。 

 [!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a>請參閱 
  [switch 陳述式](switch.md)  
  [try/catch 陳述式](try-catch.md)  
  [try/catch/finally 陳述式](try-catch-finally.md) 


