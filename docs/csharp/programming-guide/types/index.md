---
title: 類型 - C# 程式設計手冊
description: '深入瞭解 c # 程式設計中的類型，例如內建類型、自訂類型、實數值型別和參考型別。'
ms.date: 11/19/2020
helpviewer_keywords:
- value types [C#]
- reference types [C#]
- types [C#]
- C# language, data types
- common type system [C#]
- data types [C#]
- C# language, types
- strong typing [C#]
ms.assetid: f782d7cc-035e-4500-b1b1-36a9881130ad
ms.openlocfilehash: c347dbc6af46d4c334445d606d7cedfdf17e43f6
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098706"
---
# <a name="types-c-programming-guide"></a>類型 (C# 程式設計手冊)

## <a name="types-variables-and-values"></a>類型、變數和值

C # 是強型別語言。 每個變數和常數都有型別，如同每個會評估為值的運算式一般。 每個方法宣告都會針對每個輸入參數和傳回值指定名稱、參數數目、類型和種類 (值、參考或輸出) 。 .NET 類別庫會定義一組內建數數值型別，以及更複雜的型別，這些型別代表各種不同的邏輯結構，例如檔案系統、網路連接、物件的集合和陣列，以及日期。 一般 c # 程式會使用類別庫的類型和使用者定義型別，來建立程式問題領域專屬概念的模型。

儲存在類型中的資訊可以包含下列專案：

- 型別的變數需要的儲存空間。
- 它可以代表的最大值和最小值。
- 它所包含的成員 (方法、欄位、事件等等)。
- 它繼承自的基底型別。
- 介面 (s) 它所執行。
- 將在執行階段配置給變數的記憶體位置。
- 允許的作業類型。

編譯器會使用類型資訊，以確保在您的程式碼中執行的所有作業都是 *型別安全*。 例如，如果您宣告型別 [int](../../language-reference/builtin-types/integral-numeric-types.md) 的變數，編譯器會允許您使用額外的變數和減法運算。 如果您嘗試針對型別 [bool](../../language-reference/builtin-types/bool.md) 的變數執行相同作業，編譯器會產生錯誤，如下列範例所示︰

:::code language="csharp" source="snippets/index/Program.cs" id="TypeSafeExample":::

> [!NOTE]
> C 和 C++ 開發人員要注意在 C# 中，[bool](../../language-reference/builtin-types/bool.md) 不能轉換為 [int](../../language-reference/builtin-types/integral-numeric-types.md)。

編譯器會將型別資訊視為中繼資料內嵌至可執行檔。 通用語言執行平台 (CLR) 會在執行階段使用該中繼資料，以在它配置和回收記憶體時，進一步保證型別安全。

### <a name="specifying-types-in-variable-declarations"></a>在變數宣告中指定類型

當您在程式中宣告變數或常數時，您必須指定其型別，或使用 [var](../../language-reference/keywords/var.md) 關鍵字以讓編譯器推斷其型別。 下列範例示範一些變數宣告，使用內建的數字型別和複雜的使用者定義型別︰

:::code language="csharp" source="snippets/index/Program.cs" id="Declarations":::

方法參數和傳回值的類型是在方法宣告中指定。 下列簽章顯示的方法要求 [int](../../language-reference/builtin-types/integral-numeric-types.md) 做為輸入引數且會傳回字串︰

:::code language="csharp" source="snippets/index/Program.cs" id="GetName":::

宣告變數之後，您就無法使用新的類型來重新宣告變數，也無法指派與其宣告類型不相容的值。 例如，您無法宣告 [int](../../language-reference/builtin-types/integral-numeric-types.md) ，然後為它指派布林值 `true` 。 不過，您可以將值轉換成其他類型，例如，將它們指派給新的變數，或做為方法引數傳遞。 編譯器會自動執行不會造成資料遺失的 *型別轉換* 。 而可能導致資料遺失的轉換在原始程式碼中需要有 *cast*。

如需詳細資訊，請參閱[轉換和型別轉換](./casting-and-type-conversions.md)。

## <a name="built-in-types"></a>內建類型

C # 提供一組標準的內建類型，以表示整數、浮點數、布林運算式、文字字元、十進位值和其他類型的資料。 另外還有內建的 `string` 和 `object` 型別。 您可以在任何 c # 程式中使用這些類型。 如需內建類型的完整清單，請參閱 [內建類型](../../language-reference/builtin-types/built-in-types.md)。

## <a name="custom-types"></a>自訂類型

您可使用 [struct](../../language-reference/builtin-types/struct.md)、[class](../../language-reference/keywords/class.md)、[interface](../../language-reference/keywords/interface.md) 及 [enum](../../language-reference/builtin-types/enum.md) 建構來建立您自己的自訂型別。 .NET 類別庫本身是 Microsoft 所提供的自訂型別集合，可供您用於自己的應用程式中。 根據預設，類別庫中最常使用的型別可用於任何 C# 程式中。 只有當您明確地將專案參考新增至其定義所在的元件時，其他專案才會變成可用。 編譯器在有該組件的參考之後，您可以針對在原始程式碼的那個組件中宣告的型別宣告變數 (和常數) 。 如需詳細資訊，請參閱 [.NET 類別庫](../../../standard/class-library-overview.md)。

## <a name="the-common-type-system"></a>一般類型系統

請務必瞭解 .NET 中的型別系統的兩個基本要點：

- 它支援繼承原則。 型別可以衍生自稱為「基底型別」的其他型別。 衍生的型別會繼承 (有部份限制) 基底型別的方法、屬性和其他成員。 基底型別同樣可以衍生自一些其他型別，所衍生的型別會繼承其繼承階層架構中兩個基底型別的成員。 包括 <xref:System.Int32?displayProperty=nameWithType> (C# 關鍵字：[int](../../language-reference/builtin-types/integral-numeric-types.md)) 等內建數字型別在內的所有型別，最終都衍生自單一基底型別，即 <xref:System.Object?displayProperty=nameWithType> (C# 關鍵字：[object](../../language-reference/builtin-types/reference-types.md))。 這種統一型別階層架構稱為[一般型別系統](../../../standard/base-types/common-type-system.md) (CTS)。 如需 C# 中有關繼承的詳細資訊，請參閱[繼承](../classes-and-structs/inheritance.md)。
- CTS 中的每個型別都會定義為「實值型別」或「參考型別」。 這些類型包括 .NET 類別庫中的所有自訂類型，以及您自己的使用者定義類型。 您使用 [struct](../../language-reference/builtin-types/struct.md) 關鍵字定義的型別為實值型別；所有內建的數字型別都是 `structs`。 您使用 [class](../../language-reference/keywords/class.md) 關鍵字定義的型別為參考型別。 參考型別和實值型別有不同的編譯時期規則和不同的執行階段行為。

下圖顯示 CTS 中的實值型別和參考型別之間的關聯性。

下圖顯示 CTS 中的實值型別和參考型別：

![顯示 CTS 實值型別和參考型別的螢幕擷取畫面。](./media/index/value-reference-types-common-type-system.png)

> [!NOTE]
> 您可以看到最常使用的型別全都整理在 <xref:System> 命名空間中。 不過，其中包含型別的命名空間和實值型別或參考型別毫無關聯。

### <a name="value-types"></a>值類型

實值型別衍生自 <xref:System.ValueType?displayProperty=nameWithType>，該型別又衍生自 <xref:System.Object?displayProperty=nameWithType>。 衍生自 <xref:System.ValueType?displayProperty=nameWithType> 的型別在 CLR 中具有特殊行為。 實值型別變數會直接包含其值，這表示配置的記憶體內嵌在宣告該變數的內容中。 數值型別變數沒有個別的堆積配置或垃圾收集負荷。

實值型別有兩種類別︰[struct](../../language-reference/builtin-types/struct.md) 和 [enum](../../language-reference/builtin-types/enum.md)。

內建的數位類型是結構，而且具有您可以存取的欄位和方法：

:::code language="csharp" source="snippets/index/Program.cs" id="ConstantByte":::

但是，您可以宣告並指派值給它們，就像它們是簡單的非匯總類型一樣：

:::code language="csharp" source="snippets/index/Program.cs" id="NonAggregateTypes":::

實數值型別是 *密封* 的，這表示您無法從任何實值型別衍生型別 <xref:System.Int32?displayProperty=nameWithType> 。 您無法將結構定義為繼承自任何使用者定義的類別或結構，因為結構只能繼承自 <xref:System.ValueType?displayProperty=nameWithType> 。 不過，結構可以實作一個或多個介面。 您可以將結構類型轉換成它所實的任何介面型別;這 *種轉換* 會導致將結構包裝在 managed 堆積上的參考型別物件內。 當您將實值型別傳遞至接受 <xref:System.Object?displayProperty=nameWithType> 或任何介面型別做為輸入參數的方法時，就會發生 Boxing 作業。 如需詳細資訊，請參閱 [Boxing 和 Unboxing](./boxing-and-unboxing.md)。

您使用 [struct](../../language-reference/builtin-types/struct.md) 關鍵字來建立您自己自訂的實值型別。 一般來說，會使用結構做為一小組相關變數的容器，如下列範例所示︰

:::code language="csharp" source="snippets/index/Program.cs" id="Coords":::

如需結構的詳細資訊，請參閱 [結構類型](../../language-reference/builtin-types/struct.md)。 如需實值型別的詳細資訊，請參閱實 [數值型別](../../language-reference/builtin-types/value-types.md)。

實值型別的另一種類別是 [enum](../../language-reference/builtin-types/enum.md)。 列舉會定義一組具名的整數常數。 例如，.NET 類別庫中的 <xref:System.IO.FileMode?displayProperty=nameWithType> 列舉包含一組指定該如何開啟檔案的具名常數整數。 其定義方式如下列範例所示：

:::code language="csharp" source="snippets/index/Program.cs" id="EnumFileMode":::

`System.IO.FileMode.Create` 常數的值為 2。 不過，名稱對於讀取原始程式碼的人來說更有意義，因此最好是使用列舉，而不是常數常值。 如需詳細資訊，請參閱<xref:System.IO.FileMode?displayProperty=nameWithType>。

所有的委派都繼承自 <xref:System.Enum?displayProperty=nameWithType>，該列舉又繼承自 <xref:System.ValueType?displayProperty=nameWithType>。 所有適用於結構的規則，也適用於列舉。 如需列舉的詳細資訊，請參閱 [列舉類型](../../language-reference/builtin-types/enum.md)。

### <a name="reference-types"></a>參考型別

定義為 [class](../../language-reference/keywords/class.md)、[delegate](../../language-reference/builtin-types/reference-types.md)、array 或 [interface](../../language-reference/keywords/interface.md) 的型別即為「參考型別」。 在執行階段，當您宣告參考型別的變數時，該變數會包含值 [null](../../language-reference/keywords/null.md)，直到您使用 [new](../../language-reference/operators/new-operator.md) 運算子明確地建立物件，或為它指派在他處使用 `new` 建立的物件為止，如下列範例所示︰

:::code language="csharp" source="snippets/index/Program.cs" id="DeclarationAndAssignment":::

介面必須和實作它的類別物件一起初始化。 如果 `MyClass` 實作 `IMyInterface`，您建立的 `IMyInterface` 執行個體會如下列範例所示︰

:::code language="csharp" source="snippets/index/Program.cs" id="InterfaceDeclaration":::

建立物件時，會在 Managed 堆積上配置記憶體，而變數只會保留物件位置的參考。 Managed 堆積上的類型在配置時，以及由 CLR 的自動記憶體管理功能（也就是所謂的 *垃圾收集*）回收時，都需要額外負荷。 不過，垃圾收集也已高度優化，在大部分情況下，它不會產生效能問題。 如需有關記憶體回收的詳細資訊，請參閱[自動記憶體管理](../../../standard/automatic-memory-management.md)。

所有陣列都是參考型別，即使其元素都是實值型別。 陣列隱含衍生自 <xref:System.Array?displayProperty=nameWithType> 類別，但您會利用 C# 所提供的簡化語法來宣告及使用陣列，如下列範例所示：

:::code language="csharp" source="snippets/index/Program.cs" id="ArrayDeclaration":::

參考型別完全支援繼承。 當您建立類別時，可以繼承自任何未定義為 [密封](../../language-reference/keywords/sealed.md)的介面或類別，而其他類別可以繼承自您的類別並覆寫您的虛擬方法。 如需如何為您自己建立類別的詳細資訊，請參閱[類別和結構](../classes-and-structs/index.md)。 如有關繼承和虛擬方法的詳細資訊，請參閱[繼承](../classes-and-structs/inheritance.md)。

## <a name="types-of-literal-values"></a>常值的類型

在 C# 中，常值會接收來自編譯器的型別。 您可以在數字後面附加一個字母，指定應如何輸入數值常值。 例如，若要指定應該將值 4.56 視為浮點數時，請在數字之後附加 "f" 或 "F"︰`4.56f`。 如果未附加任何字母時，編譯器會推斷其型別為常值。 如需可以使用字母后置字元指定哪些類型的詳細資訊，請參閱 [整數類資料類型](../../language-reference/builtin-types/integral-numeric-types.md) 和 [浮點數](../../language-reference/builtin-types/floating-point-numeric-types.md)類型。

因為常值是具型別，而且所有型別最終都是衍生自 <xref:System.Object?displayProperty=nameWithType> ，所以您可以撰寫和編譯器代碼，如下列程式碼所示：

:::code language="csharp" source="snippets/index/Program.cs" id="ConvertTypes":::

## <a name="generic-types"></a>泛型類型

可使用一或多個「型別參數」宣告的型別，做為預留位置 (具象型別)，以供用戶端程式碼在其建立該型別的執行個體時提供實際型別。 這類的型別稱為「泛型型別」。 例如，.NET 型別 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 有一個依慣例指定名稱 *T* 的型別參數。當您建立型別的實例時，您會指定清單將包含的物件類型，例如字串：

:::code language="csharp" source="snippets/index/Program.cs" id="GenericType":::

使用型別參數讓您能夠重複使用相同的類別來保存任何元素型別，而不需要將每個元素都轉換成 [object](../../language-reference/builtin-types/reference-types.md)。 泛型集合類別稱為強型別 *集合* ，因為編譯器知道集合專案的特定類型，如果您嘗試將整數加入至 `stringList` 上述範例中的物件，就會在編譯時期引發錯誤。 如需詳細資訊，請參閱[泛型](../generics/index.md)。

## <a name="implicit-types-anonymous-types-and-nullable-value-types"></a>隱含類型、匿名型別和可為 null 的實值型別

如先前所述，您可以使用 [var](../../language-reference/keywords/var.md) 關鍵字，隱含地輸入本機變數 (但不是類別成員)。 變數還是會在編譯時期收到型別，但其是由編譯器所提供的型別。 如需詳細資訊，請參閱[隱含型別區域變數](../classes-and-structs/implicitly-typed-local-variables.md)。

針對您不想要儲存或在方法界限外傳遞的簡單相關值集建立一個命名類型，可能不方便。 為此，您可以建立「匿名型別」。 如需詳細資訊，請參閱 [匿名型別](../classes-and-structs/anonymous-types.md)。

一般實數值型別不能有 [null](../../language-reference/keywords/null.md)值。 不過，您可以在類型之後附加，以建立可為 null 的實數值型別 `?` 。 例如，`int?` 就是也能有 [null](../../language-reference/keywords/null.md) 值的 `int` 型別。 可為 null 的實數值型別是泛型結構類型的實例 <xref:System.Nullable%601?displayProperty=nameWithType> 。 可為 null 的實值型別特別適用于當您將資料傳入和寫入資料庫時，數值可能會是 null。 如需詳細資訊，請參閱 [可為 null 的實數值型別](../../language-reference/builtin-types/nullable-value-types.md)。

## <a name="compile-time-type-and-runtime-type"></a>編譯時間類型和執行時間類型

變數可以有不同的編譯時期和執行時間類型。 *編譯時間類型* 是原始程式碼中變數的宣告或推斷型別。 *執行時間類型* 是該變數所參考之實例的型別。 這兩種類型通常是相同的，如下列範例所示：

:::code language="csharp" source="snippets/index/Program.cs" id="CompileTimeType":::

在其他情況下，編譯時間類型是不同的，如下列兩個範例所示：

:::code language="csharp" source="snippets/index/Program.cs" id="RuntimeTypes":::

在上述兩個範例中，執行時間類型為 `string` 。 編譯時間類型是 `object` 在第一行，而 `IEnumerable<char>` 在第二個。

如果變數的這兩個類型不同，請務必瞭解何時套用編譯時間類型和執行時間類型。 編譯時間類型決定編譯器所採取的所有動作。 這些編譯器動作包括方法呼叫解析、多載解析，以及可用的隱含和明確轉換。 執行時間類型決定在執行時間解決的所有動作。 這些執行時間動作包括分派虛擬方法呼叫、評估 `is` 和 `switch` 運算式，以及其他型別測試 api。 若要進一步瞭解您的程式碼與型別之間的互動方式，請辨識何種動作適用於何種類型。

## <a name="related-sections"></a>相關章節

如需詳細資訊，請參閱下列文章：

- [轉換和類型轉換](./casting-and-type-conversions.md)
- [Boxing 和 Unboxing](./boxing-and-unboxing.md)
- [使用動態類型](./using-type-dynamic.md)
- [實數值型別](../../language-reference/builtin-types/value-types.md)
- [參考型別](../../language-reference/keywords/reference-types.md)
- [類別和結構](../classes-and-structs/index.md)
- [匿名類型](../classes-and-structs/anonymous-types.md)
- [泛型](../generics/index.md)

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C # 參考](../../language-reference/index.md)
- [C # 程式設計指南](../index.md)
- [XML 資料型別轉換](../../../standard/data/xml/conversion-of-xml-data-types.md)
- [整數型別](../../language-reference/builtin-types/integral-numeric-types.md)
