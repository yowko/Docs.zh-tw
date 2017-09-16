---
title: "ref (C# 參考)"
ms.date: 2017-05-30
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: 32
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 003125ca6218d42a919d8bb592b5454a7cb387c7
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="ref-c-reference"></a>ref (C# 參考)

`ref` 關鍵字指出以傳址方式傳遞的值。 它用於三個不同的內容： 

- 在方法簽章和方法呼叫中，以傳址方式將引數傳遞給方法。 如需詳細資訊，請參閱[以傳址方式傳遞引數](#passing-an-argument-by-reference)。

- 在方法簽章中，以傳址方式將值傳回給呼叫者。 如需詳細資訊，請參閱[參考傳回值](#reference-return-values)。

- 在成員主體中，指出參考傳回值儲存在本機作為呼叫者想要修改的參考。 如需詳細資訊，請參閱 [ref 區域變數](#ref-locals)。

## <a name="passing-an-argument-by-reference"></a>以傳址方式傳遞引數

用於方法的參數清單時，`ref` 關鍵字指出以傳址方式傳遞引數，而不是以傳值方式。 以傳址方式傳遞的效果是已呼叫方法中引數的任何變更都會反映在呼叫方法中。 例如，如果呼叫者傳遞區域變數運算式或陣列元素存取運算式，而且已呼叫方法取代 ref 參數所參考的物件，則在傳回方法時，呼叫者的區域變數或陣列元素現在會參考新的物件。

> [!NOTE]
>  請勿將參考傳遞的概念與參考類型的概念相混淆。 兩個概念並不相同。 方法參數可以由 `ref` 修改，而不論其是否為實值類型或參考類型。 當實值類型由參考傳遞時，沒有 boxing。  

若要使用 `ref` 參數，方法定義和呼叫方法都必須明確使用 `ref` 關鍵字，如下列範例所示。  

[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]

傳遞至 `ref` 參數的引數，在傳遞之前必須先初始化。 這與 [out](out.md) 參數不同，其引數不需要在傳遞之前先明確初始化。

類別的成員不能擁有僅在 `ref` 和 `out` 方面不同的簽章。 如果類型的兩個成員之間唯一的區別在於其中一個具有 `ref` 參數，而另一個具有 `out` 參數，則編譯器會發生錯誤。 例如，下列程式碼不會進行編譯。  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]
  
 不過，如果一種方法具有 `ref` 或 `out` 參數，而且另一種方法具有實值參數，則可以多載方法，如下列範例所示。
  
 [!code-cs[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]
  
 在需要簽章比對的其他情況 (如隱藏或覆寫) 下，`ref` 和 `out` 是簽章的一部分，而且彼此不相符。  
  
 屬性不是變數。 它們都是方法，且不能傳遞給 `ref` 參數。  
  
 如需如何傳遞陣列的資訊，請參閱[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。  
  
 您不能將 `ref` 和 `out` 關鍵字用於下列幾種方法：  
  
-   使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的 async 方法。  
  
-   迭代器方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。  
  
## <a name="passing-an-argument-by-reference-an-example"></a>以傳址方式傳遞引數：範例

先前的範例會以傳址方式傳遞實值型別。 您也可以使用 `ref` 關鍵字，以傳址方式傳遞參考型別。 以傳址方式傳遞參考型別，可讓已呼叫方法取代參考參數在呼叫者中所參考的物件。 物件的儲存位置會以參考參數值的方式，傳遞至方法。 如果您變更參數儲存位置中的值 (指向新的物件)，則也會變更呼叫端所參考的儲存位置。 下列範例會以 `ref` 參數，傳遞參考類型的執行個體。   
  
 [!code-cs[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]  

如需如何依傳值和依傳址方式來傳遞參考類型的詳細資訊，請參閱[傳遞參考類型參數](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)。
  
## <a name="reference-return-values"></a>參考傳回值

參考傳回值 (或 ref 傳回值) 是方法以傳址方式傳回給呼叫者的值。 也就是說，呼叫者可以修改方法所傳回的值，而且該變更會反映在包含方法的物件狀態中。 

參考傳回值是使用 `ref` 關鍵字所定義：

- 在方法簽章中。 例如，下列方法簽章指出 `GetCurrentPrice` 方法以傳址方式傳回 <xref:System.Decimal> 值。

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- 方法中每個 `return` 陳述式的前面。 例如: 
 
   ```csharp
   ref return Decimal.Zero;
   ``` 

為了讓呼叫者修改物件的狀態，參考傳回值必須儲存至明確定義為 [ref 區域變數](#ref-locals)的變數。 

如需範例，請參閱 [ref 傳回值和 ref 區域變數範例](#a-ref-returns-and-ref-locals-example)。

## <a name="ref-locals"></a>ref 區域變數

ref 區域變數用來參考使用 `ref return` 所傳回的值。  ref 區域變數必須初始化並指派給 ref 傳回值。 任何對 ref 區域變數值進行的修改，都會反映在其方法以傳址方式傳回值之物件的狀態。

定義 ref 區域變數的方式是在變數宣告前面使用 `ref` 關鍵字，並且緊接在以傳址方式傳回值的方法呼叫前面。 

例如，下列陳述式定義名為 `GetEstimatedValue` 之方法所傳回的 ref 區域變數值：

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

請注意，`ref` 關鍵字必須用在兩個位置，或者編譯器會產生錯誤 CS8172「無法使用值將傳址變數初始化」。 
 
## <a name="a-ref-returns-and-ref-locals-example"></a>ref 傳回值和 ref 區域變數範例

下面範例會定義具有 `Title` 和 `Author` 這兩個 <xref:System.String> 欄位的 `Book` 類別。 它也會定義 `BookCollection` 類別，以包含 `Book` 物件的私用陣列。 以傳址方式傳回個別書籍物件，方法是呼叫其 `GetBookByTitle` 方法。

[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]  

呼叫者將 `GetBookByTitle` 方法所傳回的值儲存為 ref 區域變數時，呼叫者對傳回值進行的變更會反映在 `BookCollection` 物件中，如下列範例所示。

[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]  

## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [傳遞參數](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [方法參數](../../../csharp/language-reference/keywords/method-parameters.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)

