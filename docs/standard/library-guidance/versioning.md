---
title: 版本控制與 .NET 程式庫
description: .NET 程式庫版本控制的最佳做法建議。
ms.date: 01/26/2021
ms.openlocfilehash: 1f3a14a7c32091621dda30a2d86724915d629564
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794723"
---
# <a name="versioning"></a>版本控制

軟體程式庫在 1.0 版中通常還不完整。 良好的程式庫會隨著時間而演進、新增功能、修正錯誤，以及提升效能。 您必須發行新版的 .NET 程式庫，為每個版本提供額外的價值，而不會中斷現有的使用者。

## <a name="breaking-changes"></a>重大變更

如需處理版本之間中斷性變更的相關資訊，請參閱[中斷性變更](./breaking-changes.md)。

## <a name="version-numbers"></a>版本號碼

.NET 程式庫有許多方式可以指定版本。 這些版本是最重要的：

### <a name="nuget-package-version"></a>NuGet 套件版本

[NuGet 套件版本](/nuget/reference/package-versioning)會顯示在 NuGet.org (Visual Studio NuGet 套件管理員) 上，並在使用套件時加入至原始程式碼。 NuGet 套件版本是使用者通常會看到的版本號碼，當他們討論他們所使用的程式庫版本時，他們會提及它。 NuGet 會使用 NuGet 套件版本，且對執行階段行為沒有影響。

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

NuGet 套件識別碼與 NuGet 套件版本結合，可用來識別 NuGet 中的套件。 例如：`Newtonsoft.Json` + `11.0.2`。 帶有後置詞的套件是發行前版本套件，且具有特殊的行為，很適合用於測試。 如需詳細資訊，請參閱[發行前版本套件](./nuget.md#pre-release-packages)。

因為 NuGet 套件版本是開發人員最明顯的版本，所以使用[語意版本控制 (SemVer)](https://semver.org/) 更新它是個不錯的主意。 SemVer 指出版本之間變更的重要性，並可協助開發人員在選擇要使用哪一個版本時，做出明智的決定。 例如，從 `1.0` 到 `2.0` 表示可能有潛在的中斷性變更。

✔️ 考慮使用 [SemVer 2.0.0](https://semver.org/) 來設定 NuGet 套件的版本。

✔️ 請務必在公用文件中使用 NuGet 套件版本，因為它是使用者通常會看到的版本號碼。

✔️ 請務必包含發行前版本尾碼 (當發行非穩定套件時)。

> 使用者必須選擇取得發行前版本套件，以便他們了解套件不完整。

### <a name="assembly-version"></a>組件版本

元件版本是 CLR 在執行時間用來選取要載入的元件版本。 使用版本設定選取組件僅適用於具有強式名稱的組件。

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

.NET Framework CLR 會要求完全相符，以載入強式名稱的元件。 例如，`Libary1, Version=1.0.0.0` 編譯時參考了 `Newtonsoft.Json, Version=11.0.0.0`。 .NET Framework 只會載入確切的版本 `11.0.0.0` 。 若要在執行時間載入不同的版本，必須將系結重新導向新增至 .NET 應用程式的設定檔。

強式命名與組件版本相結合，可啟用[嚴格的組件版本載入](../assembly/versioning.md)。 雖然強式命名程式庫有許多優點，但通常會導致找不到元件的執行時間例外狀況，而且必須在或中修正系結重新 [導向](../../framework/configure-apps/redirect-assembly-versions.md) `app.config` `web.config` 。 在 .NET Core 中，元件載入更寬鬆。 .NET Core 執行時間會在執行時間自動載入具有較高版本的元件。

✔️ 考慮只在 AssemblyVersion 中包括主要版本。

> 例如，Library 1.0 與 Library 1.0.1 的 AssemblyVersion 都為 `1.0.0.0`，而 Library 2.0 的 AssemblyVersion 為 `2.0.0.0`。 當組件版本變更頻率較低時，它可減少繫結重新導向。

✔️ 考慮將 AssemblyVersion 與 NuGet 套件版本的主要版本號碼保持同步。

> AssemblyVersion 包含在向使用者顯示的一些參考用訊息中，例如，例外狀況訊息中的組件名稱與組件限定類型名稱。 維護版本之間的關聯性，可為開發人員提供有關他們使用之版本的詳細資訊。

❌請勿使用固定的 AssemblyVersion。

> 雖然不會變更的 AssemblyVersion 避免了繫結重新導向的需要，但這表示只能在全域組件快取 (GAC) 中安裝單一版本的組件。 此外，如果另一個應用程式使用中斷性變更更新 GAC 組件，則參考 GAC 中組件的應用程式將中斷。

### <a name="assembly-file-version"></a>組件檔版本

元件檔案版本是用來顯示 Windows 中的檔案版本，不會影響執行時間行為。 是否設定此版本是選擇性的。 它會顯示在 Windows 檔案總管的 [檔案內容] 對話方塊中：

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Windows 檔案總管](./media/versioning/win-properties.png "Windows 檔案總管")

✔️ 考慮包括持續整合組建編號作為 AssemblyFileVersion 修訂。

> 例如，您正在建置版本 1.0.0 的專案，且持續整合組建編號是 99，因此您的 AssemblyFileVersion 是 1.0.0.99。

✔️ 針對檔案版本，請使用 `Major.Minor.Build.Revision` 格式。

> 雖然 .NET 永遠不會使用檔案版本，但 [Windows 預期檔案版本](/windows/desktop/menurc/versioninfo-resource)的格式為 `Major.Minor.Build.Revision`。 如果版本未遵循此格式，則會引發警告。

### <a name="assembly-informational-version"></a>組件資訊版本

組件資訊版本用於記錄其他版本資訊，對執行階段行為沒有影響。 是否設定此版本是選擇性的。 如果您正在使用來源連結，則此版本將在組建時使用 NuGet 套件版本加上原始檔控制版本進行設定。 例如，`1.0.0-beta1+204ff0a` 包括組件建置來源之原程式始碼的認可雜湊。 如需詳細資訊，請參閱[來源連結](./sourcelink.md)。

```xml
<InformationalVersion>The quick brown fox jumped over the lazy dog.</InformationalVersion>
```

> [!NOTE]
> 如果此版本未遵循 `Major.Minor.Build.Revision` 格式，則舊版的 Visual Studio 會引發建置警告。 您可以安心略過該警告。

❌避免設定您自己的組件資訊版本。

> 允許 SourceLink 自動產生包含 NuGet 與原始檔控制中繼資料的版本。

>[!div class="step-by-step"]
>[上一個](publish-nuget-package.md) 
>[下一步](breaking-changes.md)
