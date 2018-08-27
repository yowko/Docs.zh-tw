---
title: 方法 - C# 手冊
description: 方法、方法參數和方法傳回值的概觀
author: rpetrusha
ms.author: ronpet
ms.date: 05/21/2018
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: f5fd156ba25352fb1f816349c5e130267f7da8c2
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925840"
---
# <a name="methods"></a>方法 #

方法是包含一系列陳述式的程式碼區塊。 程式會造成呼叫方法並指定任何所需的方法引數來執行陳述式。 在 C# 中，每個執行的指示是在方法的內容中執行。 `Main` 方法是每個 C# 應用程式的進入點，而且它是由通用語言執行平台 (CLR) 啟動程式時呼叫。

> [!NOTE]
> 本主題討論具名的方法。 如需匿名函式的資訊，請參閱[匿名函式 (C# 程式設計手冊)](programming-guide/statements-expressions-operators/anonymous-functions.md)。

此主題包括下列章節：

- [方法簽章](#signatures)
- [方法引動過程](#invocation)
- [繼承和覆寫方法](#inherited)
- [傳遞參數](#passing)
  - [以傳值方式傳遞參數](#byval)
  - [以傳址方式傳遞參數](#byref)
  - [參數陣列](#paramarray)
- [選擇性參數和引數](#optional)
- [傳回值](#return)
- [擴充方法](#extension)
- [非同步方法](#async)
- [運算式主體成員](#expr)
- [迭代器](#iterators)

<a name="signatures"></a>
## <a name="method-signatures"></a>方法簽章 ##

指定下列項目以 `class` 或 `struct` 宣告方法：

- 選擇性的存取層級，例如 `public` 或 `private`。 預設為 `private`。
- 選擇性修飾詞，例如 `abstract` 或 `sealed`。
- 傳回值，或如果方法為無，則為 `void`。
- 方法名稱。
- 任何方法參數。 方法參數會放在括號中，並以逗號分隔。 空括號表示方法不需要任何參數。

這些組件一起構成方法簽章。

> [!NOTE]
> 方法的傳回類型不是方法多載用途的方法簽章的一部分。 不過，在判斷委派與所指向的方法之間的相容性時，它是方法簽章的一部分。

下例定義名為 `Motorcycle` 的類別，包含五個方法：

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

請注意，`Motorcycle` 類別包含多載方法 `Drive`。 兩種方法有相同的名稱，但是必須依其參數型別區別。

<a name="invocation"></a>
## <a name="method-invocation"></a>方法引動過程 ##

方法可以是「執行個體」或「靜態」。 叫用執行個體方法需要您具現化物件並針對該物件呼叫方法，執行個體方法會在該執行個體及資料上運作。 您可以參考方法所屬型別的名稱來叫用靜態方法，靜態方法運作不會在執行個體資料上操作。 嘗試透過物件執行個體呼叫靜態方法會產生編譯器錯誤。

呼叫方法就像是存取欄位。 在物件名稱後 (如果呼叫的是執行個體方法) 或型別名稱後 (如果呼叫的是 `static` 方法)，加上句點、方法名稱及括弧。 引數會在括號中列出，並以逗號分隔。

方法定義會指定所需的任何參數的名稱和類型。 在呼叫端叫用方法時，它會針對每個參數提供具體值及呼叫的引數。 引數必須與參數型別相容，但在呼叫程式碼中使用的引數，其引數名稱不需要與方法中定義的具名參數相同。 在下例中，`Square` 方法包含名為 *i* 之 `int` 型別的單一參數。 第一個方法呼叫會傳遞給 `Square` 方法型別 `int` 的 *num* 變數，第二個傳遞數值常數，第三個傳遞運算式。

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

最常見的方法引動過程形式過去使用位置引數，現在則依方法參數的順序來提供引數。 因此可以如下列範例所示呼叫 `Motorcycle` 類別的方法。 例如，呼叫 `Drive` 方法包含兩個引數，它們會對應至方法語法的兩個參數。 第一個成為 `miles` 參數的值，第二個是 `speed` 參數的值。

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

叫用方法時，您也可以使用「具名引數」，而不是使用位置引數。 使用具名引數時，您指定參數名稱，後面接著冒號 (":") 和引數。 方法的引數會以任意順序出現，只要有所有必要的引數。 下例使用具名引數來叫用 `TestMotorcycle.Drive` 方法。 本例中，具名引數的傳遞順序與方法參數清單的順序相反。

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

您可以使用位置引數和具名引數來叫用方法。 但位置引數不能接在具名引數後面。 下例會使用一個位置引數和一個具名引數，從前一個範例叫用 `TestMotorcycle.Drive` 方法。

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

 <a name="inherited"></a>
 ## <a name="inherited-and-overridden-methods"></a>繼承和覆寫方法 ##

除了在型別中明確定義的成員外，型別會繼承在其基底類別中定義的成員。 因為受管理的類型系統中之所有類型，都是直接或間接繼承自 <xref:System.Object> 類別，所以所有的類型都會繼承其成員，例如 <xref:System.Object.Equals(System.Object)>、<xref:System.Object.GetType> 及 <xref:System.Object.ToString>。 下例定義 `Person` 類別、具現化兩個 `Person` 物件，並呼叫 `Person.Equals` 方法以判斷兩個物件是否相等。 但是 `Equals` 方法不是在 `Person` 類別中定義，它繼承自 <xref:System.Object>。

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

型別可以使用 `override` 關鍵字並提供覆寫方法的實作，來覆寫繼承的成員。 方法簽章必須與覆寫方法的簽章相同。 下例與前一範例相似，不同之處在於它會覆寫 <xref:System.Object.Equals(System.Object)> 方法。 (它也會覆寫 <xref:System.Object.GetHashCode> 方法，因為兩種方法都是為了提供一致的結果。)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>
## <a name="passing-parameters"></a>傳遞參數 ##

C# 中的類型為「實值型別」「參考型別」。 如需內建實值型別的清單，請參閱[類型與變數](./tour-of-csharp/types-and-variables.md)。 根據預設，實值型別和參考型別都會以傳值方式傳遞至方法。

<a name="byval"></a>
### <a name="passing-parameters-by-value"></a>以傳值方式傳遞參數 ###

以傳值方式將實值型別傳遞至方法時，會將物件複本而不是物件本身傳遞至方法。 因此，當控制回到呼叫端時，呼叫的方法中的物件變更不會影響原始物件。

下例會以傳值方式將實值型別傳遞至方法，而呼叫的方法會嘗試變更實值型別的值。 它會定義 `int` 型別的變數 (它是實值型別)、將其值初始化為 20，再將它傳遞給名為 `ModifyValue` 的方法，此方法會將變數值變更為 30。 但傳回方法時，變數的值會維持不變。

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

當參考型別的物件以傳值方式傳遞至方法時，就會以傳值方式傳遞物件參考。 也就是說，此方法接收的不是物件本身，而是指出物件位置的引數。 如果您使用此參考來變更物件成員，當控制回到呼叫方法時，變更即會反映在物件中。 不過，當控制回到呼叫端時，取代傳遞至方法的物件不會影響原始物件。

下例會定義名為`SampleRefType` 的類別 (此為參考型別)。 它會具現化 `SampleRefType` 物件、將 44 指派給其 `value` 欄位，再將物件傳遞至 `ModifyObject` 方法。 本例會執行基本上與上一個範例相同的動作，依傳值方式將引數傳遞至方法。 但因為使用了參考型別，所以結果會不同。 在 `ModifyObject` 中對 `obj.value` 欄位的修改，也會將 `Main` 方法中引數 `rt` 的 `value` 欄位變更成 33，如範例輸出所示。

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>
### <a name="passing-parameters-by-reference"></a>以傳址方式傳遞參數 ###

當您想要變更方法中的引數值，且想要在控制回到呼叫方法時反映這項變更，您要以傳址方式傳遞參數。 若要以傳址方式傳遞參數，請使用 [`ref`](language-reference/keywords/ref.md) 或 [`out`](language-reference/keywords/out-parameter-modifier.md) 關鍵字。 您也可以傳址方式傳遞值，以避免發生複製的情況，但仍會無法使用 [`in`](language-reference/keywords/in-parameter-modifier.md) 關鍵字進行修改。

下例與前例相同，唯一差異是值以傳址方式傳遞至 `ModifyValue` 方法。 在 `ModifyValue` 方法中修改參數值時，當控制回到呼叫端時會反映值的變更。

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

依 ref 參數使用的常見模式包含交換變數值。 您以傳址方式將兩個變數傳遞至方法，且該方法會交換其內容。 下例會交換整數值。

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

傳遞參考型別參數可讓您變更參考本身的值，而不是其個別項目或欄位的值。

<a name="paramarray"></a>
### <a name="parameter-arrays"></a>參數陣列 ###

有時候，指定方法之引數確切數目的需求會有限制。 使用 `params` 關鍵字指出某參數是參數陣列，可使用數目可變的引數來呼叫方法。 以 `params` 關鍵字標記的參數必須是陣列型別，而且必須是方法參數清單中的最後一個參數。

然後呼叫端以下列三種方式之一來叫用方法︰

- 傳遞包含所需項目數目的適當型別陣列。
- 將適當型別各個引數的逗點分隔清單傳遞給方法。
- 不提供引數給參數陣列。

下例定義名為 `DoStringOperation` 的方法，其執行其第一個參數所指定的字串作業 `StringOperation` 列舉成員。 參數陣列會在字串開始執行作業時即定義字串。 `Main` 方法會示範這三種叫用方法的方式。 請注意，以 `params` 關鍵字標記的方法必須準備好處理參數陣列中無任何提供引數的情況，因此其值是 `null`。

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref108.cs#108)]

<a name="optional"></a>
## <a name="optional-parameters-and-arguments"></a>選擇性參數和引數 ##

方法定義可以指定其參數為必要項目或選擇項目。 根據預設，參數為必要項目。 在方法定義中包含參數的預設值即可指定選擇性參數。 呼叫此方法時，如不為選擇性參數提供任何引數，則改用預設值。

參數的預設值必須由下列運算式種類之一指派︰

- 常數，例如常值字串或數字。
- `new ValType` 形式的運算式，其中 `ValType` 是實值型別。 請注意，這樣會叫用實值型別的隱含預設建構函式，它不是型別的實際成員。
- `default(ValType)` 形式的運算式，其中 `ValType` 是實值型別。

如果方法同時包含必要和選擇性參數，則選擇性參數會定義在參數清單結尾，在所有必要參數的後面。

下例會定義 `ExampleMethod` 方法，它有一個必要參數和兩個選擇性參數。

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

如果使用位置引數叫用了有多個選擇性引數的方法，則呼叫端必須為所有選擇性參數提供引數，從第一個到最後一個。 以 `ExampleMethod` 方法為例，當呼叫端為 `description` 參數提供引數時，它也必須為 `optionalInt` 參數提供一個引數。 `opt.ExampleMethod(2, 2, "Addition of 2 and 2");` 是有效的方法呼叫，而 `opt.ExampleMethod(2, , "Addition of 2 and 0);` 會產生「引數遺失」編譯器錯誤。

如果使用具名引數或位置和具名引數的組合來呼叫方法，則呼叫端可以省略方法呼叫中最後一個位置引數之後的任何引數。

下例呼叫三次 `ExampleMethod` 方法。  前兩個方法呼叫使用位置引數。 第一個省略了這兩個選擇性引數，而第二個省略了最後一個引數。 第三個方法呼叫提供了必要參數的位置引數，但在使用具名引數將值提供給 `description` 參數時省略 `optionalInt` 引數。

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

使用選擇性參數會影響「多載解析」，或 C# 編譯器判斷依方法呼叫應叫用哪個特定多載的方式，如下所示︰

- 如果每個參數都是選擇性或為依名稱或位置對應要呼叫之陳述式的單一引數，且該引數可以轉換成參數的型別，則方法、索引子或建構函式就是執行的候選項目。
- 如果找到多個候選項目，則慣用轉換的多載解析規則會套用至明確指定的引數。 會忽略選擇性參數的省略引數。
- 如果兩個候選項目的評斷結果一樣好，則偏向沒有選擇性參數的候選項目，其會在呼叫中省略引數。 這是多載解析一般偏好參數較少之候選項目的結果。

 <a name="return"></a>
 ## <a name="return-values"></a>傳回值 ##

方法可以傳回值給呼叫者。 針對傳回型別，如果列在方法名稱前面的型別不是 `void`，則方法可以使用 `return` 關鍵字傳回值。 在 `return` 關鍵字後面接著符合傳回型別的變數、常數或運算式的陳述式，會將該值傳回給方法呼叫端。 具有非 void 傳回類型的方法需要使用 `return` 關鍵字以傳回值。 `return` 關鍵字也會停止執行方法。

如果傳回類型為 `void`，不含值的 `return` 陳述式對於停止方法的執行仍很有用。 若沒有 `return` 關鍵字，在方法到達程式碼區塊的結尾時，方法將會停止執行。

例如，這兩種方法使用 `return` 關鍵字傳回整數：

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

若要使用從方法傳回的值，呼叫方法可以在使用相同類型值的任意位置使用方法呼叫本身即已足夠。 您也可以指派傳回值給變數。 例如，下列兩個程式碼範例會達到相同的目標：

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

使用區域變數，在此情況下的 `result`來儲存值是選擇性的。 它有助於程式碼的可讀性，或如果您需要儲存方法的整個範圍引數的原始值，則可能為必要。

有時候，您希望自己的方法傳回的不止單一值。 從 C# 7.0 開始，您可以使用「Tuple 型別」和「Tuple 常值」輕鬆達到這個目標。 Tuple 型別會定義 Tuple 項目的資料類型。 Tuple 常值會提供傳回 Tuple 的實際值。 在下列範例中，`(string, string, string, int)` 會定義由 `GetPersonalInfo` 方法所傳回的 Tuple 類型。 運算式 `(per.FirstName, per.MiddleName, per.LastName, per.Age)` 是 Tuple 常值，方法會傳回 `PersonInfo` 物件的名字、中間名和姓氏以及年齡。

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    if (per != null)
       return (per.FirstName, per.MiddleName, per.LastName, per.Age);
    else
       return null;
}
```

然後呼叫端使用傳回的 Tuple 及程式碼，如下所示︰

```csharp
var person = GetPersonalInfo("111111111")
if (person != null)
   Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

在 Tuple 型別定義中也可以將名稱指派給 Tuple 項目。 下例示範使用具名項目的 `GetPersonalInfo` 方法替代版本：

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    if (per != null)
       return (per.FirstName, per.MiddleName, per.LastName, per.Age);
    else
       return null;
}
```

前一次的 `GetPersonInfo` 方法呼叫可修改如下︰

```csharp
var person = GetPersonalInfo("111111111");
if (person != null)
   Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

如果方法將陣列當作引數傳遞並修改個別項目的值，方法就不需要傳回陣列，雖然您可選擇這樣做以取得良好的值樣式或功能性流程。  這是因為 C# 會以傳值方式傳遞所有的參考型別，而陣列參考的值是陣列的指標。 在下例中，以 `DoubleValues` 方法完成的 `values` 陣列內容變更，都可透過任何具有陣列參考的程式碼觀察到。

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

 <a name="exten"></a>
 ## <a name="extension-methods"></a>擴充方法 ##

一般來說，有兩種方式可將方法加入至現有的型別︰

- 修改該型別的原始程式碼。 如果您未擁有型別的原始程式碼，當然就無法這樣做。 而如果您同時新增任何私用資料欄位以支援方法，這會成為一項重大變更。
- 在衍生類別中定義新的方法。 方法不能以使用其他型別繼承的這種方式新增，例如結構和列舉。 也不能用來將方法「新增」至密封的類別。

擴充方法可讓您將方法「新增」至現有的類型，但不必修改型別本身或在繼承的型別中實作新方法。 擴充方法也不必和其擴充型別位於相同的組件中。 呼叫擴充方法就像它是型別的定義成員一樣。

如需詳細資訊，請參閱[擴充方法](programming-guide/classes-and-structs/extension-methods.md)。

<a name="async"></a>
## <a name="async-methods"></a>非同步方法 ##

使用非同步功能，您就可以呼叫非同步方法，而不需要使用明確回呼或手動將您的程式碼分散到多種方法或 lambda 運算式上。

如果您使用 [async](language-reference/keywords/async.md) 修飾詞來標示方法，則可以在方法中使用 [await](language-reference/keywords/await.md) 運算子。 當控制項到達 async 方法的 `await` 運算式時，如果等候的工作未完成，控制會回到呼叫端，而有 `await` 關鍵字之方法中的進度會暫停，直到等候的工作完成。 當工作完成時，方法中的執行可以繼續。

> [!NOTE]
> 非同步方法會在遇到第一個未完成的等候物件或是到達非同步方法的結尾時 (以先發生者為準)，傳回呼叫者

非同步方法可以有 <xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.Task> 或 `void` 的傳回類型。 `void` 傳回型別主要用於定義需要 `void` 傳回型別的事件處理常式。 傳回 `void` 的非同步方法無法等候，而且 void 傳回方法的呼叫端無法攔截方法擲回的例外狀況。 從 C# 7.0 開始，非同步方法可具備[任何類似工作的傳回類型](./whats-new/csharp-7.md#generalized-async-return-types)。

在下例中，`DelayAsync` 是包含會傳回整數之 return 陳述式的非同步方法。 因為它是非同步方法，所以其方法宣告必須有傳回型別 `Task<int>`。 因為傳回型別是 `Task<int>`，所以 `DoSomethingAsync` 中 `await` 運算式的評估會產生整數，如下列 `int result = await delayTask` 陳述式所示。

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

非同步方法不可以宣告任何 [in](language-reference/keywords/in-parameter-modifier.md)、[ref](language-reference/keywords/ref.md) 或 [out](language-reference/keywords/out-parameter-modifier.md) 參數，但是可以呼叫具有這類參數的方法。

 如需非同步方法的詳細資訊，請參閱 [Asynchronous Programming with async and await (C#)](async.md) (使用 Async 和 Await 進行非同步程式設計 (C#))、[Control Flow in Async Programs (C#)](programming-guide/concepts/async/control-flow-in-async-programs.md) (非同步程式中的控制流程 (C#)) 和 [Async Return Types (C#)](programming-guide/concepts/async/async-return-types.md) (非同步傳回型別 (C#))。

<a name="expr"></a>
## <a name="expression-bodied-members"></a>運算式主體成員 ##

方法定義只是立即傳回運算式的結果，或是具有單一陳述式做為方法的主體是很常見的。  使用 `=>`定義這類方法有個語法捷徑：

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

如果方法傳回 `void` 或為非同步方法，則方法的主體必須是陳述式運算式 (如同 Lambda)。  針對屬性和索引子，它們必須是唯讀，而且您不會使用 `get` 存取子關鍵字。

<a name="iterators"></a>
## <a name="iterators"></a>迭代器 ##

迭代器會對集合執行自訂的反覆項目，例如清單或陣列。 迭代器會使用 [yield return](language-reference/keywords/yield.md) 陳述式一次傳回一個項目。 達到 `yield return` 陳述式時，即會記住目前的位置，讓呼叫端可以要求序列中的下一個項目。

迭代器的傳回類型可以是 <xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>或 <xref:System.Collections.Generic.IEnumerator%601>。

如需詳細資訊，請參閱[迭代器](programming-guide/concepts/iterators.md)。

## <a name="see-also"></a>另請參閱 ##

- [存取修飾詞](language-reference/keywords/access-modifiers.md)   
- [靜態類別和靜態類別成員](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
- [繼承](programming-guide/classes-and-structs/inheritance.md)   
- [抽象和密封類別以及類別成員](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
- [params](language-reference/keywords/params.md)   
- [out](language-reference/keywords/out-parameter-modifier.md)   
- [ref](language-reference/keywords/ref.md)   
- [in](language-reference/keywords/in-parameter-modifier.md)   
- [傳遞參數](programming-guide/classes-and-structs/passing-parameters.md)
