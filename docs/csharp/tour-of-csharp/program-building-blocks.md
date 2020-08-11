---
title: 'C # 程式的建立區塊」'
description: '瞭解 c # 成員、運算式和語句。 類型包含您撰寫的成員。 這些成員是由語句和運算式所建立。'
ms.date: 08/06/2020
ms.openlocfilehash: de9f634db129ea2ec6f692cabb657f9fe41b2f9c
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88068530"
---
# <a name="program-building-blocks"></a>程式建立區塊

前一篇文章中所述的型別是使用下列構成要素來建立的：[***成員***](../programming-guide/classes-and-structs/members.md)、 [***運算式***和***語句***](../programming-guide/statements-expressions-operators/index.md)。

## <a name="members"></a>成員

的成員 `class` 可以是***靜態成員***或***實例成員***。 靜態成員隸屬於類別，而執行個體成員則隸屬於物件 (類別的執行個體)。

下列清單提供類別可以包含的成員種類總覽。

- **常數**：與類別相關聯的常數值
- **欄位**：與類別相關聯的變數
- **方法**：可由類別執行的動作
- **屬性**：與讀取和寫入類別的命名屬性相關聯的動作
- **索引子**：與類別的實例建立關聯的動作，例如陣列
- **事件**：可由類別產生的通知
- **運算子**：類別支援的轉換和運算式運算子
- **析構**函式：初始化類別或類別本身的實例時所需的動作
- 完成**項：在**類別的實例永久捨棄之前執行的動作
- **類型**：類別所宣告的巢狀型別

## <a name="accessibility"></a>協助工具選項

類別的每個成員都有相關聯的存取範圍，可控制可以存取成員的程式文字區域。 存取能力有六種可能的形式。 以下摘要說明存取修飾詞。

- `public`：存取不受限制。
- `private`：存取僅限於此類別。
- `protected`：存取僅限於此類別或衍生自此類別的類別。
- `internal`：存取限制為目前的元件 (`.exe` 或 `.dll`) 。
- `protected internal`：存取僅限於此類別、衍生自這個類別的類別，或相同元件中的類別。
- `private protected`：存取限於這個類別，或在相同元件中從這個類型衍生的類別。

## <a name="fields"></a>欄位

「欄位」** 是與類別或類別執行個體關聯的變數。

使用 static 修飾詞來宣告的欄位會定義靜態欄位。 靜態欄位只會識別一個儲存位置。 無論建立多少個類別實例，都只會有一個靜態欄位複本。

未使用 static 修飾詞來宣告的欄位會定義執行個體欄位。 每個類別執行個體都包含一個該類別所有執行個體欄位的個別複本。

在下列範例中，類別的每個實例 `Color` 都有 `r` 、 `g` 和實例欄位的個別複本 `b` ，但只有一個 `Black` 、 `White` 、、 `Red` `Green` 及 `Blue` 靜態欄位的複本：

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ColorClassDefinition":::

如先前的範例所示，可以使用 `readonly` 修飾詞來宣告「唯讀欄位」**。 指派至唯讀欄位只會當做欄位宣告的一部分，或在相同類別的函式中發生。

## <a name="methods"></a>方法

「方法」** 是實作物件或類別所能執行之計算或動作的成員。 存取「靜態方法」** 時，是透過類別來存取。 存取「執行個體方法」** 時，是透過類別的執行個體來存取。

方法可能會有一份*參數*清單，其中代表傳遞至方法的值或變數參考。 方法具有傳回*型*別，它會指定方法所計算和傳回的值型別。 如果方法的傳回型別不會傳回值，則為 `void` 。

與型別相同，方法也可能有一組型別參數，而呼叫方法時，必須為這些參數指定型別引數。 與型別不同的是，型別引數通常可以從方法呼叫的引數推斷，而不需要明確指定。

在宣告方法的類別中，方法的「簽章」** 必須是唯一的。 方法的簽章包含方法的名稱、型別參數的數目，以及其參數的數目、修飾詞和類型。 方法的簽章不包含傳回型別。

