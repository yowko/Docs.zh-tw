---
title: C# 的教學課程 - C# 指南
description: 第一次接觸 C#？ 了解該語言的基本概念。
ms.date: 08/06/2020
ms.openlocfilehash: 9fa292e8e85832d831f36cf0f21512aa0cf32580
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656224"
---
# <a name="a-tour-of-the-c-language"></a>C # 語言教學課程

C # (發音為「看清晰的」 ) 是新式、物件導向且型別安全的程式設計語言。 C# 源自於是 C 系列語言，使用 C、C++、Java 和 JavaScript 的程式設計人員會立即感到熟悉。 本教學課程概要說明 c # 8 和更早版本中語言的主要元件。 如果您想要透過互動式範例探索語言，請嘗試 [c #](../tutorials/intro-to-csharp/index.md) 教學課程簡介。

C # 是物件導向、 ***元件導向*** 的程式設計語言。 C # 提供語言結構來直接支援這些概念，讓 c # 成為用來建立和使用軟體元件的自然語言。 自其來源起，c # 已新增功能，以支援新的工作負載和新興的軟體設計作法。

有數種 c # 功能有助於穩固且持久的應用程式的結構。 [***垃圾收集***](../../standard/garbage-collection/index.md) 會自動回收無法存取未使用的物件所佔用的記憶體。 [***例外狀況處理***](../programming-guide/exceptions/index.md) 可提供結構化且可擴充的方法來偵測和復原錯誤。 [***Lambda 運算式***](../language-reference/operators/lambda-expressions.md) 支援功能性程式設計技術。 [***查詢語法***](../linq/index.md) 會建立一般模式，以處理來自任何來源的資料。 [***非同步作業***](../programming-guide/concepts/async/index.md)的語言支援提供建立分散式系統的語法。 [***模式***](..//pattern-matching.md) 比對會提供語法，讓您輕鬆地將資料與新式分散式系統中的演算法分隔開來。 C # 具有 [***統一的類型系統***](../programming-guide/types/index.md)。 所有的 C# 型別 (包括 `int` 和 `double` 等基本型別) 都繼承自單一的 `object` 根型別。 所有類型都共用一組常見的作業。 任何型別的值都可以透過一致的方式來儲存、傳輸和操作。 此外，c # 也支援使用者定義的參考型別和實數值型別。 C # 允許動態設定物件和輕量結構的內嵌儲存體。

C # 強調 ***版本控制*** ，以確保程式和程式庫能夠以相容的方式在一段時間內演進。 C # 的設計方面，直接受到版本控制考慮的影響包括個別 `virtual` 和修飾詞 `override` 、方法多載解析的規則，以及對明確介面成員宣告的支援。

## <a name="hello-world"></a>Hello World

“Hello, World” 程式通常用來介紹程式設計語言。 以下是以 C# 撰寫的：

:::code language="csharp" interactive="try-dotnet" source="./snippets/shared/HelloWorld.cs":::

“Hello, World” 程式的開頭為 `using` 指示詞，會參考 `System` 命名空間。 命名空間提供組織 C# 程式和程式庫的階層式方法。 命名空間包含型別和其他命名空間，例如 `System` 命名空間包含數個型別 (如程式中參考的 `Console` 類別)，和數個其他命名空間 (如 `IO` 和 `Collections`)。 使用 `using` 指示詞參考指定的命名空間，就能以非限定的方式使用屬於該命名空間成員的型別。 因為 `using` 指示詞的緣故，該程式可以使用 `Console.WriteLine` 當作 `System.Console.WriteLine` 的縮寫。

“Hello, World” 程式宣告的 `Hello` 類別包含單一成員，即名為 `Main` 的方法。 `Main`使用修飾詞宣告方法 `static` 。 執行個體方法可以使用關鍵字 `this` 參考特定的封入物件執行個體，但靜態方法卻不需要參考特定物件即可運作。 依照慣例，名為的靜態方法可 `Main` 作為 c # 程式的進入點。

程式的輸出是由 `System` 命名空間中 `Console` 類別的 `WriteLine` 方法產生。 此類別是由標準類別程式庫提供，根據預設，編譯器會自動參考此程式庫。

## <a name="types-and-variables"></a>型別與變數

C# 中有兩種型別：*實值型別*和*參考型別*。 實值型別的變數直接包含其資料，而參考型別的變數則將參考儲存到其資料，後者即是物件。 使用參考型別時，可能會有兩個變數參考相同的物件，而且對某個變數進行的作業可能會影響另一個變數所參考的物件。 使用實值型別時，每個變數都有自己的資料複本，而且在一個上進行的作業不可能會影響其他 (`ref` 但 `out`) 的和參數變數。

***識別碼***是變數名稱。 識別碼是 unicode 字元序列，不含任何空白。 如果識別碼前面加上，則識別碼可以是 c # 保留字 `@` 。 當與其他語言互動時，這會很有用。

