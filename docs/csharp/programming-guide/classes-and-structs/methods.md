---
title: "方法 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
caps.latest.revision: 41
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: da1abda4faec540c115d93e14a757dae24c5ae78
ms.contentlocale: zh-tw
ms.lasthandoff: 05/15/2017

---
# <a name="methods-c-programming-guide"></a>方法 (C# 程式設計手冊)
方法是包含一系列陳述式的程式碼區塊。 程式會造成呼叫方法並指定任何所需的方法引數來執行陳述式。 在 C# 中，每個執行的指示是在方法的內容中執行。 Main 方法是每個 C# 應用程式的進入點，而且它是由 Common Language Runtime (CLR) 啟動程式時呼叫。  
  
> [!NOTE]
>  本主題討論具名的方法。 如需匿名函式的資訊，請參閱[匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)。  
  
## <a name="method-signatures"></a>方法簽章  
 方法是在 [類別](../../../csharp/language-reference/keywords/class.md) 或 [結構](../../../csharp/language-reference/keywords/struct.md) 中宣告，透過指定存取層級 (例如 `public` 或 `private`)、選擇性修飾詞 (例如 `abstract` 或 `sealed`)、傳回值、方法的名稱，以及任何方法參數。 這些部份放在一起即為方法的簽章。  
  