當方法主體是單一運算式時，可以使用 compact 運算式格式來定義方法，如下列範例所示：

```csharp
public override ToString() => "This is an object";
```

### <a name="parameters"></a>參數

參數是用來將值或變數參考傳遞給方法。 方法的參數會從叫用方法時所指定的「引數」** 取得其實際值。 參數有四種：值參數、參考參數、輸出參數，以及參數陣列。

「值參數」** 適用於傳遞輸入引數。 值參數會對應至區域變數，此變數會從針對參數傳遞的引數取得其初始值。 值參數的修改不會影響針對參數傳遞的引數。

只要指定預設值，值參數便可以成為選用參數，如此即可省略對應的引數。

「參考參數」** 適用於以參考方式傳遞引數。 針對參考參數傳遞的引數必須是具有明確值的變數。 在方法執行期間，參考參數會代表與引數變數相同的儲存位置。 宣告參考參數時，是使用 `ref` 修飾詞來宣告。 下列範例示範 `ref` 參數的用法。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="RefExample":::

「輸出參數」** 適用於以參考方式傳遞引數。 其類似於參考參數，只不過它並不需要您明確指派值給呼叫端提供的引數。 宣告輸出參數時，是使用 `out` 修飾詞來宣告。 下列範例示範如何使用 C# 7 中所引入的語法來利用 `out` 參數。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="OutExample":::

「參數陣列」** 可允許將數目不固定的引數傳遞給方法。 宣告參數陣列時，是使用 `params` 修飾詞來宣告。 只有方法的最後一個參數可以是參數陣列，而參數陣列的型別必須是單一維度陣列型別。 `Write`類別的和 `WriteLine` 方法 <xref:System.Console?displayProperty=nameWithType> 是參數陣列使用方式的良好範例。 這些宣告如下所示。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ConsoleExtract":::

在使用參數陣列的方法內，參數陣列的行為與陣列型別的一般參數完全相同。 不過，在具有參數陣列的方法調用中，可以傳遞參數陣列類型的單一引數，或參數陣列的元素類型的任何引數數目。 在後者的案例中，會自動建立陣列執行個體並以指定的引數將其初始化。 以下範例

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UseParamsArgs":::

等同於撰寫下列程式碼。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="CompilerParams":::

### <a name="method-body-and-local-variables"></a>方法主體和區域變數

方法的主體會指定叫用方法時所要執行的陳述式。

方法主體可以宣告方法叫用專屬的變數。 這類變數稱為「區域變數」**。 區域變數宣告會指定型別名稱、變數名稱，還可能指定初始值。 下列範例會宣告一個初始值為零的區域變數 `i`，以及一個沒有初始值的區域變數 `j`。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="SquaresClass":::

C# 要求必須「明確指派」** 區域變數，才能取得其值。 例如，如果先前的宣告 `i` 未包含初始值，則編譯器會針對後面的使用方式報告錯誤， `i` 因為 `i` 不會在程式中的那些點上明確指派。

方法可以使用 `return` 陳述式將控制權交還給其呼叫端。 在傳回的方法中 `void` ， `return` 語句不能指定運算式。 在傳回非 void 的方法中，`return` 陳述式必須包含會計算傳回值的運算式。

### <a name="static-and-instance-methods"></a>靜態和執行個體方法

使用修飾詞宣告的方法 `static` 是*靜態方法*。 靜態方法不會在特定的實例上運作，而且只能直接存取靜態成員。

未使用修飾詞宣告的方法 `static` 是*實例方法*。 執行個體方法會在特定的執行個體上運作，並且既可存取靜態成員也可存取執行個體成員。 透過 `this` 可以明確存取叫用執行個體方法時所在的執行個體。 `this`在靜態方法中參考是錯誤的。

下列 `Entity` 類別同時含有靜態成員和執行個體成員。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="EntityClass":::