C # 的實值型別會進一步分割成 *簡單類型*、 *列舉類型*、 *結構類型*和 *可為 null*的實值型別。 C # 的參考型別會進一步分割成 *類別類型*、 *介面類別型*、 *陣列類型*和 *委派類型*。

下列大綱概要說明 c # 的型別系統。

- [值類型](../language-reference/builtin-types/value-types.md)
  - [簡單型別](../language-reference/builtin-types/value-types.md#built-in-value-types)
    - [帶正負](../language-reference/builtin-types/integral-numeric-types.md)號的整數： `sbyte` 、 `short` 、 `int` 、 `long`
    - [不帶正負號的整數](../language-reference/builtin-types/integral-numeric-types.md)： `byte` 、 `ushort` 、 `uint` 、 `ulong`
    - [Unicode 字元](../../standard/base-types/character-encoding-introduction.md)： `char` ，代表 utf-16 程式碼單位
    - [IEEE 二進位浮點數](../language-reference/builtin-types/floating-point-numeric-types.md)： `float` 、 `double`
    - [高精確度十進位浮點數](../language-reference/builtin-types/floating-point-numeric-types.md)： `decimal`
    - `bool`代表布林值的布林值：-或的值。 `true``false`
  - [列舉類型](../language-reference/builtin-types/enum.md)
    - 表單的使用者定義類型 `enum E {...}` 。 `enum` 型別是包含具名常數的不同型別。 每個 `enum` 型別都具有一個基礎型別，其必須是八種整數型別之一。 `enum` 型別的值組與基礎型別的值組相同。
  - [結構型別](../language-reference/builtin-types/struct.md)
    - 使用者定義型別，格式為 `struct S {...}`
  - [可為 Null 的實值型別](../language-reference/builtin-types/nullable-value-types.md)
    - 含有 `null` 值的所有其他數值型別的擴充
  - [元組實數值型別](../language-reference/builtin-types/value-tuples.md)
    - 使用者定義型別，格式為 `(T1, T2, ...)`
- [參考型別](../language-reference/keywords/reference-types.md)
  - [類別類型](../language-reference/keywords/class.md)
    - 所有其他型別的基底類別︰`object`
    - [Unicode 字串](../../standard/base-types/character-encoding-introduction.md)： `string` ，代表一系列的 utf-16 程式碼單位
    - 使用者定義型別，格式為 `class C {...}`
  - [介面類型](../language-reference/keywords/interface.md)
    - 使用者定義型別，格式為 `interface I {...}`
  - [陣列類型](../programming-guide/arrays/index.md)
    - 單一和多維度和不規則，例如，、 `int[]` `int[,]` 和 `int[][]`
  - [委派型別](../language-reference/builtin-types/reference-types.md#the-delegate-type)
    - 使用者定義型別，格式為 `delegate int D(...)`

C# 程式使用*型別宣告*來建立新型別。 型別宣告指定新型別的名稱成員。 有五種類型的 c # 類別可供使用者定義：類別類型、結構類型、介面類別型、列舉類型和委派類型。

- `class` 型別定義資料結構，其中包含資料成員 (欄位) 和函式成員 (方法、屬性及其他)。 類別型別支援單一繼承和多型，這些是可供衍生類別將基底類別延伸及特製化的機制。
- `struct` 型別與類別型別相似，它代表具有資料成員和函式成員的結構。 不過，不同于類別，結構是實數值型別，通常不需要堆積配置。 結構類型不支援使用者指定的繼承，且所有結構類型都隱含地繼承自型別 `object` 。
- 類型會將 `interface` 合約定義為一組命名的公用成員。 執行的 `class` 或 `struct` `interface` 必須提供介面成員的實作為。 `interface` 可以繼承自多個基底介面，`class` 或 `struct`可實作多個介面。
- `delegate` 型別代表對方法的參考，其中含有特定參數清單與傳回型別。 委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。 委派類似函式語言提供的函式型別。 它們也與某些其他語言中的函式指標概念類似。 與函式指標不同的是，委派是物件導向且型別安全的。

`class`、、 `struct` `interface` 和 `delegate` 類型全都支援泛型，因此可以使用其他類型進行參數化。

C# 支援任何型別的單一維度及多維陣列。 不同于上面所列的類型，不需要先宣告陣列類型就可以使用它們。 而陣列型別的建構方法，是在型別名稱之後加上方括弧。 例如，是的一 `int[]` 維陣列，是的二維陣列，而是的一維陣列或「不規則」陣列的一 `int` `int[,]` `int` `int[][]` 維陣列 `int` 。

可為 null 的類型不需要個別的定義。 針對每一個不可為 null 的型 `T` 別，都有一個對應的可為 null 型 `T?` 別，可以保留額外的值 `null` 。 比方說， `int?` 是可以保存任何32位整數或值的型別 `null` ，而且 `string?` 是可保存任何或值的型別 `string` `null` 。

C # 的型別系統是統一的，因此任何型別的值都可以視為 `object` 。 C# 中的每個型別都直接或間接衍生自 `object` 類別型別，而 `object` 是所有型別的基底類別。 參考型別的值之所以會視為物件，只是將這些值當作 `object` 型別來檢視。 數值型別的值之所以會視為物件，只是透過執行 *boxing* 和 *unboxing* 作業。 在下列範例中，`int` 值會轉換成 `object`，並再次轉換回 `int`。

:::code language="csharp" source="./snippets/shared/Program.cs" ID="boxing" :::

當實值型別的值指派給 `object` 參考時，會配置 "box" 來保存該值。 該方塊是參考型別的實例，而值會複製到該方塊中。 相反地，當 `object` 參考轉換成實值型別時，就會檢查參考的 `object` 是正確值型別的方塊。 如果檢查成功，則會將方塊中的值複製到數值型別。

C # 的統一型別系統實際上表示實值型別被視為 `object` 參考「視需要」。 由於統一的一般用途程式庫 `object` 可以與衍生自的所有型別搭配使用 `object` ，包括參考型別和實值型別。

C# 中有數種*變數*，包括欄位、陣列元素、區域變數和參數。 變數代表儲存位置。 每個變數都有一種類型，可判斷哪些值可以儲存在變數中，如下所示。

- 不可為 Null 的實值型別
  - 該型別的值
- 可為 Null 的實值型別
  - `null` 值或該型別的值
- 物件 (object)
  - `null` 參考、任一參考型別之物件的參考，或是任一實值型別的 Boxed 值的參考
- 類別型別
  - `null` 參考、該類別型別之執行個體的參考，或衍生自該類別型別之類別執行個體的參考
- 介面類型
  - `null` 參考、實作該介面型別之類別型別的執行個體的參考，或實作該介面型別之實值型別的 Boxed 值的參考
- 陣列型別
  - `null` 參考、該陣列型別之執行個體的參考，或相容的陣列型別之執行個體的參考
- 委派類型
  - `null` 參考或相容的委派類型之執行個體的參考

## <a name="program-structure"></a>程式結構

C # 中的重要組織概念是 [***程式***](../programming-guide/inside-a-program/index.md)、 [***命名空間***](../programming-guide/namespaces/index.md)、 [***類型***](../programming-guide/types/index.md)、 [***成員***](../programming-guide/classes-and-structs/members.md)和 [***元件***](../../standard/assembly/index.md)。 程式宣告型別，其中包含成員並可以依據命名空間分組。 類別、結構和介面是類型的範例。 欄位、方法、屬性及事件都是成員的範例。 編譯 c # 程式時，它們實際上會封裝成元件。 組件通常具有副檔名 `.exe` 或 `.dll`，其分別在於實作「應用程式」****** 或「程式庫」******。

舉例來說，請考慮包含下列程式碼的元件：

:::code language="csharp" source="./snippets/shared/AcmeStack.cs":::

此類別的完整名稱是 `Acme.Collections.Stack`。 該類別包含數個成員︰一個名為 `top` 的欄位、兩個名為 `Push` 和 `Pop` 的方法以及名為 `Entry` 的巢狀類別。 `Entry` 類別更包含三個成員︰一個名為 `next` 的欄位、一個名為 `data` 的欄位以及建構函式。 `Stack`是*泛型*類別。 它有一個型別參數， `T` 會在使用時以具象型別取代。

> [!NOTE]
> *堆疊*是「first in last out」 (FILO) 收集。 新的元素會新增至堆疊的頂端。 移除專案時，它會從堆疊的最上方移除。

組件包含的可執行程式碼採用中繼語言 (IL) 指令形式，而符號資訊採用中繼資料形式。 在執行之前，即時 (JIT) 編譯器的 .NET Common Language Runtime 會將元件中的 IL 程式碼轉換成處理器特定的程式碼。

由於元件是包含程式碼和中繼資料的自我描述功能單位，因此 c # 中不需要指示詞 `#include` 和標頭檔。 特定組件中所包含的公用型別和成員只能在編譯程式時，使用 C# 程式來參考該組件。 例如，此程式使用來自 `acme.dll` 組件的 `Acme.Collections.Stack` 類別︰

:::code language="csharp" source="./snippets/shared/StackUsage.cs":::

若要編譯此程式，您必須 *參考* 包含先前範例中所定義之堆疊類別的元件。

C # 程式可以儲存在數個原始程式檔中。 編譯 c # 程式時，所有的原始程式檔都會一起處理，而原始程式檔可以自由地互相參考。 就概念而言，在處理之前，所有的原始程式檔都會串連成一個大型檔案。 C # 中永遠不需要向前宣告，因為有一些例外狀況，宣告順序並不重要。 C # 不會限制原始程式檔僅宣告一個公用類型，也不會要求來源檔案的名稱符合原始程式檔中宣告的類型。

本教學課程中的後續文章將說明這些組織區塊。

>[!div class="step-by-step"]
>[下一個](types.md)
