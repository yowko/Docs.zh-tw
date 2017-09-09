---
title: "throw (C# 參考) | Microsoft Docs"
ms.date: 2015-03-02
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 095a86f5ab2ce50f5931643161a44b5759583e4e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="throw-c-reference"></a>throw (C# 參考)
在程式執行期間發出出現例外狀況的訊號。  
  
## <a name="remarks"></a>備註

`throw` 的語法為：

```csharp
throw [e]
```
其中 `e` 是衍生自 <xref:System.Exception?displayProperty=fullName> 的類別執行個體。 如果傳遞給 `GetNumber` 方法的引數未對應至內部陣列的有效索引，則下列範例會使用 `throw` 陳述式來擲回 @System.IndexOutOfRangeException。

[!code-cs[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

方法呼叫端接著會使用 `try-catch` 或 `try-catch-finally` 區塊來處理所擲回的例外狀況。 下列範例會處理 `GetNumber` 方法所擲回的例外狀況。

[!code-cs[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>重新擲回例外狀況

`throw` 也可以用於 `catch` 區塊，以重新擲回 `catch` 區塊中所處理的例外狀況。  在此情況下，`throw` 陳述式不接受例外狀況運算元。 這最適用於當方法將來自呼叫端的引數傳遞給某個其他程式庫方法，且程式庫方法擲回必須傳遞給呼叫端的例外狀況時。 例如，下列範例會重新擲回 @System.NullReferenceException，而這是在嘗試擷取未初始化字串的第一個字元時擲回。 

[!code-cs[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> 您也可以使用 `catch` 區塊中的 `throw e` 語法，來具現化傳遞給呼叫端的新例外狀況。 在此情況下，不會保留原始例外狀況的堆疊追蹤 (可從 @System.Exception.Stacktrace 屬性取得)。
 
## <a name="the-throw-expression"></a>`throw` 運算式

從 C# 7 開始，`throw` 可以用作運算式和陳述式。 這可在先前不支援的內容中擲回例外狀況。 它們包括：

- [條件運算子](../operators/conditional-operator.md)。 如果將空字串陣列傳遞給方法，則下列範例會使用 `throw` 運算式來擲回 @System.ArgumentException。 在 C# 7 之前，這個邏輯必須出現在 `if`/`else` 陳述式中。

   [!code-cs[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [Null 聯合運算子](../operators/null-conditional-operator.md)。 在下列範例中，如果指派給 `Name` 屬性的字串是 `null`，則搭配使用 `throw` 運算式與 Null 聯合運算子會擲回例外狀況。
 
   [!code-cs[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- 運算式主體 [ambda](../../lambda-expressions.md) 或方法。 下列範例說明因不支援轉換為 @System.DateTime 值而擲回 @System.InvalidCastException 的運算式主體方法。
 
   [!code-cs[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [C++ 中的 try、catch 和 throw 陳述式](../../../csharp/language-reference/keywords/try-catch.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [例外狀況處理陳述式](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [如何：明確擲回例外狀況](https://msdn.microsoft.com/library/xhcbs8fz)