每個 `Entity` 實例都包含一個序號 (，而且有一些不會顯示在這裡) 的其他資訊。 `Entity` 建構函式 (類似於執行個體方法) 會將具有下一個可用序號的新執行個體初始化。 因為此函式是實例成員，所以允許它存取 `_serialNo` 實例欄位和 `s_nextSerialNo` 靜態欄位。

`GetNextSerialNo` 和 `SetNextSerialNo` 靜態方法可以存取 `s_nextSerialNo` 靜態欄位，但如果直接存取 `_serialNo` 執行個體欄位，則會產生錯誤。

下列範例示範如何使用 `Entity` 類別。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UsingEntity":::

`SetNextSerialNo`和 `GetNextSerialNo` 靜態方法會在類別上叫用，而 `GetSerialNo` 實例方法則是在類別的實例上叫用。

### <a name="virtual-override-and-abstract-methods"></a>虛擬、覆寫及抽象方法

當執行個體方法宣告包含 `virtual` 修飾詞時，該方法即稱為「虛擬方法」**。 當沒有任何 virtual 修飾詞存在時，該方法則稱為「非虛擬方法」**。

叫用虛擬方法時，叫用所針對之執行個體的「執行階段型別」** 會決定要叫用的實際方法實作。 在非虛擬方法叫用中，決定因素則是執行個體的「編譯階段型別」**。

在衍生類別中可以「覆寫」** 虛擬方法。 當執行個體方法宣告包含 override 修飾詞時，該方法會覆寫具有相同簽章的已繼承虛擬方法。 Aa 虛擬方法宣告引進了新的方法。 覆寫方法宣告會藉由提供該方法的新實作為，專門用現有的繼承虛擬方法。

「抽象方法」** 係指不含實作的虛擬方法。 抽象方法是使用修飾詞來宣告 `abstract` ，而且只允許用於抽象類別。 抽象方法必須在每個非抽象的衍生類別中被覆寫。

下列範例會宣告一個抽象類別 `Expression` 和三個衍生的類別 `Constant`、`VariableReference` 及 `Operation`，前者代表一個運算式樹狀架構節點，後者則會實作常數、變數參考及算數運算式的運算式樹狀架構節點。  (此範例類似，但與運算式樹狀架構類型無關) 。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="WorkingWithExpressions":::

先前的四個類別可用來建構算數運算式的模型。 例如，在使用這些類別執行個體的情況下，可以將運算式 `x + 3` 表示如下。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UseExpressions":::

系統會叫用 `Expression` 執行個體的 `Evaluate` 方法來評估指定的運算式並產生 `double` 值。 此方法會採用包含變數名稱 (作為項目的索引鍵) 和值 (作為項目的值) 的 `Dictionary` 引數。 因為 `Evaluate` 是一種抽象方法，所以衍生自 `Expression` 的非抽象類別必須覆寫 `Evaluate`。

`Constant` 的 `Evaluate` 實作會直接傳回預存的常數。 `VariableReference` 的實作會查詢字典中的變數名稱並傳回產生的值。 `Operation` 的實作會先評估左邊和右邊的運算元 (透過以遞迴方式叫用其 `Evaluate` 方法)，然後才執行指定的算數運算。

下列程式會使用 `Expression` 類別來評估不同 `x` 和 `y` 值的 `x * (y + 2)` 運算式。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="UsingExpressions":::

### <a name="method-overloading"></a>方法多載

方法「多載」** 可允許相同類別中的多個方法擁有相同的名稱，只要它們的簽章是唯一的即可。 編譯多載方法的叫用時，編譯器會使用「多載解析」** 來判斷要叫用的特定方法。 多載解析會尋找最符合引數的方法。 如果找不到單一最佳相符項，則會報告錯誤。 下列範例示範多載解析的實際運作情況。 方法中每個調用的批註 `UsageExample` 會顯示叫用的方法。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="Overloading":::

如範例所示，您一定可以明確地將引數轉換成確切的參數類型和類型引數，藉以選取特定的方法。

## <a name="other-function-members"></a>其他函式成員

