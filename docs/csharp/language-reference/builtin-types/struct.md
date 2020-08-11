---
title: '結構類型-c # 參考'
ms.date: 04/21/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 515b8d9adc1359581625f0d822e254d2c1df3b58
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062492"
---
# <a name="structure-types-c-reference"></a>結構類型 (c # 參考) 

*結構型*別 (或*結構型*別) 是可以封裝資料和相關功能的實[值型](value-types.md)別。 您可以使用 `struct` 關鍵字來定義結構型別：

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

結構類型具有*值的語義*。 也就是說，結構類型的變數會包含類型的實例。 根據預設，變數值會在指派時複製、將引數傳遞至方法，並傳回方法結果。 在結構類型變數的情況下，會複製類型的實例。 如需詳細資訊，請參閱實[數值型別](value-types.md)。

一般來說，您會使用結構類型來設計以資料為中心的小型類型，以提供些許或無行為。 例如，.NET 會使用結構類型來代表[整數](integral-numeric-types.md)和[實際](floating-point-numeric-types.md))  (的數位、[布林值](bool.md)、 [Unicode 字元](char.md)和[時間實例](xref:System.DateTime)。 如果您將焦點放在類型的行為，請考慮定義[類別](../keywords/class.md)。 類別類型具有*參考語義*。 也就是說，類別類型的變數包含類型實例的參考，而不是實例本身。

因為結構類型具有值的語義，所以我們建議您定義*不可變*的結構類型。

## <a name="readonly-struct"></a>`readonly`結構

從 c # 7.2 開始，您可以使用 `readonly` 修飾詞來宣告結構類型是不可變的：

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

結構的所有資料成員都 `readonly` 必須是唯讀的，如下所示：

- 任何欄位宣告都必須有[ `readonly` 修飾](../keywords/readonly.md)詞
- 任何包含自動執行的屬性都必須是唯讀的

這可保證結構的成員不會 `readonly` 修改結構的狀態。

> [!NOTE]
> 在 `readonly` 結構中，可變參考型別的資料成員仍然可以改變其本身的狀態。 例如，您無法取代 <xref:System.Collections.Generic.List%601> 實例，但是您可以在其中加入新的元素。

## <a name="readonly-instance-members"></a>`readonly`實例成員

從 c # 8.0 開始，您也可以使用 `readonly` 修飾詞來宣告實例成員不會修改結構的狀態。 如果您無法將整個結構類型宣告為 `readonly` ，請使用 `readonly` 修飾詞來標記不會修改結構狀態的實例成員。 在 `readonly` 結構中，每個實例成員都是隱含的 `readonly` 。

在 `readonly` 實例成員內，您無法指派給結構的實例欄位。 不過， `readonly` 成員可以呼叫非 `readonly` 成員。 在這種情況下，編譯器會建立結構實例的複本，並呼叫 `readonly` 該複本上的非成員。 因此，不會修改原始的結構實例。

一般來說，您會將 `readonly` 修飾詞套用至下列類型的實例成員：

- 方法

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  您也可以將修飾詞套用 `readonly` 至覆寫中所宣告方法的方法 <xref:System.Object?displayProperty=nameWithType> ：

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- 屬性和索引子：

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  如果您需要將修飾詞套用 `readonly` 至屬性或索引子的兩個存取子，請將它套用至屬性或索引子的宣告中。

  > [!NOTE]
  > `get`不論屬性宣告中的修飾詞是否存在，編譯器都會將自動實作為[屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)的存取子宣告為 `readonly` `readonly` 。

您無法將修飾詞套用 `readonly` 至結構類型的靜態成員。

編譯器可能會使用 `readonly` 修飾詞來進行效能優化。 如需詳細資訊，請參閱[撰寫安全且有效率的 c # 程式碼](../../write-safe-efficient-code.md)。

## <a name="limitations-with-the-design-of-a-structure-type"></a>結構類型設計的限制

當您設計結構類型時，您具有與[類別](../keywords/class.md)類型相同的功能，但有下列例外狀況：

- 您不能宣告無參數的函式。 每個結構類型已經提供隱含的無參數的函式，以產生類型的[預設值](default-values.md)。

- 您無法在其宣告中初始化實例欄位或屬性。 不過，您可以在其宣告中初始化[靜態](../keywords/static.md)或[常數](../keywords/const.md)欄位或靜態屬性。

- 結構類型的「構造函式」必須初始化該類型的所有實例欄位。

- 結構型別無法繼承自其他類別或結構型別，而且它不能是類別的基底。 不過，結構類型可以執行[介面](../keywords/interface.md)。

- 您[無法在結構類型中宣告](../../programming-guide/classes-and-structs/destructors.md)完成項。

## <a name="instantiation-of-a-structure-type"></a>結構類型的具現化

在 c # 中，您必須先初始化已宣告的變數，才能使用它。 因為結構類型變數無法 `null` (，除非它是[可為 null 的實數值型別](nullable-value-types.md)) 的變數，您必須具現化對應類型的實例。 有幾種方式可以這麼做。

通常，您會使用運算子來呼叫適當的處理常式，以具現化結構類型 [`new`](../operators/new-operator.md) 。 每個結構類型都至少有一個函式。 這是隱含的無參數的函式，它會產生類型的[預設值](default-values.md)。 您也可以使用[預設值運算式](../operators/default.md)來產生類型的預設值。

如果結構類型的所有實例欄位都可存取，您也可以在不使用運算子的情況下將它具現化 `new` 。 在此情況下，您必須在第一次使用實例之前，先初始化所有實例欄位。 下列範例顯示如何執行該項工作：

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

在內[建實數值型別](value-types.md#built-in-value-types)的情況下，請使用對應的常值來指定類型的值。

## <a name="passing-structure-type-variables-by-reference"></a>以傳址方式傳遞結構型別變數

當您將結構型別變數當做引數傳遞至方法，或從方法傳回結構型別值時，會複製結構型別的整個實例。 這可能會影響您的程式碼在涉及大型結構類型的高效能案例中的效能。 您可以透過傳址方式傳遞結構型別變數，以避免值複製。 使用 [`ref`](../keywords/ref.md#passing-an-argument-by-reference) 、 [`out`](../keywords/out-parameter-modifier.md) 或方法參數修飾詞， [`in`](../keywords/in-parameter-modifier.md) 表示必須以傳址方式傳遞引數。 使用[ref](../../programming-guide/classes-and-structs/ref-returns.md) return 傳回以傳址方式傳回的方法結果。 如需詳細資訊，請參閱[撰寫安全且有效率的 c # 程式碼](../../write-safe-efficient-code.md)。

## <a name="ref-struct"></a>`ref`結構

從 c # 7.2 開始，您可以在 `ref` 結構類型的宣告中使用修飾詞。 `ref`結構型別的實例會配置於堆疊上，而且無法將其跳到 managed 堆積。 為確保，編譯器會限制結構類型的使用 `ref` 方式，如下所示：

- `ref`結構不可以是陣列的元素類型。
- `ref`結構不可以是類別或非結構之欄位的宣告型別 `ref` 。
- `ref`結構無法執行介面。
- `ref`無法將結構封裝成 <xref:System.ValueType?displayProperty=nameWithType> 或 <xref:System.Object?displayProperty=nameWithType> 。
- `ref`結構不可以是類型引數。
- `ref` [Lambda 運算式](../operators/lambda-expressions.md)或[區域函數](../../programming-guide/classes-and-structs/local-functions.md)無法捕捉結構變數。
- `ref`結構變數不能用在方法中 [`async`](../keywords/async.md) 。 不過，您可以在 `ref` 同步方法中使用結構變數，例如，在傳回或的情況下 <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> 。
- `ref`Struct 變數不能用在[反覆運算](../../iterators.md)器中。

`ref`當您需要也包含結構類型之資料成員的類型時，通常會定義結構類型 `ref` ：

[!code-csharp[ref struct](snippets/StructType.cs#RefStruct)]

若要將 `ref` 結構宣告為 [`readonly`](#readonly-struct) ，請 `readonly` 在類型宣告中結合和修飾詞， `ref` (修飾詞必須在修飾詞 `readonly` `ref`) 之前：

[!code-csharp[readonly ref struct](snippets/StructType.cs#ReadonlyRef)]

在 .NET 中，結構的範例 `ref` 是 <xref:System.Span%601?displayProperty=nameWithType> 和 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 。

## <a name="conversions"></a>轉換

針對任何結構類型 (除了[ `ref` 結構](#ref-struct)類型) 之外，還有在和類型之間進行的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換 <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> 。 結構型別和它所執行的任何介面之間也有一個裝箱和取消裝箱轉換。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[結構](~/_csharplang/spec/structs.md)一節。

如需 c # 7.2 和更新版本中引進之功能的詳細資訊，請參閱下列功能建議事項：

- [Readonly 結構](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [唯讀執行個體成員](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [參考樣式類型的編譯時間安全性](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [設計方針-在類別和結構之間選擇](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [設計方針-結構設計](../../../standard/design-guidelines/struct.md)
- [類別和結構](../../programming-guide/classes-and-structs/index.md)
