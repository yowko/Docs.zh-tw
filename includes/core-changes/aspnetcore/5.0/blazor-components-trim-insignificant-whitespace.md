---
ms.openlocfilehash: ca369c4e3f78648c6e8e0bcb5d54711d3009a769
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174255"
---
### <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a>Blazor：在編譯時期從元件修剪的空白空白字元

從 ASP.NET Core 5.0 Preview 7 開始，Razor 編譯器會在編譯時期 (*razor*檔案) 中省略 Blazor 元件中的空白空白字元。 如需討論，請參閱 issue [dotnet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 7

#### <a name="old-behavior"></a>舊的行為

在3.x 版的 Blazor 伺服器和 Blazor WebAssembly 中，在元件的原始程式碼中會接受空白字元。 只有空白字元的文位元組點會在瀏覽器的檔物件模型 (DOM) 中呈現，即使沒有視覺效果也一樣。

請考慮下列 Blazor 元件程式碼：

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

上述範例會呈現兩個空白字元節點：

* 在程式 `@foreach` 代碼區塊之外。
* 圍繞 `<li>` 元素。
* 在 `@item.Text` 輸出周圍。

包含100專案的清單會產生402個空白節點。 這不是所有呈現的節點一半，即使空白節點都不會影響轉譯的輸出。

為元件轉譯靜態 HTML 時，不會保留標記內的空白字元。 例如，請參閱下列元件的來源：

```razor
<foo        bar="baz"     />
```

不會保留空白字元。 預先呈現的輸出為：

```razor
<foo bar="baz" />
```

#### <a name="new-behavior"></a>新的行為

除非 `@preservewhitespace` 指示詞與值搭配使用 `true` ，否則會移除空白字元節點，如下所示：

* 是元素內的前置或尾端。
* 是參數內的開頭或結尾 `RenderFragment` 。 例如，將子內容傳遞至另一個元件。
* 在 c # 程式碼區塊之前或後面 `@if` ，例如和 `@foreach` 。

#### <a name="reason-for-change"></a>變更的原因

ASP.NET Core 5.0 中的 Blazor 目標是要改善轉譯和比較的效能。 無意義的空白字元樹狀節點在基準測試中耗用最多40% 的轉譯時間。

#### <a name="recommended-action"></a>建議的動作

在大部分情況下，轉譯之元件的視覺化配置不會受到影響。 不過，使用類似的 CSS 規則時，移除空白字元可能會影響轉譯的輸出 `white-space: pre` 。 若要停用此效能優化並保留空白字元，請採取下列其中一個動作：

* 在 razor 檔案頂端新增指示詞 `@preservewhitespace true` ， *.razor*以將喜好設定套用至特定元件。
* 在 `@preservewhitespace true` *_Imports razor*檔案內加入指示詞，以將喜好設定套用到整個子目錄或整個專案。

在大部分情況下，不需要採取任何動作，因為應用程式通常會繼續正常運作 (但) 更快。 如果空白字元的移除會導致特定元件發生任何問題，請 `@preservewhitespace true` 在該元件中使用來停用此優化。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!--

#### Affected APIs

Not detectable via API analysis

-->
