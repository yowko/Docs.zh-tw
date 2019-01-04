---
title: 版本控制與 .NET 程式庫
description: .NET 程式庫版本控制的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 12/10/2018
ms.openlocfilehash: e47b8a5ccad7c57d125e16f6e1d37fb91de31161
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169595"
---
# <a name="versioning"></a>版本控制

軟體程式庫在 1.0 版中通常還不完整。 良好的程式庫會隨著時間演進、新增功能、修正錯誤 (Bug) 並改善效能。 您必須發行新版的 .NET 程式庫，為每個版本提供額外的價值，而不會中斷現有的使用者。

## <a name="breaking-changes"></a>重大變更

如需處理版本之間中斷性變更的相關資訊，請參閱[中斷性變更](./breaking-changes.md)。

## <a name="version-numbers"></a>版本號碼

.NET 程式庫有許多方式可以指定版本。 這些版本是最重要的：

### <a name="nuget-package-version"></a>NuGet 套件版本

[NuGet 套件版本](/nuget/reference/package-versioning)會顯示在 NuGet.org (Visual Studio NuGet 套件管理員) 上，並在使用套件時加入至原始程式碼。 NuGet 套件版本是使用者通常會看到的版本號碼，當他們討論他們所使用的程式庫版本時，他們會提及它。 NuGet 會使用 NuGet 套件版本，且對執行階段行為沒有影響。

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

NuGet 套件識別碼與 NuGet 套件版本結合，可用來識別 NuGet 中的套件。 例如，`Newtonsoft.Json` + `11.0.2`。 帶有後置詞的套件是發行前版本套件，且具有特殊的行為，很適合用於測試。 如需詳細資訊，請參閱[發行前版本套件](./nuget.md#pre-release-packages)。

因為 NuGet 套件版本是開發人員最明顯的版本，所以使用[語意版本控制 (SemVer)](https://semver.org/) 更新它是個不錯的主意。 SemVer 指出版本之間變更的重要性，並可協助開發人員在選擇要使用哪一個版本時，做出明智的決定。 例如，從 `1.0` 到 `2.0` 表示可能有潛在的中斷性變更。

**✔️ 考慮**使用 [SemVer 2.0.0](https://semver.org/) 來設定 NuGet 套件的版本。

**✔️ 請務必**在公用文件中使用 NuGet 套件版本，因為它是使用者通常會看到的版本號碼。

**✔️ 請務必**包含發行前版本尾碼 (當發行非穩定套件時)。

> 使用者必須選擇取得發行前版本套件，以便他們了解套件不完整。

### <a name="assembly-version"></a>組件版本

組件版本是 CLR 在執行階段使用以選取要載入之組件版本的方式。 使用版本設定選取組件僅適用於具有強式名稱的組件。

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

Windows.NET Framework CLR 會要求完全相符，以載入強式名稱組件。 例如，`Libary1, Version=1.0.0.0` 編譯時參考了 `Newtonsoft.Json, Version=11.0.0.0`。 .NET Framework 將只會載入該確切版本 `11.0.0.0`。 若要在執行階段載入不同的版本，必須將繫結重新導向新增至 .NET 應用程式的設定檔中。

強式命名與組件版本相結合，可啟用[嚴格的組件版本載入](../../framework/app-domains/assembly-versioning.md)。 雖然為程式庫進行強式命名有很多好處，但它通常會導致無法找到組件的執行階段例外狀況，而且[要求修復 `app.config`/`web.config` 中的繫結重新導向](../../framework/configure-apps/redirect-assembly-versions.md)。 .NET Core 組件載入已經放寬，.NET Core CLR 將在更高版本的執行階段自動載入組件。

**✔️ 考慮**只在 AssemblyVersion 中包括主要版本。

> 例如，Library 1.0 與 Library 1.0.1 的 AssemblyVersion 都為 `1.0.0.0`，而 Library 2.0 的 AssemblyVersion 為 `2.0.0.0`。 當組件版本變更頻率較低時，它可減少繫結重新導向。

**✔️ 考慮**將 AssemblyVersion 與 NuGet 套件版本的主要版本號碼保持同步。

> AssemblyVersion 包含在向使用者顯示的一些參考用訊息中，例如，例外狀況訊息中的組件名稱與組件限定類型名稱。 維護版本之間的關聯性，可為開發人員提供有關他們使用之版本的詳細資訊。

**❌ 請勿**使用固定的 AssemblyVersion。

> 雖然不會變更的 AssemblyVersion 避免了繫結重新導向的需要，但這表示只能在全域組件快取 (GAC) 中安裝單一版本的組件。 此外，如果另一個應用程式使用中斷性變更更新 GAC 組件，則參考 GAC 中組件的應用程式將中斷。

### <a name="assembly-file-version"></a>組件檔版本

組件檔版本用於顯示 Windows 中的檔案版本，對執行階段行為沒有影響。 是否設定此版本是選擇性的。 它會顯示在 Windows 檔案總管的 [檔案內容] 對話方塊中：

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Windows 檔案總管](./media/versioning/win-properties.png "Windows 檔案總管")

**✔️ 考慮**包括持續整合組建編號作為 AssemblyFileVersion 修訂。

> 例如，您正在建置版本 1.0.0 的專案，且持續整合組建編號是 99，因此您的 AssemblyFileVersion 是 1.0.0.99。

**✔️ 針對檔案版本，請**使用 `Major.Minor.Build.Revision` 格式。

> 雖然 .NET 永遠不會使用檔案版本，但 [Windows 預期檔案版本](/windows/desktop/menurc/versioninfo-resource)的格式為 `Major.Minor.Build.Revision`。 如果版本未遵循此格式，則會引發警告。

### <a name="assembly-informational-version"></a>組件資訊版本

組件資訊版本用於記錄其他版本資訊，對執行階段行為沒有影響。 是否設定此版本是選擇性的。 如果您正在使用 SourceLink，則此版本將在建置時使用 NuGet 套件版本加上原始檔控制版本進行設定。 例如，`1.0.0-beta1+204ff0a` 包括組件建置來源之原程式始碼的認可雜湊。 如需詳細資訊，請參閱 [SourceLink](./sourcelink.md)。

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> 如果此版本未遵循 `Major.Minor.Build.Revision` 格式，則舊版的 Visual Studio 會引發建置警告。 您可以安心略過該警告。

**❌ 避免**自行設定組件資訊版本。

> 允許 SourceLink 自動產生包含 NuGet 與原始檔控制中繼資料的版本。

>[!div class="step-by-step"]
>[上一頁](publish-nuget-package.md)
>[下一頁](breaking-changes.md)
