---
title: 相依性與 .NET 程式庫
description: 在 .NET 程式庫中管理 NuGet 相依性的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: c5df30c606e77c9ef44387233b0072ab890f612f
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2018
ms.locfileid: "49400526"
---
# <a name="dependencies"></a>相依性

將相依性新增至 .NET 程式庫的主要方式是參考 NuGet 套件。 雖然 NuGet 套件參考能讓您快速地重複使用並運用已撰寫的功能，但它們也是造成 .NET 開發人員間摩擦的常見原因。 若要避免在其他 .NET 程式庫中所做的變更造成您的 .NET 程式庫中斷 (反之亦然)，正確地管理相依性便顯得非常重要！

## <a name="diamond-dependencies"></a>菱形相依性

.NET 專案在其相依性樹狀結構中經常會有相同套件的多個版本。 例如，某個應用程式會相依於兩個 NuGet 套件，而每個套件都會相依於相同套件的不同版本。 這使得應用程式的相依性關係圖中存在菱形相依性。

![菱形相依性](./media/dependencies/diamond-dependency.png "菱形相依性")

在建置期間，NuGet 會分析專案相依的所有套件，包含相依性的相依性。 偵測到相同套件的多個版本時，系統會評估規則以從中挑選。 整合套件是必要的，因為在相同的應用程式中同時執行某個組件的多個版本，勢必會在 .NET 中產生問題。

雖然大部分的菱形相依性都很容易解決，但它們可能會在某些情況下造成問題：

1. **衝突的 NuGet 套件參考**會防止系統在套件還原期間解析某個版本。
2. **版本之間的中斷性變更**會在執行階段造成錯誤和例外狀況。
3. **套件組件具有強式名稱**、組件版本已變更，且應用程式是在 .NET Framework 上執行。 需要進行組件繫結重新導向。

您不可能得知其他人會將您的套件搭配哪些套件使用。 一個降低菱形相依性中斷您程式庫之機會的良好方式，便是將您所相依之套件的數目降到最低。

**✔️ 請務必**檢閱您的 .NET 程式庫，以找出非必要的相依性。

## <a name="nuget-dependency-version-ranges"></a>NuGet 相依性版本範圍

套件參考能指定其所允許之有效套件的範圍。 通常，專案檔案中的套件參考版本指的是最小版本，且沒有最大版本。

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

NuGet 用來解決相依性的規則非常[複雜](/nuget/consume-packages/dependency-resolution)，但 NuGet 一律會尋找最低的適用版本。 NuGet 之所以會偏好使用最低適用版本，而非最高版本的原因，是因為最低版本的相容性問題最少。

基於 NuGet 的最低適用版本規則，我們並不需要在套件參考上放置較高版本或確切範圍來避免取得最新的版本。 因為 NuGet 已經會嘗試為您找出最低且最具相容性的版本。

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

較高版本限制會在發生衝突時造成 NuGet 失敗。 例如，某個程式庫僅接受 1.0 版，而另一個程式庫則需要 2.0 版或更新版本。 雖然 2.0 版可能會出現中斷性變更，嚴格或較高限制版本相依性將一定會造成錯誤。

![菱形相依性衝突](./media/dependencies/diamond-dependency-conflict.png "菱形相依性衝突")

**❌ 請勿**使用沒有最小版本的 NuGet 套件參考。

**❌ 請避免**要求明確版本的 NuGet 套件參考。

**❌ 請避免**使用具有版本較高限制的 NuGet 套件參考。

## <a name="nuget-shared-source-packages"></a>NuGet 共用的來源套件

其中一個降低外部 NuGet 套件相依性的方式，是參考共用的來源套件。 共用的來源套件包含[原始程式碼檔案](/nuget/reference/nuspec#including-content-files)，這些檔案會在被參考時包含在專案中。 因為您只是包含與專案其餘部分一起編譯的原始程式碼檔案，所以不會有任何外部相依性，也不會有發生衝突的機會。

共用的來源套件很適合用來包含較小的功能片段。 例如，適用於進行 HTTP 呼叫之協助程式的共用來源套件。

![共用的來源套件](./media/dependencies/shared-source-package.png "共用的來源套件")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![共用的來源專案](./media/dependencies/shared-source-project.png "共用的來源專案")

共用的來源套件有一些限制。 它們只能由 `PackageReference` 參考，因此會排除較舊的 `packages.config` 專案。 此外，共用的來源套件只適用於具有相同語言類型的專案。 因為這些限制，共用的來源套件最適合在開放原始碼專案內共用功能時使用。

**✔️ 請考慮**針對較小的內部功能片段使用共用的來源套件。

**✔️ 請考慮**在套件提供的是較小的內部功能片段的情況下，使它成為共用的來源套件。

**✔️ 請務必**搭配 `PrivateAssets="All"` 參考共用的來源套件。

> 此設定能告訴 NuGet 該套件僅適用於開發階段，且不應該公開為公用相依性。

**❌ 請勿**在您的公用 API 中包含共用的來源套件類型。

> 共用來源類型會編譯為參考組件，且不能跨越組件界線進行交換。 例如，某個專案中的共用來源 `IRepository` 類型，與另一個專案中相同的共用來源 `IRepository` 將會是完全不同的類型。 共用來源套件中的類型應該僅具有 `internal` 可見性。

**❌ 請勿**將共用的來源套件發佈至 nuget.org。

> 共用的來源套件包含原始程式碼，而且只能用於具有相同語言類型的專案。 例如，以 F# 撰寫的應用程式將無法使用以 C# 撰寫的共用來源套件。

>[!div class="step-by-step"]
[上一頁](./nuget.md)
[下一頁](./sourcelink.md)
