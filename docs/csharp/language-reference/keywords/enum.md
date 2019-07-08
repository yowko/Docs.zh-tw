---
title: enum 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 57043963640f3c384b1e1a9aa7aeb65114689e9f
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569527"
---
# <a name="enum-c-reference"></a>enum (C# 參考)

`enum` 關鍵字用來宣告列舉，是包含一組稱為列舉程式清單之具名常數的不同類型。

通常最好在命名空間內直接定義列舉，使得命名空間中的所有類別可以同樣便利地存取列舉。 不過，列舉也可以巢狀於類別或結構中。

根據預設，第一個列舉程式的值是 0，而每個後續列舉程式的值會遞增 1。 例如，在下列的列舉中， `Sat` 是 `0`， `Sun` 是 `1`， `Mon` 是 `2`，依此類推。

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

列舉程式可使用初始設定式覆寫預設值，如下列範例所示。

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

在這個列舉中，項目的順序會強制從 `1` 開始，而不是 `0`。 不過，建議加入值為 0 的常數。 如需詳細資訊，請參閱[列舉類型](../../programming-guide/enumeration-types.md)。

每個列舉型別都具有基礎型別，它可以是任何[整數數字型別](../builtin-types/integral-numeric-types.md)。 [Char](char.md) 型別不能是列舉的基礎型別。 預設基礎列舉項目類型是 [int](../builtin-types/integral-numeric-types.md)。若要宣告另一個整數類型的列舉，例如 [byte](../builtin-types/integral-numeric-types.md)，請在識別項後使用冒號，後面接著類型，如下列範例所示。

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

型別為列舉的變數可以指派為底層類型範圍中的任何值；該值不限於具名常數。

`enum E` 的預設值是 `(E)0`運算式所產生的值。

> [!NOTE]
> 列舉程式名稱中不能包含空白字元。

基礎類型指定為每個列舉程式配置的儲存體數量。 不過，從 `enum` 類型轉換為整數類型需要明確轉換。 例如，下列陳述式會指派列舉程式 `Sun` 為 [int](../builtin-types/integral-numeric-types.md) 類型的變數，方法是使用轉換從 `enum` 轉換成 `int`。

```csharp
int x = (int)Day.Sun;
```

當您將 <xref:System.FlagsAttribute?displayProperty=nameWithType> 套用至包含可與位元 `OR` 作業結合之項目的列舉時，這個屬性會影響 `enum` 與某些工具一起使用時的行為。 當您使用如 <xref:System.Console> 類別方法和運算式評估工具等工具時，您可以注意到這些變更。 (請參閱第三個範例。)

## <a name="robust-programming"></a>穩固程式設計

如同任何常數，對列舉之個別值的所有參考都會在編譯時期轉換成數值常值。 這有可能產生潛在的版本控制問題，如[常數](../../programming-guide/classes-and-structs/constants.md)中所述。

將額外的值指派給新版本的列舉，或變更新版本中列舉成員的值時，可能會造成相依原始碼的問題。 列舉值通常用於 [switch](switch.md) 陳述式。 如果已將其他項目加入 `enum` 類型中，可能會意外選取 switch 陳述式的預設區段。

如果其他開發人員使用您的程式碼，您應該提供詳細指引，說明當新項目加入任何 `enum` 類型中時，其程式碼應該要如何回應。

## <a name="example"></a>範例

在下列範例中，宣告了 `Day`列舉。 兩個列舉程式已明確轉換成整數，並指派給整數變數。

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>範例

在下列範例中，基底類型選項會用來宣告 `enum` ，其成員類型是 `long`。 請注意，即使列舉的基礎類型是 `long`，列舉成員仍必須使用轉換來明確地轉換成 `long` 類型。

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>範例

下列程式碼範例說明如何在 <xref:System.FlagsAttribute?displayProperty=nameWithType> 宣告上使用 `enum` 屬性與其效果。

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>註解

如果您移除 `Flags`，此範例就會顯示下列值︰

`5`

`5`

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [列舉型別](../../programming-guide/enumeration-types.md)
- [C# 關鍵字](index.md)
- [整數型別](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [內建型別表](built-in-types-table.md)
- [隱含數值轉換表](implicit-numeric-conversions-table.md)
- [明確數值轉換表](explicit-numeric-conversions-table.md)
- [列舉命名慣例](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
