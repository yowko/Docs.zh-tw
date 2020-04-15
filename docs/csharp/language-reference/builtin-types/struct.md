---
title: 結構類型 - C# 引用
ms.date: 04/14/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 8013aab5580ac007875debc78208532a2d0ad1dc
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388996"
---
# <a name="structure-types-c-reference"></a>結構類型(C# 參考)

*結構類型*(或*結構型態*)是一種可以封裝資料和相關功能[的值類型](value-types.md)。 使用 關鍵`struct`字 定義結構類型:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

結構類型具有*值語意*。 也就是說,結構類型的變數包含類型的實例。 默認情況下,在賦值時複製變數值,將參數傳遞給方法,並返回方法結果。 對於結構類型變數,將複製類型的實例。 有關詳細資訊,請參考[值類型](value-types.md)。

通常,使用結構類型來設計提供很少或沒有行為的小型以數據為中心的類型。 例如,.NET 使用結構類型來表示數位([整數](integral-numeric-types.md)與[實體 )](floating-point-numeric-types.md),[布林值](bool.md)[, Unicode 字元](char.md),[時間實例](xref:System.DateTime)。 如果您專注於類型的行為,請考慮定義[類別](../keywords/class.md)。 類別類型具有*引言語意*。 也就是說,類類型的變數包含對類型實例的引用,而不是實例本身。

由於結構類型具有值語義,因此我們建議您定義*不可變*結構類型。

## <a name="readonly-struct"></a>`readonly`結構

從 C# 7.2`readonly`開始, 使用修飾符聲明結構類型不可變:

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

`readonly`結構的所有資料成員必須唯讀如下:

- 任何欄位聲明必須具有[`readonly`變更器](../keywords/readonly.md)
- 任何屬性(包括自動實作的屬性)都必須是唯讀的

這保證了`readonly`結構的成員不會修改結構的狀態。

> [!NOTE]
> 在`readonly`結構中,可變引用類型的數據成員仍然可以更改其自己的狀態。 例如,不能替換<xref:System.Collections.Generic.List%601>實例,但可以向實例添加新元素。

## <a name="readonly-instance-members"></a>`readonly`實體成員

從 C# 8.0 開始`readonly`,還可以使用 修改器聲明實例成員不修改結構的狀態。 如果無法將整個結構類型聲明為`readonly`,請`readonly`使用 修改器標記不修改結構狀態的實例成員。 在`readonly`結構中,每個實例成員都是隱式`readonly`的。

在實例`readonly`成員中,不能分配給結構的實例欄位。 但是,成員`readonly`可以調用非`readonly`成員。 在這種情況下,編譯器將創建結構實例的副本,並調用該副本上的非`readonly`成員。 因此,不會修改原始結構實例。

通常,您將`readonly`修改器應用於以下類型的實體成員:

- 方法:

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  還可以將`readonly`修改器應用於重寫<xref:System.Object?displayProperty=nameWithType>在 中 聲明的方法的方法:

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- 屬性與索引器:

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  如果需要將`readonly`修改器應用於屬性或索引器的兩個訪問器,請將其應用於屬性或索引器的聲明。

  > [!NOTE]
  > `get`編譯器聲明[自動實現屬性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)的訪問`readonly`許可權為`readonly`,而不考慮 屬性聲明中修飾符的存在。

不能將`readonly`修改符應用於結構類型的靜態成員。

編譯器可以使用`readonly`修改器進行性能優化。 有關詳細資訊,請參閱[編寫安全高效的 C# 代碼](../../write-safe-efficient-code.md)。

## <a name="limitations-with-the-design-of-a-structure-type"></a>結構類型設計的限制

設計結構類型時,具有與[類](../keywords/class.md)類型相同的功能,但以下情況除外:

- 不能聲明無參數構造函數。 每個結構類型都已提供一個隱式無參數建構函數,該建構函數產生類型的[預設值](default-values.md)。

- 不能在其聲明上初始化實例欄位或屬性。 但是,您可以在其聲明上初始化[靜態](../keywords/static.md)或[const](../keywords/const.md)欄位或靜態屬性。

- 結構類型的構造函數必須初始化類型的所有實例欄位。

- 結構類型不能從其他類或結構類型繼承,也不能是類的基礎。 但是,結構類型可以實現[介面](../keywords/interface.md)。

- 無法在結構型態中宣告[終結器](../../programming-guide/classes-and-structs/destructors.md)。

## <a name="instantiation-of-a-structure-type"></a>結構類型的實體化

在 C# 中,必須先初始化聲明變數,然後才能使用它。 因為結構類型變數不能`null`(除非它是可 null[值類型的](nullable-value-types.md)變數),因此必須實例化相應類型的實例。 有幾種方法可以做到這一點。

通常,通過使用運算符調用適當的構造函數來[`new`](../operators/new-operator.md)實例化結構類型。 每個結構類型至少有一個構造函數。 這是一個隱式無參數建構函數,它產生類型的[預設值](default-values.md)。 您還可以使用[預設值運算式](../operators/default.md)生成類型的預設值。

如果結構類型的所有實例欄位都可訪問,也可以在沒有`new`運算元的情況下實例化它。 在這種情況下,您必須在首次使用實例之前初始化所有實例欄位。 下列範例顯示如何執行該項工作：

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

在[內建值類型](value-types.md#built-in-value-types)的情況下,使用相應的文本指定類型的值。

## <a name="passing-structure-type-variables-by-reference"></a>透過參考傳遞結構型態變數

將結構類型變數作為參數傳遞給方法或從方法返回結構類型值時,將複製結構類型的整個實例。 這可能會影響代碼在涉及大型結構類型的高性能方案中的性能。 可以通過引用傳遞結構類型變數來避免值複製。 使用[`ref`](../keywords/ref.md#passing-an-argument-by-reference)、[`out`](../keywords/out-parameter-modifier.md)[`in`](../keywords/in-parameter-modifier.md)或方法參數修改器指示必須透過引用傳遞參數。 使用[ref 返回](../../programming-guide/classes-and-structs/ref-returns.md)通過引用返回方法結果。 有關詳細資訊,請參閱[編寫安全高效的 C# 代碼](../../write-safe-efficient-code.md)。

## <a name="conversions"></a>轉換

對於任何結構類型,都存在與和<xref:System.ValueType?displayProperty=nameWithType><xref:System.Object?displayProperty=nameWithType>類型轉換的[裝箱和取消裝箱](../../programming-guide/types/boxing-and-unboxing.md)轉換。 結構類型和它實現的任何介面之間也存在裝箱和取消裝箱轉換。

## <a name="c-language-specification"></a>C# 語言規格

有關詳細資訊,請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)的[「結構」](~/_csharplang/spec/structs.md)部分。

有關 C# 7.2 及更高版本中引入的功能的詳細資訊,請參閱以下功能建議說明:

- [唯讀結構](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [唯讀執行個體成員](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [設計指南 ─ 在類別和結構之間進行選擇](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [設計指南 - 結構設計](../../../standard/design-guidelines/struct.md)
- [類別和結構](../../programming-guide/classes-and-structs/index.md)