> [!NOTE]
>  方法的傳回類型不是方法多載用途的方法簽章的一部分。 不過，在判斷委派與所指向的方法之間的相容性時，它是方法簽章的一部分。  
  
 方法參數會放在括號中，並以逗號分隔。 空括號表示方法不需要任何參數。 這個類別包含三個方法：  
  
 [!code-cs[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]  
  
## <a name="method-access"></a>方法存取  
 在物件上呼叫方法，就像是存取欄位。 在物件名稱後面加上句點、方法的名稱與括號。 引數會在括號中列出，並以逗號分隔。 因此可以如下列範例所示呼叫 `Motorcycle` 類別的方法：  
  
 [!code-cs[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]  
  
## <a name="method-parameters-vs-arguments"></a>方法參數與引數  
 方法定義會指定所需的任何參數的名稱和類型。 在呼叫程式碼呼叫此方法時，它會提供對每個參數呼叫的引數的具體值。 引數都必須與參數類型相容，呼叫程式碼中使用的引數名稱 (如果有的話) 不需要與方法中定義的具名參數相同。 例如:   
  
 [!code-cs[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>以傳址方式傳遞與以傳值方式傳遞  
 根據預設，傳遞實值類型至方法時，會傳遞複本，而不是物件本身。 因此，對引數的變更對於呼叫方法中的原始複本不會有影響。 您可以使用 ref 關鍵字依參考傳遞實值類型。 如需詳細資訊，請參閱[傳遞實值型別參數](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)。 如需內建實值型別的清單，請參閱[實值型別表](../../../csharp/language-reference/keywords/value-types-table.md)。  
  
 傳遞參考類型的物件至方法時，會傳遞物件的參考。 也就是說，此方法接收的不是物件本身，而是指出物件位置的引數。 如果您使用此參考變更物件的成員，變更會反映在呼叫方法的引數中，即使以傳值方式傳遞物件。  
  
 您會使用 `class` 關鍵字建立參考類型，如下列範例所示。  
  
 [!code-cs[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]  
  
 現在，如果您將此類型為基礎的物件傳遞至方法，即會傳遞物件的參考。 下列範例會將類型 `SampleRefType` 的物件傳遞至方法 `ModifyObject`。  
  
 [!code-cs[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]  
  
 此範例會執行與上一個範例基本上相同的動作，依傳值方式將引數傳遞至方法。 但是，由於使用參考類型，結果會不同。 `ModifyObject` 中對參數 `value` 的 `obj`欄位做的修改，也會變更 `value` 方法中引數 `rt`的 `TestRefType` 欄位。 `TestRefType` 方法會顯示 33 做為輸出。  
  
 如需如何依傳址和依傳值方式來傳遞參考型別的詳細資訊，請參閱[傳遞參考型別參數](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)和[參考型別](../../../csharp/language-reference/keywords/reference-types.md)。  
  
## <a name="return-values"></a>傳回值  
 方法可以傳回值給呼叫者。 針對傳回類型，如果列在方法名稱前面的類型不是 `void`，方法可以使用 `return` 關鍵字傳回值。 具有 `return` 關鍵字後面接著符合傳回類型值的陳述式，會將該值傳回給方法呼叫者。 `return` 關鍵字也會停止執行方法。 如果傳回類型為 `void`，不含值的 `return` 陳述式對於停止方法的執行仍很有用。 若沒有 `return` 關鍵字，在方法到達程式碼區塊的結尾時，方法將會停止執行。 具有非 void 傳回類型的方法需要使用 `return` 關鍵字以傳回值。 例如，這兩種方法使用 `return` 關鍵字傳回整數：  
  
 [!code-cs[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]  
  
 若要使用從方法傳回的值，呼叫方法可以在使用相同類型值的任意位置使用方法呼叫本身即已足夠。 您也可以指派傳回值給變數。 例如，下列兩個程式碼範例會達到相同的目標：  
  
 [!code-cs[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]  
  
 [!code-cs[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]  
  
 使用區域變數，在此情況下的 `result`來儲存值是選擇性的。 它有助於程式碼的可讀性，或如果您需要儲存方法的整個範圍引數的原始值，則可能為必要。  
  
 如果呼叫端函式將多維陣列傳遞給可修改陣列內容的方法 M，則不需要從 M 傳回該陣列。您可能會從 M 傳回產生的陣列，而產生的陣列具有良好樣式或功能流程的值，但並不需要。  這是因為 C# 會以傳值方式傳遞所有參考型別，而陣列參考的值是陣列的指標，因此您不需要傳回已修改的陣列。 在方法 M 中，任何陣列內容變更都可以透過任何具有陣列參考的程式碼觀察到，如下列範例所示。  
  
```csharp  
static void Main(string[] args)  
        {  
            int[,] matrix = new int[2, 2];  
            FillMatrix(matrix);  
            // matrix is now full of -1  
        }  
  
        public static void FillMatrix(int[,] matrix)  
        {  
            for (int i = 0; i < matrix.GetLength(0); i++)  
            {  
                for (int j = 0; j < matrix.GetLength(1); j++)  
                {  
                    matrix[i, j] = -1;  
                }  
            }  
        }  
```  
  
 如需詳細資訊，請參閱 [return](../../../csharp/language-reference/keywords/return.md)。  
  
## <a name="async-methods"></a>非同步方法  
 使用非同步功能，您就可以呼叫非同步方法，而不需要使用明確回呼或手動將您的程式碼分散到多種方法或 lambda 運算式上。 
  
 如果您使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞來標示方法，可以在方法中使用 [await](../../../csharp/language-reference/keywords/await.md) 運算子。 當控制項到達 async 方法的 await 運算式時，控制項會傳回給呼叫者，方法中的進度會暫停，直到等候的工作完成。 當工作完成時，方法中的執行可以繼續。  
  
> [!NOTE]
>  非同步方法會在遇到第一個未完成的等候物件或是到達非同步方法的結尾時 (以先發生者為準)，傳回呼叫者  
  
 非同步方法的傳回類型可以是 <xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.Task> 或 void。 void 傳回類型主要用於定義需要 void 傳回類型的事件處理常式。 傳回 void 類型的非同步方法無法等候，而且 void 傳回方法的呼叫者無法攔截方法擲回的例外狀況。  
  
 在下列範例中，`DelayAsync` 是會傳回類型 <xref:System.Threading.Tasks.Task%601> 的非同步方法。 `DelayAsync` 具有傳回整數的 `return` 陳述式。 因此 `DelayAsync` 的方法宣告必須具有傳回類型 `Task<int>`。 因為傳回類型是 `Task<int>`， `await` 中 `DoSomethingAsync` 運算式的評估會產生整數，如下列陳述式所示範： `int result = await delayTask`。  
  
 `startButton_Click` 方法是傳回類型為 void 的非同步方法的範例。 因為 `DoSomethingAsync` 是非同步方法，對 `DoSomethingAsync` 的呼叫工作必須等候，如下列陳述式所示： `await DoSomethingAsync();`。 `startButton_Click` 方法都必須定義 `async` 修飾詞，因為方法有 `await` 運算式。  
  
 [!code-cs[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]  
  
 非同步方法不可以宣告任何 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數，但是可以呼叫具有這類參數的方法。  
  
 如需非同步方法的詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)、[非同步程式中的控制流程](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)和[非同步傳回型別](../../../csharp/programming-guide/concepts/async/async-return-types.md)。  
  
## <a name="expression-body-definitions"></a>運算式主體定義  
 方法定義只是立即傳回運算式的結果，或是具有單一陳述式做為方法的主體是很常見的。  使用 `=>`定義這類方法有個語法捷徑：  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 如果方法會傳回 `void` 或非同步方法，則方法的主體必須是陳述式運算式 (如同 lambda)。  若為屬性和索引子，它們必須是唯讀，因此您不應使用 `get` 存取子關鍵字。  
  
## <a name="iterators"></a>Iterator  
 迭代器會對集合執行自訂的反覆項目，例如清單或陣列。 迭代器會使用 [yield return](../../../csharp/language-reference/keywords/yield.md) 陳述式來一次傳回一個項目。 當 [yield return](../../../csharp/language-reference/keywords/yield.md) 到達陳述式時，會記住在程式碼中的目前位置。 下一次呼叫迭代器時，便會從這個位置重新開始執行。  
  
 您會使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式，透過用戶端程式碼呼叫迭代器。  
  
 迭代器的傳回類型可以是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。  
  
 如需詳細資訊，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](index.md)   
 [存取修飾詞](access-modifiers.md)   
 [靜態類別和靜態類別成員](static-classes-and-static-class-members.md)   
 [繼承](inheritance.md)   
 [抽象和密封類別以及類別成員](abstract-and-sealed-classes-and-class-members.md)   
 [params](../../../csharp/language-reference/keywords/params.md)   
 [return](../../../csharp/language-reference/keywords/return.md)   
 [out](../../../csharp/language-reference/keywords/out.md)   
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [傳遞參數](passing-parameters.md)

