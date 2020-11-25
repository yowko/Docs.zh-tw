---
title: 重大變更： Blazor： RenderTreeFrame readonly public fields 已成為屬性
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Blazor： RenderTreeFrame readonly public fields 已成為屬性
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: e9da9c538cc0a8ed4f138ef64ece0c7d144f28d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760441"
---
# <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a>Blazor： RenderTreeFrame readonly public fields 已成為屬性

在 ASP.NET Core 3.0 和3.1 中， <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> 結構會公開各種 `readonly public` 欄位，包括 <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType> 、 <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> 和其他欄位。 在 ASP.NET Core 5.0 RC1 和更新版本中，所有的 `readonly public` 欄位都會變更為 `readonly public` 屬性。

這種變更不會影響許多開發人員，因為：

* 只要使用檔案 `.razor` (或甚至是手動呼叫) 來定義其元件的任何應用程式或程式庫，都 <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> 不會直接參考此類型。
* `RenderTreeFrame`型別本身被視為是一種執行的詳細資料，而不是用於架構之外。 如果直接使用型別，ASP.NET Core 3.0 和更新版本包含的分析器會發出編譯器警告。
* 即使您直接參考 `RenderTreeFrame` ，這項變更仍是二進位檔，但不會中斷來源。 也就是說，您現有的原始程式碼會編譯並正常運作。 您只會在針對 .NET Core 3.x framework 進行編譯，然後針對 .NET 5.0 RC1 和更新版本的架構執行這些二進位檔時，才會遇到問題。

如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 25727](https://github.com/dotnet/aspnetcore/issues/25727)。

## <a name="version-introduced"></a>引進的版本

5.0 RC1

## <a name="old-behavior"></a>舊的行為

上的 Public 成員 `RenderTreeFrame` 定義為欄位。 例如，`renderTreeFrame.Sequence` 與 `renderTreeFrame.ElementName`。

## <a name="new-behavior"></a>新的行為

上的 Public 成員 `RenderTreeFrame` 定義為與之前相同名稱的屬性。 例如，`renderTreeFrame.Sequence` 與 `renderTreeFrame.ElementName`。

如果在此變更之後，舊的先行編譯器代碼尚未重新編譯，可能會擲回類似 *system.missingfieldexception：找不到欄位： ' RenderTree. RenderTreeFrame. FrameType '* 的例外狀況。

## <a name="reason-for-change"></a>變更的原因

需要進行這項變更，才能在 ASP.NET Core 5.0 的 Blazor 元件轉譯中執行高影響力效能改進。 系統會維護相同等級的安全性和封裝。

## <a name="recommended-action"></a>建議的動作

大部分的 Blazor 開發人員都不會受到這項變更的影響。 變更可能會影響媒體櫃和套件作者，但只有在罕見的情況下才會影響。 具體而言，如果您要開發：

* 應用程式和使用 ASP.NET Core 3.x 或升級至 5.0 RC1 或更新版本，您不需要變更自己的程式碼。 但是，如果您相依于升級為帳戶以進行這項變更的程式庫，則您需要更新為該程式庫的較新版本。
* 程式庫，而且只想要支援 ASP.NET Core 5.0 RC1 或更新版本，不需要採取任何動作。 請確定您的專案檔宣告 `<TargetFramework>` 的值為 `net5.0` 或更新版本。
* 程式庫，而且想要同時支援 ASP.NET Core 3.x *和* 5.0，以判斷您的程式碼是否會讀取任何 `RenderTreeFrame` 成員。 例如，評估 `someRenderTreeFrame.FrameType` 。
  * 大部分的程式庫都不會讀取 `RenderTreeFrame` 成員，包括包含元件的程式庫 `.razor` 。 在此情況下，不需要採取任何動作。
  * 但是，如果您的程式庫這樣做，則您需要多目標以支援 `netstandard2.1` 和 `net5.0` 。 將下列變更套用至您的專案檔：
    * 以取代現有的 `<TargetFramework>` 元素 `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>` 。
    * `Microsoft.AspNetCore.Components`針對您想要支援的兩個版本，請使用條件式套件參考來進行考慮。 例如：

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

如需進一步的說明，請參閱此 [差異顯示 @jsakamoto 已升級連結 `Toolbelt.Blazor.HeadElement` 庫的方式](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51)。

## <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->