包含可執行程式碼的成員統稱為類別的「函式成員」**。 上一節描述方法，這是函數成員的主要類型。 本節將說明 C# 所支援的其他函式成員類型：建構函式、屬性、索引子、事件、運算子及完成項。

下列範例示範名為的泛型類別 `MyList<T>` ，它會執行物件的可成長清單。 此類別包含數個最常見的函式成員類型。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListExample":::

### <a name="constructors"></a>建構函式

C# 同時支援執行個體建構函式和靜態建構函式。 「執行個體建構函式」** 是實作將類別執行個體初始化所需之動作的成員。 *靜態*的函式是一個成員，它會在第一次載入時，執行初始化類別本身所需的動作。

建構函式的宣告方式與方法類似，但不含傳回型別且名稱會與包含它的類別相同。 如果函式宣告包含修飾詞 `static` ，則會宣告靜態的函式。 否則，所宣告的會是執行個體建構函式。

執行個體建構函式可以多載，且可以具有選擇性參數。 例如，`MyList<T>` 類別會使用單一選擇性 `int` 參數來宣告一個執行個體建構函式。 叫用執行個體建構函式時，是使用 `new` 運算子來叫用。 下列陳述式會使用 `MyList` 類別的建構函式搭配或不搭配選用的引數來配置兩個 `MyList<string>` 執行個體。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="CreateLists":::

不同于其他成員，實例的構造函式不會繼承。 類別沒有任何實例的函式，而不是在類別中實際宣告的那些函數。 如果沒有為類別提供任何執行個體建構函式，則會自動提供一個沒有任何參數的空建構函式。

### <a name="properties"></a>屬性

「屬性」** 是欄位的自然延伸。 兩者都是具有關聯型別的具名成員，並且用來存取欄位和屬性的語法是相同的。 不過，與欄位不同的是，屬性不代表儲存位置。 相反地，屬性具有可指定讀取或寫入其值時所執行之語句的*存取*子。

屬性的宣告方式與欄位類似，不同之處在于宣告的結尾是 get 存取子，或是在分隔符號之間寫入的 set 存取子， `{` `}` 而不是以分號結尾。 同時具有 get 存取子和 set 存取子的屬性是「讀寫屬性」**，只有 get 存取子的屬性是「唯讀屬性」**，而只有 set 存取子的屬性則是「唯寫屬性」**。

get 存取子會與傳回值屬於屬性型別的無參數方法對應。 set 存取子會與具有單一參數具名值且沒有任何傳回型別的方法對應。 Get 存取子會計算屬性的值。 Set 存取子會為屬性提供新的值。 當屬性是指派的目標，或是或的運算元時 `++` `--` ，就會叫用 set 存取子。 在參考屬性的其他情況下，會叫用 get 存取子。

 將屬性作為指派目標或是作為 ++ 或 -- 的運算元來參考時，會以提供新值的引數來叫用 set 存取子。

`MyList<T>` 類別會宣告 `Count` 和 `Capacity` 這兩個屬性，它們分別是唯讀屬性和讀寫屬性。 下列程式碼是使用這些屬性的範例：

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="AccessProperties":::

與欄位和方法類似，C# 也同時支援執行個體屬性和靜態屬性。 宣告靜態屬性時，是使用 static 修飾詞來宣告，而宣告執行個體屬性時，則不使用該修飾詞。

屬性的存取子可以是虛擬的。 當屬性宣告包含 `virtual`、`abstract` 或 `override` 修飾詞時，會套用至該屬性的存取子。

### <a name="indexers"></a>索引子

「索引子」** 是可讓物件以和陣列相同的方式進行索引編製的成員。 索引子的宣告方式與屬性類似，不同之處在於成員的名稱是 `this`，後面接著在 `[` 與 `]` 分隔符號之間撰寫的參數清單。 索引子的存取子中會提供參數。 與屬性類似，索引子可以是讀寫、唯讀及唯寫的，而索引子的存取子可以是虛擬的。

`MyList<T>` 類別會宣告一個採用 `int` 參數的單一讀寫索引子。 此索引子使得系統能夠以 `int` 值編製 `MyList<T>` 執行個體的索引。 例如：

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListAddition":::

