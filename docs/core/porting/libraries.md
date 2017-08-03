---
title: "移轉到 .NET Core - 程式庫"
description: "了解如何將程式庫專案從 .NET Framework 移植到 .NET Core。"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 07/14/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: a0fd860d-d6b6-4659-b325-8a6e6f5fa4a1
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b7cce50df0862a93c8ce144cd30965fb5b5705ed
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="porting-to-net-core---libraries"></a>移轉到 .NET Core - 程式庫

本文討論將程式庫程式碼移植到 .NET Core 來使它能跨平台執行。

## <a name="prerequisites"></a>必要條件

本文假設您已具備下列條件：

- 使用 Visual Studio 2017 或更新版本。 .NET Core 不支援較舊的 Visual Studio 版本。
- 了解[建議的移植程序](index.md)。
- 已解決任何[協力廠商相依性](third-party-deps.md)問題。

您也應該進一步熟悉下列主題的內容：

[.NET Standard](~/docs/standard/net-standard.md)   
本主題描述計畫在所有 .NET 執行階段上提供的正式 .NET API 規格。

[套件、中繼套件和架構](~/docs/core/packages.md)   
本文討論 .NET Core 如何定義及使用套件，以及套件如何支援在多個 .NET 執行階段上執行的程式碼。

[使用跨平台工具開發程式庫](~/docs/core/tutorials/libraries.md)   
本主題說明如何使用跨平台 CLI 工具撰寫 .NET 的程式庫。

[適用於 .NET Core 之 *csproj* 格式的新增項目](~/docs/core/tools/csproj.md)   
本文概述從改為使用 *csproj* 和 MSBuild 時，新增至專案檔的變更。

[移植到 .NET Core - 分析協力廠商相依性](~/docs/core/porting/third-party-deps.md)   
本主題討論協力廠商相依性的可攜性，以及當某個 NuGet 套件相依性無法在 .NET Core 上執行時的解決方法。

## <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Core 上無法使用的 .NET Framework 技術

