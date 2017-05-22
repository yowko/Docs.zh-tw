---
title: "out 參數修飾詞 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: 9
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: a2f2e9b9239836b051820bda66523822e95cdf52
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="out-parameter-modifier-c-reference"></a>out 參數修飾詞 (C# 參考)
`out` 關鍵字會導致引數由參考傳遞。 它類似於 [ref](../../../csharp/language-reference/keywords/ref.md) 關鍵字，只是 `ref` 需要在傳遞之前，先初始化變數。 若要使用 `out` 參數，方法定義和呼叫方法都必須明確地使用 `out` 關鍵字。 例如:   
  
 [!code-cs[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> `out` 關鍵字也可以和泛型型別參數一起使用，指定型別參數為 Covariant。 如需在此內容中使用 `out` 關鍵字的詳細資訊，請參閱 [out (泛型修飾詞)](../../../csharp/language-reference/keywords/out-generic-modifier.md)。
  
 當作 `out` 引數傳遞的變數不必先初始化，再於方法呼叫中傳遞。 不過，需要先指派值給被呼叫的方法，方法才能傳回。  
  
 雖然 `ref` 和 `out` 關鍵字會導致不同的執行階段行為，但在編譯階段，不會將其視為方法簽章的一部分。 因此，如果唯一的差別是一種方法採用 `ref` 引數，而另一種方法採用 `out` 引數，則不能多載方法。 例如，將不會編譯下列程式碼：  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
不過，如果一種方法採用 `ref` 或 `out` 引數，而另一種方法都不採用，則可以完成多載，如下所示：  
  
 [!code-cs[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 屬性不是變數，因此無法做為 `out` 參數傳遞。  
  
 如需傳遞陣列的資訊，請參閱[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。  
  
 您不能將 `ref` 和 `out` 關鍵字用於下列幾種方法：  
  
-   使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。  
  
-   迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。  

## <a name="declaring-out-arguments"></a>宣告 `out` 引數   

 當您想要方法傳回多個值時，宣告使用 `out` 引數的方法很有用。 下列範例使用 `out`，在單一方法呼叫中，傳回三個變數。 請注意，第三個引數指派為 null。 這可讓方法能選擇性地傳回值。  
  
 [!code-cs[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 [Try 模式](https://docs.microsoft.com/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) 牽涉到傳回 `bool` 指出作業成功或失敗，並傳回作業在 `out` 引數中產生的值。 有許多剖析方法使用此模式，例如 @System.DateTime.TryParse(System.String,@System.DateTime) 方法。
   
## <a name="calling-a-method-with-an-out-argument"></a>呼叫有 `out` 引數的方法

在 C# 6 和舊版中，您必須先在其他陳述式中宣告變數，再將它傳遞為 `out` 引數。 下例先宣告名為 `number` 的變數，再傳遞至 [Int32.TryParse](xref:System.Int32.TryParse(System.String,@System.Int32) 方法，其嘗試將字串轉換為數字。

 [!code-cs[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

從 C# 7 開始，您可以在方法呼叫的引數清單中宣告 `out` 變數，而非在其他的變數中宣告。 這會產生更精簡、更容易閱讀的程式碼，也可避免不小心在方法呼叫前先將值指派給變數。 下例類似上例，不同之處在於它會在 [Int32.TryParse](xref:System.Int32.TryParse(System.String,@System.Int32) 方法呼叫中定義 `number` 變數。

 [!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
在上例中，`number` 變數是如同 `int` 的強型別。 您也可以宣告隱含型別的區域變數，如下例所示。

 [!code-cs[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [方法參數](../../../csharp/language-reference/keywords/method-parameters.md)