索引子可以多載。 類別可以宣告多個索引子，只要其參數的數目或類型不同。

### <a name="events"></a>事件

「事件」** 是可讓類別或物件提供通知的成員。 事件的宣告方式與欄位類似，不同之處在于宣告包含 `event` 關鍵字，而類型必須是委派類型。

在宣告事件成員的類別中，事件的行為就像委派類型的欄位一樣， (前提是事件不是抽象的，而且不會宣告存取子) 。 欄位會儲存對委派項目的參考，該委派項目代表已新增到事件中的事件處理常式。 如果沒有任何事件處理常式存在，欄位就會是 `null`。

`MyList<T>` 類別會宣告一個名為 `Changed` 的單一事件成員，此成員會指出新項目已新增到清單中。 Changed 事件是由 `OnChanged` 虛擬方法所引發，此方法會先檢查事件是否為 `null` (意謂著沒有任何處理常式存在)。 引發事件的概念相當於叫用事件所表示的委派。 沒有用於引發事件的特殊語言結構。

用戶端是透過「事件處理常式」** 來對事件進行反應。 附加事件處理常式時，是使用 `+=` 運算子，移除時，則是使用 `-=` 運算子。 下列範例會將事件處理常式附加到 `MyList<string>` 的 `Changed` 事件。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="RespondToEvents":::

針對需要控制事件之基礎儲存的高階案例，事件宣告可以明確提供 `add` 和 `remove` 存取子，類似于 `set` 屬性的存取子。

### <a name="operators"></a>運算子

「運算子」** 是定義將特定運算式運算子套用到類別執行個體之意義的成員。 可定義的運算子有三種：一元運算子、二元運算子及轉換運算子。 所有運算子都必須宣告為 `public` 和 `static`。

類別會宣告 `MyList<T>` 和這兩個運算子 `operator ==` `operator !=` 。 這些覆寫的運算子會對將這些運算子套用至實例的運算式提供新意義 `MyList` 。 具體而言，運算子會 `MyList<T>` 使用其方法來比較所包含的每個物件，以定義兩個實例是否相等 `Equals` 。 下列範例會使用 `==` 運算子來比較兩個 `MyList<int>` 執行個體。

:::code language="csharp" source="./snippets/shared/ClassesObjects.cs" ID="ListAddition":::

第一個 `Console.WriteLine` 會輸出 `True`，因為兩個清單所包含物件的數目相同、值相同且順序相同。 如果 `MyList<T>` 並未定義 `operator ==`，則第一個 `Console.WriteLine` 所輸出的會是 `False`，因為 `a` 和 `b` 參考不同的 `MyList<int>` 執行個體。

### <a name="finalizers"></a>完成項

「完成項」** 是實作將類別執行個體完成所需之動作的成員。 通常需要完成項才能釋放非受控資源。 完成項不能有參數，它們不能有存取範圍修飾詞，因此無法明確叫用。 系統會在記憶體回收期間自動叫用執行個體的完成項。 如需詳細資訊，請參閱完成[項的](../programming-guide/classes-and-structs/destructors.md)相關文章。

記憶體回收行程有相當大的自由來決定何時回收物件並執行完成項。 具體而言，完成項調用的時機並不具決定性，而完成項可能會在任何執行緒上執行。 基於這些及其他理由，類別應該只有在沒有任何其他解決方案可行時，才實作完成項。

`using` 陳述式提供較佳的物件解構方法。

## <a name="expressions"></a>運算式

「運算式」** 是由「運算元」** 和「運算子」** 建構而成。 運算式的運算子會指出要將哪些運算套用到運算元。 運算子範例包括 `+`、`-`、`*`、`/` 及 `new`。 運算元範例包括常值、欄位、區域變數及運算式。

當運算式包含多個運算子時，運算子的「優先順序」會控制個別運算子的評估順序。 例如，運算式 `x + y * z` 會評估為 `x + (y * z)`，因為 `*` 運算子的優先順序高於 `+` 運算子。

