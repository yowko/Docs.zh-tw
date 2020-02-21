---
title: 屬性
description: 瞭解屬性F#如何讓中繼資料套用至程式設計結構。
ms.date: 02/19/2020
ms.openlocfilehash: 77b84713ab9360166b3634d406993cf209c8a623
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543634"
---
# <a name="attributes"></a>屬性

屬性可讓中繼資料套用至程式設計結構。

## <a name="syntax"></a>語法

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>備註

在先前的語法中，*目標*是選擇性的，如果有的話，則會指定要套用屬性的程式實體類型。 *Target*的有效值會顯示在本檔稍後所顯示的表格中。

*屬性名稱*是指有效屬性類型的名稱（可能是以命名空間限定），而不含後置字元 `Attribute` 通常用於屬性類型名稱。 例如，您可以將類型 `ObsoleteAttribute` 縮短為在此內容中 `Obsolete`。

*引數*是屬性類型之函式的引數。 如果屬性具有無參數的函式，則可以省略引數清單和括弧。 屬性同時支援位置引數和具名引數。 *位置引數*是以它們出現的順序來使用的引數。 如果屬性具有公用屬性，則可以使用具名引數。 您可以使用引數清單中的下列語法來設定這些參數。

```fsharp
property-name = property-value
```

這類屬性初始化可以依任何順序排列，但必須遵循任何位置引數。 以下是使用位置引數和屬性初始化的屬性範例：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

在此範例中，屬性是 `DllImportAttribute`，這裡以縮短的形式使用。 第一個引數是位置參數，而第二個是屬性。

屬性是一種 .NET 程式設計結構，可讓稱為*屬性*的物件與型別或其他程式元素產生關聯。 套用屬性的程式元素稱為*屬性目標*。 屬性通常包含其目標的相關中繼資料。 在此內容中，中繼資料可能是除了其欄位和成員以外類型的任何資料。

中F#的屬性可以套用至下列程式設計結構：函式、方法、元件、模組、類型（類別、記錄、結構、介面、委派、列舉、等位等等）、程式（attribute）、屬性（property）、欄位、參數、型別參數和傳回值。 屬性不允許用於類別、運算式或工作流程運算式中的 `let` 系結。

一般而言，屬性宣告會直接出現在屬性目標的宣告前面。 可以同時使用多個屬性宣告，如下所示：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

您可以在執行時間使用 .NET 反映來查詢屬性。

如先前的程式碼範例所示，您可以個別宣告多個屬性，或者，如果您使用分號來分隔個別屬性和構造函式，則可以在一組方括弧中宣告它們，如下所示：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

通常遇到的屬性包括 `Obsolete` 屬性、安全性考慮的屬性、COM 支援的屬性、與程式碼擁有權相關的屬性，以及指出類型是否可以序列化的屬性。 下列範例示範 `Obsolete` 屬性的用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

針對 `assembly` 和 `module`的屬性目標，您可以將屬性套用至元件中的最上層 `do` 系結。 您可以在屬性宣告中包含 `assembly` 或 `module` 這一字，如下所示：

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

如果您省略套用至 `do` 系結之屬性的屬性目標，則F#編譯器會嘗試判斷對該屬性有意義的屬性目標。 許多屬性類別都具有類型 `System.AttributeUsageAttribute` 的屬性，其中包含該屬性所支援之可能目標的相關資訊。 如果 `System.AttributeUsageAttribute` 指出屬性支援以函式作為目標，則會採用屬性以套用至程式的主要進入點。 如果 `System.AttributeUsageAttribute` 指出屬性支援將元件當做目標，則編譯器會採用屬性以套用至元件。 大部分的屬性都不會同時套用至函式和元件，但在這些情況下，會採用屬性以套用至程式的 main 函式。 如果明確指定屬性目標，則會將屬性套用至指定的目標。

雖然您通常不需要明確指定屬性目標，但在屬性中， *target*的有效值和使用方式範例如下表所示：

<table>
  <tr>
    <th>屬性目標</td>
    <th>範例</td>
  </tr>
  <tr>
    <td>組件 (assembly)</td>
    <td><pre><code class="lang-fsharp">[&lt;assembly: AssemblyVersion("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td>return</td>
    <td><pre><code class="lang-fsharp">let function1 x : [&lt;return: MyCustomAttributeThatWorksOnReturns&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td>field</td>
    <td><pre><code class="lang-fsharp">[&lt;DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td>屬性</td>
    <td><pre><code class="lang-fsharp">[&lt;Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td>參數</td>
    <td><pre><code class="lang-fsharp">member this.MyMethod([&lt;Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td>type</td>
    <td>
        <pre><code class="lang-fsharp">
[&lt;type: StructLayout(LayoutKind.Sequential)&gt;]
type MyStruct =
  struct
    val x : byte
    val y : int
  end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
