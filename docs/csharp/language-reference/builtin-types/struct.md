---
title: '結構類型-c # 參考'
description: 瞭解 C 中的結構類型#
ms.date: 10/23/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 96a39609e9ae8b11e9872b049134136fe1ff3e2a
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599098"
---
# <a name="structure-types-c-reference"></a>結構類型 (c # 參考) 

*結構類型* (或 *結構類型*) 是可封裝資料和相關功能的實 [值型](value-types.md)別。 您可以使用 `struct` 關鍵字來定義結構類型：

[!code-csharp[struct example](snippets/shared/StructType.cs#StructExample)]

結構類型具有 *值語義*。 也就是說，結構型別的變數包含型別的實例。 根據預設，變數值會在指派時複製、將引數傳遞至方法，並傳回方法結果。 在結構類型變數的情況下，會複製類型的實例。 如需詳細資訊，請參閱實 [數值型別](value-types.md)。

一般而言，您會使用結構類型來設計以資料為中心的小型型別，以提供小或無的行為。 例如，.NET 會使用結構類型來表示 [整數](integral-numeric-types.md) 和 [實數](floating-point-numeric-types.md)) 的數位 (、 [布林值](bool.md)、 [Unicode 字元](char.md)、 [時間實例](xref:System.DateTime)。 如果您是以類型的行為為焦點，請考慮定義 [類別](../keywords/class.md)。 類別類型具有 *參考語義*。 也就是說，類別型別的變數包含型別實例的參考，而不是實例本身。

因為結構類型具有值語義，所以建議您定義 *不可變* 的結構類型。

## <a name="readonly-struct"></a>`readonly` 結構

從 c # 7.2 開始，您可以使用 `readonly` 修飾詞來宣告結構類型是不可變的：

[!code-csharp[readonly struct](snippets/shared/StructType.cs#ReadonlyStruct)]

結構的所有資料成員都 `readonly` 必須是唯讀的，如下所示：

- 任何欄位宣告都必須有[ `readonly` 修飾](../keywords/readonly.md)詞
- 任何屬性（包括自動執行的屬性）都必須是唯讀的。 在 c # 9.0 和更新版本中，屬性可能具有[ `init` 存取](../../whats-new/csharp-9.md#init-only-setters)子。

這可保證結構的成員不會 `readonly` 修改結構的狀態。 在 c # 8.0 和更新版本中，這表示其他實例成員（除了函式之外）是隱含的 [`readonly`](#readonly-instance-members) 。

> [!NOTE]
> 在 `readonly` 結構中，可變動參考型別的資料成員仍可以改變本身的狀態。 例如，您無法取代 <xref:System.Collections.Generic.List%601> 實例，但是可以在其中加入新的元素。

## <a name="readonly-instance-members"></a>`readonly` 實例成員

從 c # 8.0 開始，您也可以使用 `readonly` 修飾詞來宣告實例成員不會修改結構的狀態。 如果您無法將整個結構類型宣告為 `readonly` ，請使用 `readonly` 修飾詞來標記不會修改結構狀態的實例成員。

在 `readonly` 實例成員中，您無法指派給結構的實例欄位。 不過， `readonly` 成員可以呼叫非 `readonly` 成員。 在這種情況下，編譯器會建立結構實例的複本，並呼叫 `readonly` 該複本上的非成員。 因此，原始的結構實例不會被修改。

一般來說，您會將 `readonly` 修飾詞套用至下列類型的實例成員：

- 方法：

  [!code-csharp[readonly method](snippets/shared/StructType.cs#ReadonlyMethod)]

  您也可以將修飾詞套用 `readonly` 至覆寫在中宣告之方法的方法 <xref:System.Object?displayProperty=nameWithType> ：

  [!code-csharp[readonly override](snippets/shared/StructType.cs#ReadonlyOverride)]

- 屬性和索引子：

  [!code-csharp[readonly property get](snippets/shared/StructType.cs#ReadonlyProperty)]

  如果您需要將修飾詞套用 `readonly` 至屬性或索引子的兩個存取子，請將它套用至屬性或索引子的宣告中。

  > [!NOTE]
  > 編譯器會將 `get` [自動執行之屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md) 的存取子宣告為 `readonly` ，而不論屬性宣告中的修飾詞是否存在 `readonly` 。

  在 c # 9.0 和更新版本中，您可以 `readonly` 使用存取子將修飾詞套用至屬性或索引子 `init` ：

  :::code language="csharp" source="snippets/shared/StructType.cs" id="ReadonlyWithInit":::

您無法將修飾詞套用 `readonly` 至結構類型的靜態成員。

編譯器可能會使用 `readonly` 修飾詞進行效能優化。 如需詳細資訊，請參閱 [撰寫安全且有效率的 c # 程式碼](../../write-safe-efficient-code.md)。

## <a name="limitations-with-the-design-of-a-structure-type"></a>結構類型設計的限制

當您設計結構類型時，與 [類別](../keywords/class.md) 類型具有相同的功能，但有下列例外狀況：

- 您無法宣告無參數的函式。 每個結構類型都已提供隱含的無參數函式，其會產生型別的 [預設值](default-values.md) 。

- 您無法在宣告時初始化實例欄位或屬性。 不過，您可以在宣告時初始化 [靜態](../keywords/static.md) 或 [const](../keywords/const.md) 欄位或靜態屬性。

- 結構類型的函式必須初始化類型的所有實例欄位。

- 結構類型無法繼承自其他類別或結構類型，而且不能是類別的基底。 不過，結構類型可以執行 [介面](../keywords/interface.md)。

- 您無法在結構 [類型中宣告](../../programming-guide/classes-and-structs/destructors.md) 完成項。

## <a name="instantiation-of-a-structure-type"></a>結構類型的具現化

在 c # 中，您必須先初始化已宣告的變數，才能使用它。 因為結構類型變數無法 `null` (，除非它是 [可為 null 實值型](nullable-value-types.md) 別) 的變數，所以您必須具現化對應類型的實例。 有幾種方法可以這麼做。

一般來說，您可以使用運算子呼叫適當的函式，以具現化結構類型 [`new`](../operators/new-operator.md) 。 每個結構類型都至少有一個函數。 這是隱含無參數的函式，它會產生型別的 [預設值](default-values.md) 。 您也可以使用 [預設值運算式](../operators/default.md) 來產生型別的預設值。

如果結構類型的所有實例欄位都可以存取，您也可以在不使用運算子的情況下將它具現化 `new` 。 在這種情況下，您必須在第一次使用實例之前，初始化所有的實例欄位。 下列範例顯示如何執行該項工作：

[!code-csharp[without new](snippets/shared/StructType.cs#WithoutNew)]

在內 [建實值](value-types.md#built-in-value-types)型別的情況下，請使用對應的常值來指定類型的值。

## <a name="passing-structure-type-variables-by-reference"></a>以傳址方式傳遞結構類型變數

當您將結構類型變數當作引數傳遞至方法，或是從方法傳回結構類型值時，會複製結構類型的整個實例。 這可能會影響您的程式碼在涉及大型結構類型的高效能案例中的效能。 您可以藉由傳址方式傳遞結構類型變數，以避免值複製。 使用 [`ref`](../keywords/ref.md#passing-an-argument-by-reference) 、 [`out`](../keywords/out-parameter-modifier.md) 或方法參數修飾詞 [`in`](../keywords/in-parameter-modifier.md) 來表示引數必須以傳址方式傳遞。 使用 [ref](../../programming-guide/classes-and-structs/ref-returns.md) return 以傳址方式傳回方法結果。 如需詳細資訊，請參閱 [撰寫安全且有效率的 c # 程式碼](../../write-safe-efficient-code.md)。

## <a name="ref-struct"></a>`ref` 結構

從 c # 7.2 開始，您可以 `ref` 在結構類型的宣告中使用修飾詞。 `ref`結構類型的實例會在堆疊上配置，而且無法對 managed 堆積進行 escape。 為了確保這一點，編譯器會限制結構類型的使用方式，如下所示 `ref` ：

- `ref`結構不能是陣列的元素類型。
- `ref`結構不能是類別或非結構之欄位的宣告型別 `ref` 。
- `ref`結構無法執行介面。
- `ref`結構不能封裝成 <xref:System.ValueType?displayProperty=nameWithType> 或 <xref:System.Object?displayProperty=nameWithType> 。
- `ref`結構不能是型別引數。
- `ref` [Lambda 運算式](../operators/lambda-expressions.md)或[區域函數](../../programming-guide/classes-and-structs/local-functions.md)無法捕捉結構變數。
- `ref`結構變數不能用在方法中 [`async`](../keywords/async.md) 。 不過，您可以 `ref` 在同步方法中使用結構變數，例如，在傳回或的 <xref:System.Threading.Tasks.Task> 中 <xref:System.Threading.Tasks.Task%601> 。
- `ref`結構變數不能用在[反覆運算](../../iterators.md)器中。

一般來說， `ref` 當您需要也包含結構類型之資料成員的型別時，您會定義結構類型 `ref` ：

[!code-csharp[ref struct](snippets/shared/StructType.cs#RefStruct)]

若要將 `ref` 結構宣告為 [`readonly`](#readonly-struct) ，請 `readonly` 在類型宣告中結合和修飾詞， `ref` (修飾詞必須在修飾詞 `readonly` `ref`) 之前：

[!code-csharp[readonly ref struct](snippets/shared/StructType.cs#ReadonlyRef)]

在 .NET 中，結構的範例 `ref` 包括 <xref:System.Span%601?displayProperty=nameWithType> 和 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 。

## <a name="struct-constraint"></a>結構條件約束

您也可以 `struct` 在[ `struct` 條件約束](../../programming-guide/generics/constraints-on-type-parameters.md)中使用關鍵字，指定型別參數為不可為 null 的實值型別。 結構和 [列舉](enum.md) 類型都符合 `struct` 條件約束。

## <a name="conversions"></a>轉換

若為任何結構類型 ([ `ref` 結構](#ref-struct)類型除外) ，則會在和類型之間存在的[裝箱和取消](../../programming-guide/types/boxing-and-unboxing.md)加入轉換 <xref:System.ValueType?displayProperty=nameWithType> <xref:System.Object?displayProperty=nameWithType> 。 結構類型和它所執行的任何介面之間，也有另外的裝箱和取消程式轉換。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[結構](~/_csharplang/spec/structs.md)一節。

如需有關 c # 7.2 和更新版本中所引進之功能的詳細資訊，請參閱下列功能提案附注：

- [Readonly 結構](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [唯讀執行個體成員](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [參考樣式類型的編譯時間安全性](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [設計指導方針-在類別和結構之間選擇](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [設計指導方針-結構設計](../../../standard/design-guidelines/struct.md)
- [類別和結構](../../programming-guide/classes-and-structs/index.md)
