---
title: "in 參數修飾詞 (C# 參考)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 035aac3e6b902f607e533b709713eb1d07c9774a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="in-parameter-modifier-c-reference"></a>in 參數修飾詞 (C# 參考)

`in` 關鍵字會導致引數由參考傳遞。 這和 [ref](ref.md) 或 [out](out-parameter-modifier.md) 關鍵字類似同，但 `in` 引數無法由呼叫的方法加以修改，而是可以修改 `ref` 引數。`out` 引數必須由呼叫端修改，而這些修改內容可於呼叫內容中查看。

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

上述範例示範了 `in` 修飾詞在呼叫位置並非必要， 而只有在宣告方法時才會需要該項目。

> [!NOTE] 
> `in` 關鍵字也可與泛型型別搭配使用，來指定類型參數是否為 Contravariant、屬於 `foreach` 陳述式的一部分，或是屬於 LINQ 查詢中的 `join` 子句。 如需如何在這些內容中使用 `in` 關鍵字的詳細資訊，請參閱 [in](in.md)，其提供所有這些使用的連結。
  
 傳遞為 `in` 引數的變數，必須先經過初始化，才能在方法呼叫中傳遞。 但是，呼叫方法可能不會指派值或修改引數。  
  
 雖然 `in`、`ref` 和 `out` 關鍵字會導致不同的執行階段行為，但在編譯期間，不會將其視為方法簽章的一部分。 因此，如果唯一的差別是一種方法採用 `ref` 或 `in` 引數，而另一種方法採用 `out` 引數，則無法對方法進行多載。 例如，將不會編譯下列程式碼：  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
若有 `in`，可以進行多載，但會產生編譯器警告：  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

因為呼叫方法並不會修改屬性與常數的值，所以這兩者皆會以 `in` 參數方式傳遞。
  
您不可為下列幾種方法使用 `in`、`ref` 和 `out` 關鍵字：  
  
- 使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。  
  
- 迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。  

一般來說，您宣告 `in` 引數，以避免出現依值傳遞引數時所需進行的複製作業。 當引數為結構或結構的陣列時，此方法相當實用。

## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [方法參數](../../../csharp/language-reference/keywords/method-parameters.md)