有幾種 .NET Framework 程式庫可用的功能並無法搭配 .NET Core 使用，例如 AppDomain、遠端、程式碼存取安全性 (CAS) 和安全性透明。 如果您的程式庫會依賴一或多個這些技術，請考慮使用下述的替代方法。 如需 API 相容性的詳細資訊，請參閱 CoreFX 小組在 GitHub 上維護的[行為變更/相容性中斷及過時/舊版 API 的清單](https://github.com/dotnet/corefx/wiki/ApiCompat) \(英文\)。

目前未實作的 API或技術，並不代表我們是刻意不支援它。 在 GitHub 上的 [dotnet/corefx 存放庫問題](https://github.com/dotnet/corefx/issues) \(英文\) 頁面中提出問題，以要求特定的 API 和技術。 [移植要求的相關問題](https://github.com/dotnet/corefx/labels/port-to-core) \(英文\) 會以 `port-to-core` 標籤標記。

### <a name="appdomains"></a>AppDomain

AppDomain 可將應用程式互相隔離。 AppDomain 需要執行階段支援，且通常具有較高的成本。 該功能尚未在 .NET Core 中實作。 我們並未計畫於未來加入此功能。 若要隔離程式碼，建議使用不同的處理序或使用容器作為替代方法。 若要以動態方式載入組件，建議使用新的 <xref:System.Runtime.Loader.AssemblyLoadContext> 類別。

為了使從 .NET Framework 的程式碼移植作業更加容易，我們已公開 .NET Core 中的部分 <xref:System.AppDomain> API 介面。 某些 API 會正常運作 (例如 <xref:System.AppDomain.UnhandledException?displayProperty=fullName>)，某些成員則不會執行任何動作 (例如 <xref:System.AppDomain.SetCachePath%2A>)，而某些會擲回 <xref:System.PlatformNotSupportedException> (例如 <xref:System.AppDomain.CreateDomain%2A>)。 在 [dotnet/corefx GitHub 存放庫](https://github.com/dotnet/corefx) \(英文\) 中針對 [`System.AppDomain` 參考來源](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs) \(英文\) 檢查您使用的類型，請務必選取符合您實作版本的分支。

### <a name="remoting"></a>遠端處理

.NET 遠端處理已被識別為有問題的架構。 該功能是用於目前已不支援的跨 AppDomain 通訊。 此外，遠端處理需要執行階段支援，因此維護成本相當高昂。 基於這些原因，.NET Core 上並不支援 .NET 遠端處理，且我們也未計畫於未來支援該功能。

如需進行跨處理序通訊，請考慮使用處理序間通訊 (IPC) 機制來代替遠端處理，例如 <xref:System.IO.Pipes> 或 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> 類別。

針對跨機器通訊，請使用以網路為基礎的替代方案。 最好是使用額外負荷較低的純文字通訊協定，例如 HTTP。 [Kestrel Web 伺服器](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) \(英文\) 是 ASP.NET Core 所使用的 Web 伺服器，也是此情況下可考慮使用的選項。 針對以網路基礎的跨機器案例，也可以考慮使用 <xref:System.Net.Sockets>。 如需更多選項，請參閱 [.NET 開放原始碼開發人員專案：傳訊](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging) \(英文\)。

### <a name="code-access-security-cas"></a>程式碼存取安全性 (CAS)

需依賴執行階段或架構，來限制 Managed 應用程式或程式庫可使用或執行之資源的沙箱功能，[在 .NET Framework 上並不受支援](~/docs/framework/misc/code-access-security.md)，因此在 .NET Core 上也不受支援。 我們認為 .NET Framework 和執行階段中存在太多發生權限提高的案例，因而無法繼續將 CAS 視為安全性界線。 此外，CAS 會讓實作更為複雜，且經常會對不需要使用它的應用程式，正確性與效能之間帶來潛在的相互影響。

使用由作業系統提供的安全性界線 (例如虛擬化、容器或使用者帳戶) 來以最少的權限集合執行處理序。

### <a name="security-transparency"></a>安全性透明度

安全性透明度與 CAS 類似，允許以宣告方式區隔沙箱化程式碼和安全性關鍵程式碼，但它已[不再支援作為安全性界線](~/docs/framework/misc/security-transparent-code.md)。 Silverlight 會大量使用這項功能。 

使用由作業系統提供的安全性界線 (例如虛擬化、容器或使用者帳戶) 來以最少的權限集合執行處理序。

### <a name="globaljson"></a>global.json

*global.json* 檔案是可讓您設定專案 .NET Core 工具版本的選擇性檔案。 如果您是使用 .NET Core 的每晚建置版本，且想要指定特定版本的 SDK，請使用 *global.json* 檔案來指定版本。 它通常位於目前的工作目錄，或是它的其中一個父目錄中。 

```json
{
  "sdk": {
    "version": "2.1.0-preview1-006491"
  }
}
```

## <a name="converting-a-pcl-project"></a>轉換 PCL 專案

您可以透過在 Visual Studio 2017 中載入程式庫並執行下列步驟，以將 PCL 專案的目標轉換至 .NET Standard：

1. 以滑鼠右鍵按一下專案檔，並選取 [屬性]。
1. 在 [程式庫] 底下，選取 [目標 .NET 平台標準]。

如果您的套件支援 NuGet 3.0，專案會將目標重新設定為 .NET Standard。

如果您的套件不支援 NuGet 3.0，Visual Studio 將會顯示對話方塊，告知您將目前的套件解除安裝。 如果收到此通知，請執行下列步驟：

1. 以滑鼠右鍵按一下專案，選取 [管理 NuGet 套件]。
1. 記下該專案的套件。
1. 將套件逐一解除安裝。
1. 您可能需要重新啟動 Visual Studio 以完成解除安裝程序。 如果需要重新啟動，可以使用 [NuGet 套件管理員] 視窗中所顯示的 [重新啟動] 按鈕。
1. 當專案重新載入時，它會以 .NET Standard 為目標。 新增先前要求您解除安裝的套件。

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>將您的 .NET Framework 程式碼目標重新設定為 .NET Framework 4.6.2

如果您的程式碼目標不是 .NET Framework 4.6.2，建議您將目標重新設定為 .NET Framework 4.6.2。 這可確保在 .NET Standard 不支援現有 API 的情況下，仍可以使用最新的 API 替代項目。

針對您想要移轉的每個 Visual Studio 專案，執行下列作業︰

1. 以滑鼠右鍵按一下專案並選取 [屬性]。
1. 在 [目標 Framework] 下拉式清單中，選取 [.NET Framework 4.6.2]。
1. 重新編譯您的專案。

因為您的專案現在是以 .NET Framework 4.6.2 為目標，請使用該版本的 .NET Framework 作為基礎移植程式碼。

## <a name="determining-the-portability-of-your-code"></a>判斷程式碼的可攜性

下一個步驟是執行 API 可攜性分析器 (ApiPort)，以產生可用於分析的可攜性報告。

請確定您了解 [API 可攜性分析器 (ApiPort)](~/docs/standard/portability-analyzer.md)，以及產生目標 .NET Core 之可攜性報告的方式。 作法因個人需求及品味而異。 以下是幾種不同的方法。 根據您的程式碼架構，可以混合使用這些方法的步驟。

### <a name="dealing-primarily-with-the-compiler"></a>主要以編譯器處理

這個方法大概最適合小型專案或不使用太多 .NET Framework API 的專案。 方法相當簡單︰

1. 對專案選擇性地執行 ApiPort。 如果執行 ApiPort，請透過報告取得需解決問題的相關知識。
1. 將所有程式碼全部複製到新的 .NET Core 專案。
1. 在參考可攜性報告 (若有產生) 的同時，持續解決編譯器錯誤，直到專案可完整編譯為止。

雖然此方法不夠有條理，但以程式碼為主的方法通常可以快速解決問題，而且可能是最適合小型專案或程式庫的方法。 只包含資料模型的專案可能最適合此方法。

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>留在 .NET Framework 直到解決可攜性問題

如果您偏好在整個程序期間執行編譯的程式碼，這就是最佳方法。 方法如下所示︰

1. 對專案執行 ApiPort。
1. 使用不同的可攜式 API 來解決問題。
1. 記下您無法使用直接替代方法的所有區域。
1. 為所有要移植的專案重複上述步驟，直到確定每個專案皆已準備好複製到新的 .NET Core 專案。
1. 將程式碼複製到新的 .NET Core 專案。
1. 解決您先前所記下沒有直接替代方法的問題。

這個謹慎的方法比處理編譯器錯誤更有條理，但仍相當著重在程式碼，並具備永遠有會執行編譯之程式碼的優點。 改用其他 API 仍無法解決的問題，其解決方式差異極大。 您可能現某些專案需要開發更完善的方案，下個方法中會加以說明。

### <a name="developing-a-comprehensive-plan-of-attack"></a>開發全面的攻擊計畫

這個方法可能最適合大型且更複雜的專案，因為可能必須重新建構程式碼或完全重寫特定區域的程式碼才能支援 .NET Core。 方法如下所示︰

1. 對專案執行 ApiPort。
1. 了解每個非可攜式類型是用在程式碼的何處，以及對整體可攜性有何影響。
   - 了解這些類型的性質。 它們是否數量很少但使用頻繁？ 它們是否數量很大但很少使用？ 使用集中還是分散在整個程式碼？
   - 是否容易隔離非可攜式的程式碼，以便更輕鬆地處理它？
   - 是否需要重構程式碼？
   - 對於非可攜式的類型，是否有替代的 API 可以完成相同的工作？ 例如，如果您使用的是 <xref:System.Net.WebClient> 類別，或許可以改用 <xref:System.Net.Http.HttpClient> 類別。
   - 是否有不同的可攜式 API 可用來完成工作，即使它不是直接替換項目？ 例如，如果您是使用 <xref:System.Xml.Schema.XmlSchema> 來剖析 XML，但不需要 XML 結構描述探索，則可以使用 <xref:System.Xml.Linq> API 並自行實作剖析，而不需依靠 API。
1. 如果有難以移轉的組件，暫時留在 .NET Framework 是否值得？ 以下是要考量的事項：
   - 程式庫中可能有一些功能與 .NET Core 不相容，因為它太過依賴 .NET Framework 或 Windows 特定的功能。 是否值得先不考慮該功能，改為暫時推出功能較少的程式庫 .NET Core 版本，直到有資源可供移植該功能？
   - 重構是否會有幫助？
1. 撰寫無法使用的 .NET Framework API 自有實作是否合理？
   可以考慮複製、修改及使用來自 [.NET Framework 參考來源](https://github.com/Microsoft/referencesource) \(英文\) 的程式碼。 參考來源程式碼是依據 [MIT 授權條款](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt) \(英文\) 授權，因此您有充分的權限可以將該來源做為自己程式碼的基礎。 您只需記得在程式碼中適當地將版權歸於 Microsoft。
1. 視需要對不同的專案重複此程序。
 
分析階段可能需要一些時間，視您的程式碼基底大小而定。 在這個階段花時間徹底了解所需的變更範圍並開發計畫，通常能為未來省下許多時間，特別是在您程式碼基底較為複雜的情況下。

您的計劃可能涉及在對程式碼基底進行重大變更時仍要以 .NET Framework 4.6.2 為目標，讓它成為前一種方法更有條理的版本。 執行計畫的方式須視程式碼基底而定。

### <a name="mixing-approaches"></a>混合方法

您可能會根據每個專案混用上述各種方法。 您應該做對您和程式碼基底而言最有意義的事。

## <a name="porting-your-tests"></a>移植測試

移轉程式碼後，確定一切正常運作的最佳方式，是在將程式碼移轉到 .NET Core 時測試程式碼。 若要這樣做，您必須使用能針對 .NET Core 建置並執行測試的測試架構。 目前有三個選項︰

- [xUnit](https://xunit.github.io/)
  * [使用者入門](http://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [將 MSTest 專案轉換成 xUnit 的工具](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](http://www.nunit.org/)
  * [使用者入門](https://github.com/nunit/docs/wiki/Installation)
  * [關於從 MSTest 移轉至 NUnit 的部落格文章](http://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>建議的移植方法

不管如何，移植工作都會大幅取決於 .NET Framework 程式碼的架構方式。 移植程式碼的良好方式，是從程式庫的「基底」開始，也就是程式碼的基本元件。 它可能是資料模型，也可能是所有其他項目會直接或間接使用的基礎類別和方法。

1. 針對測試目前正在移植之程式庫層的測試專案進行移植。
1. 將程式庫的基底複製到新的 .NET Core 專案，然後選取您想要支援的 .NET Standard 版本。
1. 進行任何必要的變更，令程式碼執行編譯。 此工作有很大一部分可能會需要將 NuGet 套件相依性新增到 *csproj* 檔案中。
1. 執行測試並進行任何必要的調整。
1. 挑選要移植的下一層程式碼，並重複上述步驟。

如果您是從程式庫基底向外進行移植，並視需要測試每一層，移植將會是個系統化的程序，並將所有問題都隔離在單層的程式碼內。