當兩個優先順序相同的運算子之間有運算元時，運算子的「關聯性」** 會控制執行運算的順序：

* 除了指派和 null 聯合運算子之外，所有二元運算子都是*左關聯*的，這表示作業是由左至右執行。 例如，`x + y + z` 會判斷值為 `(x + y) + z`。
* 指派運算子、null `??` `??=` 聯合和運算子，以及條件運算子 `?:` 是*右向關聯*，這表示作業是由右至左執行。 例如，`x = y = z` 會判斷值為 `x = (y = z)`。

您可以使用括弧來控制優先順序和關聯性。 例如，`x + y * z` 會先將 `y` 乘以 `z`，然後再將結果加到 `x`，而 `(x + y) * z` 則會先將 `x` 與 `y` 相加，然後再將結果乘以 `z`。

大部分的運算子都可以[「多載」**](../language-reference/operators/operator-overloading.md)。 運算子多載可允許針對一個運算元屬於 (或兩個運算元都屬於) 使用者定義之類別或結構型別的運算式，指定使用者定義的運算子實作。

C# 提供數個運算子，用於執行[算術](../language-reference/operators/arithmetic-operators.md)、[邏輯](../language-reference/operators/boolean-logical-operators.md)、[位元和移位](../language-reference/operators/bitwise-and-shift-operators.md)作業以及[相等](../language-reference/operators/equality-operators.md)和[順序](../language-reference/operators/comparison-operators.md)比較。

如需按優先順序層級排序的 C# 運算子完整清單，請參閱 [C# 運算子](../language-reference/operators/index.md)。

## <a name="statements"></a>陳述式

程式的動作是藉由*陳述式*來表達。 C# 支援數種不同類型的陳述式，其中一些是以內嵌陳述式來定義。

- 「區塊」** 可允許在許可單一陳述式的內容中撰寫多個陳述式。 區塊是由在 `{` 與 `}` 分隔符號之間撰寫的陳述式清單所組成。
- 「宣告陳述式」** 可用來宣告區域變數和常數。
- 「運算式陳述式」** 可用來評估運算式。 可用來作為陳述式的運算式包括方法叫用、使用 `new` 運算子的物件配置、使用 `=` 和複合指派運算子的指派、使用 `++` 和 `--` 運算子的遞增和遞減運算，以及 `await` 運算。
- 「選取範圍陳述式」** 可用來選取一些可能陳述式的其中之一，以根據某個運算式的值來執行。 此群組包含 `if` 和 `switch` 語句。
- 「反覆運算陳述式」** 可用來重複執行內嵌的陳述式。 此群組包含 `while` 、 `do` 、 `for` 和 `foreach` 語句。
- 「跳躍陳述式」** 可用來轉移控制項。 此群組包含 `break` 、 `continue` 、 `goto` 、 `throw` 、 `return` 和 `yield` 語句。
- `try`...`catch` 陳述式可用來攔截在執行區塊時發生的例外狀況，而 `try`...`finally` 陳述式則可用來指定不論是否發生例外狀況都一律會執行的最終處理程式碼。
- `checked` 和 `unchecked` 陳述式可用來控制整數型別算術運算和轉換的溢位檢查內容。
- `lock` 陳述式可用來取得所指定物件的互斥鎖定、執行陳述式，然後釋放鎖定。
- `using` 陳述式可用來取得資源、執行陳述式，然後處置該資源。

以下列出可以使用的語句種類：

* 區域變數宣告。
* 區域常數宣告。
* Expression 語句。
* `if`句.
* `switch`句.
* `while`句.
* `do`句.
* `for`句.
* `foreach`句.
* `break`句.
* `continue`句.
* `goto`句.
* `return`句.
* `yield`句.
* `throw`語句和 `try` 語句。
* `checked`和 `unchecked` 語句。
* `lock`句.
* `using`句.

>[!div class="step-by-step"]
>[上一個](types.md) 
>[下一步](features.md)
