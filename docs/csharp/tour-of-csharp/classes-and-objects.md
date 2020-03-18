---
title: C# 中的類別和物件 - C# 語言教學課程
description: 第一次接觸 C#？ 閱讀類、物件和繼承的此概述
ms.date: 02/27/2020
ms.assetid: 63a89bde-0f05-4bc4-b0cd-4f693854f0cd
ms.openlocfilehash: c178e11b5667905f75538555c8a309e2fdb4a9ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159178"
---
# <a name="classes-and-objects"></a>類別與物件

*類*是 C# 的最基本類型。 類別是以單一單位結合狀態 (欄位) 和動作 (方法及其他函式成員) 的資料結構。 類別可以為動態建立的類別「執行個體」**(稱為「物件」**) 提供定義。 類別支援「繼承」** 和「多型」**，這些是可供「衍生類別」** 將「基底類別」** 延伸及特製化的機制。

建立新類別時，是使用類別宣告來建立。 類別宣告的開頭是一個標頭，此標頭會指定類別的屬性和修飾詞、類別的名稱、基底類別 (如果提供)，以及類別所實作的介面。 此標頭後面會接著類別主體，此主體是由在 `{` 與 `}` 分隔符號之間撰寫的成員宣告清單所組成。

以下代碼顯示名為`Point`： 的簡單類的聲明：

[!code-csharp[PointClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L11)]

建立類別執行個體時，是使用 `new` 運算子來建立，此運算子會為新執行個體配置記憶體、叫用建構函式來將執行個體初始化，然後傳回對執行個體的參考。 下列陳述式會建立兩個 Point 物件，並以兩個變數儲存對這些物件的參考：

[!code-csharp[PointExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L9-L10)]

當物件不再可供存取時，系統會自動回收物件所佔用的記憶體。 在 C# 中顯式解構物件既不必要也是不可能的。

## <a name="members"></a>成員

類別的成員不是靜態成員，就是執行個體成員。 靜態成員隸屬於類別，而執行個體成員則隸屬於物件 (類別的執行個體)。

下面的清單概述了類可以包含的成員類型。

- 常數
  - 與類別關聯的常數值
- 欄位
  - 類別的變數
- 方法
  - 類別所能執行的計算和動作
- 屬性
  - 與讀取和寫入具名的類別特性關聯的動作
- 索引子
  - 與編製陣列之類的類別執行個體關聯的動作
- 事件
  - 類別所能產生的通知
- 操作員
  - 類別所支援的轉換和運算式運算子
- 建構函式
  - 將類別執行個體或類別本身初始化所需的動作
- 完成項
  - 在永久捨棄類別執行個體之前所要執行的動作
- 類型
  - 類別所宣告的巢狀型別

## <a name="accessibility"></a>Accessibility

類的每個成員都有一個關聯的可訪問性，它控制可以訪問該成員的程式文本區域。 存取能力有六種可能的形式。 訪問修改器總結如下。

- `public`
  - 訪問不受限制。
- `protected`
  - 訪問僅限於此類或從此類派生的類。
- `internal`
  - 訪問僅限於當前程式集（.exe、.dll 等）。
- `protected internal`
  - 訪問僅限於包含類、派生自包含類的類或同一程式集中的類。
- `private`
  - 訪問僅限於此類。
- `private protected`
  - 訪問僅限於從同一程式集中的包含類型派生的包含類或類。

## <a name="type-parameters"></a>型別參數

類別定義可以在類別名稱後面以角括弧括住型別參數名稱清單，來定義一組型別參數。 接著，就可以在類別宣告的主體中使用這些型別參數，來定義類別的成員。 在下列範例中，`Pair` 的型別參數是 `TFirst` 和 `TSecond`：

