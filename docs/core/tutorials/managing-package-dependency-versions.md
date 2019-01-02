---
title: 如何管理 .NET Core 1.0 的套件相依性版本
description: 了解您的 .NET Core 程式庫和應用程式的套件相依性版本管理。
author: cartermp
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 7d7133ddb8717db1b830e531955454925c31a728
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168607"
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a>如何管理 .NET Core 1.0 的套件相依性版本

本文章涵蓋您需要知道有關 .NET Core 程式庫和應用程式套件版本的資訊。

## <a name="glossary"></a>字彙表

**修正** - 修正相依性表示，您會使用在 NuGet 上發行、適用於 .NET Core 1.0 的相同系列套件。

**中繼套件** - NuGet 套件，代表一組 NuGet 套件。

**修剪** - 從中繼套件移除不依賴之套件的動作。  這與 NuGet 套件作者有關。  如需詳細資訊，請參閱[減少與 project.json 的套件相依性](../deploying/reducing-dependencies.md)。 

## <a name="fix-your-dependencies-to-net-core-10"></a>將相依性固定為 .NET Core 1.0

若要可靠地還原套件，並撰寫可靠的程式碼，很重要的一點是將相依性固定為與 .NET Core 1.0 一起出貨的套件版本。  這表示每個套件應該有單一版本，而且不含任何額外的限定詞。

**固定為 1.0 的套件範例**

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

**未固定為 1.0 的套件範例**

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a>這為什麼重要？

我們保證，如果您將相依性固定為與 .NET Core 1.0 一起出貨的項目時，那些套件將一起運作。 如果您使用未以此方式固定的套件，則沒有這種保證。

### <a name="scenarios"></a>案例

雖然與 .NET Core 1.0 一起發行的所有套件和其版本清單冗長，但如果您的程式碼落在特定狀況下，可能不必看完整份清單。

**您是否只依賴** `NETStandard.Library`**？**

如果是，您應該將 `NETStandard.Library` 套件固定為 `1.6` 版。  因為這是策劃的中繼套件，其套件終止也會固定為 1.0。

**您是否只依賴** `Microsoft.NETCore.App`**？**

如果是，您應該將 `Microsoft.NETCore.App` 套件固定為 `1.0.0` 版。  因為這是策劃的中繼套件，其套件終止也會固定為 1.0。

**您是否[修剪](../deploying/reducing-dependencies.md)您的** `NETStandard.Library` **或** `Microsoft.NETCore.App` **中繼套件相依性？**

如果是，您應該確定您啟動用的中繼套件固定為 1.0。  修剪之後依賴的個別套件也會固定為 1.0。

**您是否依賴** `NETStandard.Library` **或** `Microsoft.NETCore.App` **中繼套件之外的套件？**

如果是，您需要將其他相依性固定為 1.0。  如需正確的套件版本和組建號碼，請參閱在本文結尾。

### <a name="a-note-on-using-a-splat-string--when-versioning"></a>版本控制時，使用 splat 字串 (\*) 的注意事項

您採用的版本控制模式可能是使用 splat (\*) 字串，就像這樣︰`"System.Collections":"4.0.11-*"`。

**您不應該這麼做**。  使用 splat 字串可能會導致從不同的組建還原套件，這些組建有些可能比 .NET Core 1.0 更遠。  這可能導致某些套件不相容。

## <a name="packages-and-version-numbers-organized-by-metapackage"></a>依中繼套件組織的套件和版本號碼

[所有 .NET Standard 套件和其適用於 1.0 的版本清單](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt)。

[所有執行階段套件和其適用於 1.0 的版本清單](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt)。

[所有 .NET Core 應用程式套件和其適用於 1.0 的版本清單](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt)。
