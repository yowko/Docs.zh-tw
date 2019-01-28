---
title: out 參數修飾詞 - C# 參考
ms.custom: seodec18
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 8aebe0492728f3ef87256f5d8c4859220d9106cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660004"
---
# <a name="out-parameter-modifier-c-reference"></a>out 參數修飾詞 (C# 參考)
`out` 關鍵字會導致引數由參考傳遞。 它類似於 [ref](ref.md) 關鍵字，只是 `ref` 需要在傳遞之前，先初始化變數。 其類似於 [in](in-parameter-modifier.md) 關鍵字，但不同處在於 `in` 不允許呼叫的方法來修改引數的值。 若要使用 `out` 參數，方法定義和呼叫方法都必須明確地使用 `out` 關鍵字。 例如：  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> `out` 關鍵字也可以和泛型型別參數一起使用，指定型別參數為 Covariant。 如需在此內容中使用 `out` 關鍵字的詳細資訊，請參閱 [out (泛型修飾詞)](out-generic-modifier.md)。
  
當作 `out` 引數傳遞的變數不必先初始化，再於方法呼叫中傳遞。 不過，需要先指派值給被呼叫的方法，方法才能傳回。  
  
雖然 `in`、`ref` 和 `out` 關鍵字會導致不同的執行階段行為，但在編譯期間，不會將其視為方法簽章的一部分。 因此，如果唯一的差別是一種方法採用 `ref` 或 `in` 引數，而另一種方法採用 `out` 引數，則無法對方法進行多載。 例如，將不會編譯下列程式碼：  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
但如果有一種方法採用 `ref`、`in` 或 `out` 引數，而另一種方法完全沒有這些修飾詞，則類似於：  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

編譯器會選擇最佳的多載，方法是比對呼叫位置的參數修飾詞，與方法呼叫中所使用的參數修飾詞。
 
屬性不是變數，因此無法做為 `out` 參數傳遞。
  
您不可為下列幾種方法使用 `in`、`ref` 和 `out` 關鍵字：  
  
-   使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。  
  
-   迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。  

## <a name="declaring-out-arguments"></a>宣告 `out` 引數   

 當您想要方法傳回多個值時，宣告使用 `out` 引數的方法很有用。 下列範例使用 `out`，在單一方法呼叫中，傳回三個變數。 請注意，第三個引數指派為 null。 這可讓方法能選擇性地傳回值。  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 [Try 模式](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods)牽涉到傳回 `bool` 指出作業成功或失敗，並傳回作業在 `out` 引數中產生的值。 有數種剖析方法 (例如 [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) 方法) 使用此模式。
   
## <a name="calling-a-method-with-an-out-argument"></a>呼叫有 `out` 引數的方法

在 C# 6 和舊版中，您必須先在其他陳述式中宣告變數，再將它傳遞為 `out` 引數。 下列範例宣告名為 `number` 的變數，然後將它傳遞到 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法，此方法嘗試將字串轉換為數字。

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

從 C# 7.0 開始，您可以在方法呼叫的引數清單中宣告 `out` 變數，而非在其他的變數中宣告。 這會產生更精簡、更容易閱讀的程式碼，也可避免不小心在方法呼叫前先將值指派給變數。 下列範例與上一個範例類似，但下列範例會在對 [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) 方法的呼叫中定義 `number` 變數。

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
在上例中，`number` 變數是如同 `int` 的強型別。 您也可以宣告隱含型別的區域變數，如下例所示。

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>C# 語言規格  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)
- [方法參數](../../../csharp/language-reference/keywords/method-parameters.md)