[!code-csharp[Pair](~/samples/snippets/csharp/tour/classes-and-objects/Pair.cs#L3-L7)]

類別型別若宣告為會採用型別參數，即稱為「泛型類別型別」**。 結構、介面和委託類型也可以是泛型的。
使用泛型類別時，必須為每個型別參數提供型別參數：

[!code-csharp[PairExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L15-L17)]

泛型型別若已有提供的型別參數 (如上述的 `Pair<int,string>`)，即稱為「建構的型別」**。

## <a name="base-classes"></a>基底類別

類別宣告可以在類別名稱和型別參數後面加上冒號和基底類別的名稱，來指定基底類別。 省略基底類別規格即等同於衍生自類型 `object`。 在下列範例中，`Point3D` 的基底類別是 `Point`，而 `Point` 的基底類別是 `object`：

[!code-csharp[Point3DClass](~/samples/snippets/csharp/tour/classes-and-objects/Point.cs#L3-L20)]

類別會繼承其基底類別的成員。 繼承意謂著類別隱含地包含其基底類別的所有成員，但執行個體和靜態建構函式及基底類別的完成項除外。 派生類可以將新成員添加到它繼承的成員，但不能刪除繼承成員的定義。 在先前的範例中，`Point3D` 會從 `Point` 繼承 `x` 和 `y` 欄位，而每個 `Point3D` 執行個體都會包含 `x`、`y` 及 `z` 這三個欄位。

在類別型別到其任何基底類別型別之間都存在著隱含轉換。 類類型的變數可以引用該類的實例或任何派生類的實例。 例如，以先前的類別宣告為例，`Point` 型別的變數可以參考 `Point` 或 `Point3D`：

[!code-csharp[Point3DExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L22-L23)]

## <a name="fields"></a>欄位

「欄位」** 是與類別或類別執行個體關聯的變數。

使用 static 修飾詞來宣告的欄位會定義靜態欄位。 靜態欄位只會識別一個儲存位置。 無論創建多少個類的實例，靜態欄位只有一個副本。

未使用 static 修飾詞來宣告的欄位會定義執行個體欄位。 每個類別執行個體都包含一個該類別所有執行個體欄位的個別複本。

在下面的示例中`Color`，類的每個實例都有`r`單獨的 副本，`g`和`b`實例欄位，但只有一個副本的`Black`、 `White`、 `Red`、`Green`和`Blue`靜態欄位：

[!code-csharp[ColorClass](~/samples/snippets/csharp/tour/classes-and-objects/Color.cs#L3-L17)]

如先前的範例所示，可以使用 `readonly` 修飾詞來宣告「唯讀欄位」**。 只有在欄位的宣告或在相同類別的建構函式中，才能對 `readonly` 欄位進行指派。

## <a name="methods"></a>方法

「方法」** 是實作物件或類別所能執行之計算或動作的成員。 存取「靜態方法」** 時，是透過類別來存取。 存取「執行個體方法」** 時，是透過類別的執行個體來存取。

方法可能會有一份「參數」** 清單和「傳回型別」**，前者代表傳送給方法的值或變數參考，後者則指定方法所計算並傳回的值型別。 方法的返回類型是`void`它不傳回值。

與型別相同，方法也可能有一組型別參數，而呼叫方法時，必須為這些參數指定型別引數。 與型別不同的是，型別引數通常可以從方法呼叫的引數推斷，而不需要明確指定。

在宣告方法的類別中，方法的「簽章」** 必須是唯一的。 方法的簽章是由方法的名稱、型別參數的數目以及其參數的數目、修飾詞和型別所組成。 方法的簽名不包括返回類型。

### <a name="parameters"></a>參數

參數是用來將值或變數參考傳遞給方法。 方法的參數會從叫用方法時所指定的「引數」** 取得其實際值。 參數有四種：值參數、參考參數、輸出參數，以及參數陣列。

「值參數」** 適用於傳遞輸入引數。 值參數會對應至區域變數，此變數會從針對參數傳遞的引數取得其初始值。 對值參數的修改不會影響為參數傳遞的參數。

只要指定預設值，值參數便可以成為選用參數，如此即可省略對應的引數。

「參考參數」** 適用於以參考方式傳遞引數。 針對參考參數傳遞的引數必須是含有定義值的變數，而在執行方法的期間，參考參數會代表與引數變數相同的儲存位置。 宣告參考參數時，是使用 `ref` 修飾詞來宣告。 下列範例示範 `ref` 參數的用法。

[!code-csharp[swapExample](~/samples/snippets/csharp/tour/classes-and-objects/RefExample.cs#L3-L18)]

「輸出參數」** 適用於以參考方式傳遞引數。 其類似於參考參數，只不過它並不需要您明確指派值給呼叫端提供的引數。 宣告輸出參數時，是使用 `out` 修飾詞來宣告。 下列範例示範如何使用 C# 7 中所引入的語法來利用 `out` 參數。

[!code-csharp[OutExample](~/samples/snippets/csharp/tour/classes-and-objects/OutExample.cs#L3-L17)]

「參數陣列」** 可允許將數目不固定的引數傳遞給方法。 宣告參數陣列時，是使用 `params` 修飾詞來宣告。 只有方法的最後一個參數可以是參數陣列，而參數陣列的型別必須是單一維度陣列型別。 <xref:System.Console?displayProperty=nameWithType> 類別的 Write 和 WriteLine 方法即為參數陣列用法的好例子。 聲明如下。

[!code-csharp[ConsoleExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L78-L83)]

在使用參數陣列的方法內，參數陣列的行為與陣列型別的一般參數完全相同。 但是，在調用具有參數陣列的方法時，可以傳遞參數陣列類型的單個參數或參數陣列元素類型的任意數量的參數。 在後者的案例中，會自動建立陣列執行個體並以指定的引數將其初始化。 以下範例

[!code-csharp[StringFormat](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L55-L55)]

等同於撰寫下列程式碼。

[!code-csharp[StringFormat2](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L30-L35)]

### <a name="method-body-and-local-variables"></a>方法主體和區域變數

方法的主體會指定叫用方法時所要執行的陳述式。

方法主體可以宣告方法叫用專屬的變數。 這類變數稱為「區域變數」**。 區域變數宣告會指定型別名稱、變數名稱，還可能指定初始值。 下列範例會宣告一個初始值為零的區域變數 `i`，以及一個沒有初始值的區域變數 `j`。

[!code-csharp[Squares](~/samples/snippets/csharp/tour/classes-and-objects/Squares.cs#L3-L17)]

C# 要求必須「明確指派」** 區域變數，才能取得其值。 例如，如果前面的`i`聲明不包含初始值，編譯器將報告後續用法的錯誤，`i`因為`i`不會在程式中的這些點明確分配。

方法可以使用 `return` 陳述式將控制權交還給其呼叫端。 在返回`void`的方法中，`return`語句不能指定運算式。 在傳回非 void 的方法中，`return` 陳述式必須包含會計算傳回值的運算式。

### <a name="static-and-instance-methods"></a>靜態和執行個體方法

使用 static 修飾詞來宣告的方法即為「靜態方法」**。 靜態方法不在特定實例上操作，只能直接存取靜態成員。

不使用 static 修飾詞來宣告的方法即為「執行個體方法」**。 執行個體方法會在特定的執行個體上運作，並且既可存取靜態成員也可存取執行個體成員。 透過 `this` 可以明確存取叫用執行個體方法時所在的執行個體。 `this`在靜態方法中引用是錯誤的。

下列 `Entity` 類別同時含有靜態成員和執行個體成員。

[!code-csharp[Entity](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L16-L36)]

每個`Entity`實例都包含一個序號（大概還有一些此處未顯示的其他資訊）。 `Entity` 建構函式 (類似於執行個體方法) 會將具有下一個可用序號的新執行個體初始化。 由於建構函式是實例成員，因此允許訪問`serialNo`實例欄位和`nextSerialNo`靜態欄位。

`GetNextSerialNo` 和 `SetNextSerialNo` 靜態方法可以存取 `nextSerialNo` 靜態欄位，但如果直接存取 `serialNo` 執行個體欄位，則會產生錯誤。

下列範例示範 Entity 類別的用法。

[!code-csharp[EntityExample](~/samples/snippets/csharp/tour/classes-and-objects/Entity.cs#L3-L15)]

在`SetNextSerialNo`類`GetNextSerialNo`上調用 和 靜態方法，而`GetSerialNo`實例方法在類的實例上調用。

### <a name="virtual-override-and-abstract-methods"></a>虛擬、覆寫及抽象方法

當執行個體方法宣告包含 `virtual` 修飾詞時，該方法即稱為「虛擬方法」**。 當沒有任何 virtual 修飾詞存在時，該方法則稱為「非虛擬方法」**。

叫用虛擬方法時，叫用所針對之執行個體的「執行階段型別」** 會決定要叫用的實際方法實作。 在非虛擬方法叫用中，決定因素則是執行個體的「編譯階段型別」**。

在衍生類別中可以「覆寫」** 虛擬方法。 當執行個體方法宣告包含 override 修飾詞時，該方法會覆寫具有相同簽章的已繼承虛擬方法。 虛擬方法宣告會導入新的方法，而覆寫方法宣告則是會提供現有已繼承之虛擬方法的新實作，來將該方法特製化。

「抽象方法」** 係指不含實作的虛擬方法。 宣告抽象方法時，是使用 abstract 修飾詞，並且只有在同樣宣告為抽象的類別中，才能宣告抽象方法。 抽象方法必須在每個非抽象的衍生類別中被覆寫。

下列範例會宣告一個抽象類別 `Expression` 和三個衍生的類別 `Constant`、`VariableReference` 及 `Operation`，前者代表一個運算式樹狀架構節點，後者則會實作常數、變數參考及算數運算式的運算式樹狀架構節點。 （此示例類似于，但不得與運算式樹類型混淆）。

[!code-csharp[ExpressionClass](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L3-L61)]

先前的四個類別可用來建構算數運算式的模型。 例如，在使用這些類別執行個體的情況下，可以將運算式 `x + 3` 表示如下。

[!code-csharp[ExpressionExample](~/samples/snippets/csharp/tour/classes-and-objects/Program.cs#L40-L43)]

系統會叫用 `Expression` 執行個體的 `Evaluate` 方法來評估指定的運算式並產生 `double` 值。 此方法會採用包含變數名稱 (作為項目的索引鍵) 和值 (作為項目的值) 的 `Dictionary` 引數。 因為 `Evaluate` 是一種抽象方法，所以衍生自 `Expression` 的非抽象類別必須覆寫 `Evaluate`。

`Constant` 的 `Evaluate` 實作會直接傳回預存的常數。 `VariableReference` 的實作會查詢字典中的變數名稱並傳回產生的值。 `Operation` 的實作會先評估左邊和右邊的運算元 (透過以遞迴方式叫用其 `Evaluate` 方法)，然後才執行指定的算數運算。

下列程式會使用 `Expression` 類別來評估不同 `x` 和 `y` 值的 `x * (y + 2)` 運算式。

[!code-csharp[ExpressionUsage](~/samples/snippets/csharp/tour/classes-and-objects/Expressions.cs#L66-L89)]

### <a name="method-overloading"></a>方法多載

方法「多載」** 可允許相同類別中的多個方法擁有相同的名稱，只要它們的簽章是唯一的即可。 編譯多載方法的叫用時，編譯器會使用「多載解析」** 來判斷要叫用的特定方法。 多載解析會尋找一個與引數最相符的方法，或者，如果找不到任何一個最相符的方法，則會回報錯誤。 下列範例示範多載解析的實際運作情況。 方法中每個調用的`UsageExample`注釋顯示調用的方法。

[!code-csharp[OverloadUsage](~/samples/snippets/csharp/tour/classes-and-objects/Overloading.cs#L3-L41)]

如範例所示，透過將引數明確轉換成確切的參數型別和 (或) 明確提供型別引數，即一律可以選取特定的方法。

## <a name="other-function-members"></a>其他函式成員

包含可執行程式碼的成員統稱為類別的「函式成員」**。 上一節介紹方法，這些方法是函數成員的主要類型。 本節將說明 C# 所支援的其他函式成員類型：建構函式、屬性、索引子、事件、運算子及完成項。

下面的示例顯示了一個稱為 的`MyList<T>`泛型類，它實現了可增長的物件清單。 此類別包含數個最常見的函式成員類型。

> [!NOTE]
> 這個範例會建立一個 `MyList` 類別，這和 .NET 標準 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 不同。 它會說明此教學課程所需的概念，但不是該類別的取代項目。

[!code-csharp[ListClass](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L4-L89)]

### <a name="constructors"></a>建構函式

C# 同時支援執行個體建構函式和靜態建構函式。 「執行個體建構函式」** 是實作將類別執行個體初始化所需之動作的成員。 *靜態建構函式*是實現在第一次載入類本身時實現初始化類本身所需的操作的成員。

建構函式的宣告方式與方法類似，但不含傳回型別且名稱會與包含它的類別相同。 如果建構函式宣告包含 static 修飾詞，則所宣告的就是靜態建構函式。 否則，所宣告的會是執行個體建構函式。

執行個體建構函式可以多載，且可以具有選擇性參數。 例如，`MyList<T>` 類別會使用單一選擇性 `int` 參數來宣告一個執行個體建構函式。 叫用執行個體建構函式時，是使用 `new` 運算子來叫用。 下列陳述式會使用 `MyList` 類別的建構函式搭配或不搭配選用的引數來配置兩個 `MyList<string>` 執行個體。

[!code-csharp[ListExample1](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L95-L96)]

與其他成員不同，實例建構函式不是繼承的，並且類除了在類中實際聲明的建構函式之外，沒有其他實例建構函式。 如果沒有為類別提供任何執行個體建構函式，則會自動提供一個沒有任何參數的空建構函式。

### <a name="properties"></a>屬性

「屬性」** 是欄位的自然延伸。 兩者都是具有關聯型別的具名成員，並且用來存取欄位和屬性的語法是相同的。 但是，與欄位不同，屬性不表示存儲位置。 取而代之的是，屬性會有「存取子」**，這些存取子會指定讀取或寫入其值時要執行的陳述式。

屬性的宣告方式與欄位類似，不同之處在於宣告會以在 `{` 與 `}` 分隔符號之間撰寫的 get 存取子和 (或) set 存取子作為結尾，而不是以分號作為結尾。 同時具有 get 存取子和 set 存取子的屬性是「讀寫屬性」**，只有 get 存取子的屬性是「唯讀屬性」**，而只有 set 存取子的屬性則是「唯寫屬性」**。

get 存取子會與傳回值屬於屬性型別的無參數方法對應。 除了作為指派目標的情況以外，在運算式中參考屬性時，會叫用屬性的 get 存取子來計算屬性的值。

set 存取子會與具有單一參數具名值且沒有任何傳回型別的方法對應。 將屬性作為指派目標或是作為 ++ 或 -- 的運算元來參考時，會以提供新值的引數來叫用 set 存取子。

`MyList<T>` 類別會宣告 `Count` 和 `Capacity` 這兩個屬性，它們分別是唯讀屬性和讀寫屬性。 以下代碼是使用這些屬性的示例：

[!code-csharp[ListExample2](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L101-L104)]

與欄位和方法類似，C# 也同時支援執行個體屬性和靜態屬性。 宣告靜態屬性時，是使用 static 修飾詞來宣告，而宣告執行個體屬性時，則不使用該修飾詞。

屬性的存取子可以是虛擬的。 當屬性宣告包含 `virtual`、`abstract` 或 `override` 修飾詞時，會套用至該屬性的存取子。

### <a name="indexers"></a>索引子

「索引子」** 是可讓物件以和陣列相同的方式進行索引編製的成員。 索引子的宣告方式與屬性類似，不同之處在於成員的名稱是 `this`，後面接著在 `[` 與 `]` 分隔符號之間撰寫的參數清單。 索引子的存取子中會提供參數。 與屬性類似，索引子可以是讀寫、唯讀及唯寫的，而索引子的存取子可以是虛擬的。

`MyList<T>` 類別會宣告一個採用 `int` 參數的單一讀寫索引子。 此索引子使得系統能夠以 `int` 值編製 `MyList<T>` 執行個體的索引。 例如：

[!code-csharp[ListExample3](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L109-L117)]

索引子可被多載，這意謂著類別可以宣告多個索引子，只要其參數的號碼或型別不同即可。

### <a name="events"></a>事件

「事件」** 是可讓類別或物件提供通知的成員。 事件的宣告方式與欄位類似，不同之處在於其宣告包含事件關鍵字，並且型別必須是委派型別。

在聲明事件成員的類中，事件的作用類似于委託類型的欄位（前提是事件不是抽象的，並且不聲明訪問者）。 欄位會儲存對委派項目的參考，該委派項目代表已新增到事件中的事件處理常式。 如果沒有任何事件處理常式存在，欄位就會是 `null`。

`MyList<T>` 類別會宣告一個名為 `Changed` 的單一事件成員，此成員會指出新項目已新增到清單中。 Changed 事件是由 `OnChanged` 虛擬方法所引發，此方法會先檢查事件是否為 `null` (意謂著沒有任何處理常式存在)。 引發事件的概念完全等同於叫用該事件所代表的委派項目，因此，就引發事件而言，並沒有任何特殊的語言建構。

用戶端是透過「事件處理常式」** 來對事件進行反應。 附加事件處理常式時，是使用 `+=` 運算子，移除時，則是使用 `-=` 運算子。 下列範例會將事件處理常式附加到 `MyList<string>` 的 `Changed` 事件。

[!code-csharp[EventExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L132-L148)]

對於需要控制事件基礎存儲的高級方案，事件聲明可以顯式提供`add`和`remove`訪問者，這與屬性的訪問器類似。 `set`

### <a name="operators"></a>操作員

「運算子」** 是定義將特定運算式運算子套用到類別執行個體之意義的成員。 可定義的運算子有三種：一元運算子、二元運算子及轉換運算子。 所有運算子都必須宣告為 `public` 和 `static`。

`MyList<T>` 類別會宣告 `operator ==` 和 `operator !=` 這兩個運算子，藉此賦予將這些運算子套用到 `MyList` 執行個體的運算式新意義。 具體而言，運算子會將兩個 `MyList<T>` 執行個體的等號比較定義為使用其 Equals 方法來比較所含的每個物件。 下列範例會使用 `==` 運算子來比較兩個 `MyList<int>` 執行個體。

[!code-csharp[OperatorExample](~/samples/snippets/csharp/tour/classes-and-objects/ListBasedExamples.cs#L121-L129)]

第一個 `Console.WriteLine` 會輸出 `True`，因為兩個清單所包含物件的數目相同、值相同且順序相同。 如果 `MyList<T>` 並未定義 `operator ==`，則第一個 `Console.WriteLine` 所輸出的會是 `False`，因為 `a` 和 `b` 參考不同的 `MyList<int>` 執行個體。

### <a name="finalizers"></a>完成項

「完成項」** 是實作將類別執行個體完成所需之動作的成員。 終端子不能具有參數，它們不能具有協助工具修改器，也不能顯式調用它們。 系統會在記憶體回收期間自動叫用執行個體的完成項。

記憶體回收行程有相當大的自由來決定何時回收物件並執行完成項。 具體而言，終端子調用的時間不是確定性的，可以在任何執行緒上執行終端子。 基於這些及其他理由，類別應該只有在沒有任何其他解決方案可行時，才實作完成項。

`using` 陳述式提供較佳的物件解構方法。

> [!div class="step-by-step"]
> [上一個](statements.md)
> [下一個](arrays.md)
