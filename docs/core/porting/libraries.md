---
title: "移轉到 .NET Core - 程式庫 | Microsoft Docs"
description: "移轉到 .NET Core - 程式庫"
keywords: ".NET、.NET Core"
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: a0fd860d-d6b6-4659-b325-8a6e6f5fa4a1
ms.translationtype: Human Translation
ms.sourcegitcommit: 9cd469dfd4f38605f1455c008388ad04c366e484
ms.openlocfilehash: 271720298d6432e9fed9ef757df2000c5b7d2482
ms.contentlocale: zh-tw
ms.lasthandoff: 06/20/2017

---

# 移轉到 .NET Core - 程式庫
<a id="porting-to-net-core---libraries" class="xliff"></a>

使用 .NET Core 1.0 版本時，有機會移轉現有的程式庫程式碼，讓它可以跨平台執行。 本文討論 .NET 標準程式庫、無法使用的技術、如何說明 .NET Core 1.0 上提供的較少 API、如何使用 .NET Core SDK Preview 2 隨附的工具，以及移轉程式碼的建議作法。

移轉可能需要一些時間，尤其是當您有大型的程式碼基底時。 您也應該在此視需要準備採用最適合您程式碼的指引。 每個程式碼基底都不相同，因此本文嘗試以彈性的方式規範項目，但您可能會發現自己需要偏離規定的指引。

## 必要條件
<a id="prerequisites" class="xliff"></a>

本文假設您在 Windows 上使用 Visual Studio 2017 或更新版本。 舊版 Visual Studio 不提供建置 .NET Core 程式碼所需的位元。

本文也假設您了解[建議移轉程序](index.md)，並已解決所有[協力廠商相依性](third-party-deps.md)問題。

## 以 .NET 標準程式庫為目標
<a id="targeting-the-net-standard-library" class="xliff"></a>

建置 .NET Core 跨平台程式庫的最佳辦法，是以 [.NET Standard](../../standard/net-standard.md) 為目標。 .NET 標準程式庫是計劃提供所有 .NET 執行階段使用的 .NET API 正式規格。 受 .NET Core 執行階段支援。

這表示，您必須在可以使用的 API 與可以支援的平台之間作出取捨，並挑選最適合所要取捨的 .NET Standard 平台版本。

目前有 7 種不同的版本要考慮︰.NET Standard 1.0 到 1.6。 如果您選擇較新的版本，就可以存取較多的 API，代價是在較少的目標上執行。 如果您選擇較舊的版本，程式碼可以在較多的目標上執行，代價是可用的 API 較少。

為了方便起見，以下是每個 .NET Standard 版及其執行所在的各特定區域的交叉表︰

| 平台名稱 | Alias |  |  |  |  |  | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1.5 | 1.6 |
|.NET 核心|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|4.6.3|
|Mono/Xamarin 平台||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|*|
|通用 Windows 平台|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|||
|Windows|win|&rarr;|8.0|8.1|||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1|||||
|Windows Phone Silverlight|wp|8.0|||||||

了解重點：**以較舊版本為目標的專案無法參考以較新版本為目標的專案**。 例如，以 .NET Standard 平台 1.2 版為目標的專案無法參考以 .NET Standard 平台 1.3 或更新版本為目標的專案。 但是專案**可以**參考較舊的版本，因此以 .NET Standard 平台 1.3 為目標的專案可以參考以 .NET Standard 平台 1.2 或較舊版本為目標的專案。

建議您選擇可能的最低 .NET Standard 版本，整個專案都使用這個版本。

深入了解 [.NET 平台標準程式庫](../../standard/net-standard.md)。

## .NET Standard 或 .NET Core 尚未提供關鍵技術
<a id="key-technologies-not-yet-available-on-the-net-standard-or-net-core" class="xliff"></a>

您使用的某些技術可能是 .NET Framework 提供，但目前 .NET Core 不提供。 下列小節各自對應其中一項技術。 可以採用的替代選項就會列出。

### 應用程式定義域
<a id="app-domains" class="xliff"></a>

AppDomain 在 .NET Framework 上可用於不同用途。 若要隔離程式碼，建議選擇使用不同的程序及/或容器。 若要以動態方式載入組件，建議使用新的 @System.Runtime.Loader.AssemblyLoadContext 類別。

### 遠端處理
<a id="remoting" class="xliff"></a>

若要跨處理序通訊，可以使用處理序間通訊 (IPC) 機制替代遠端處理，例如[管道](https://docs.microsoft.com/dotnet/core/api/system.io.pipes)或[記憶體對應檔案](https://docs.microsoft.com/dotnet/core/api/system.io.memorymappedfiles.memorymappedfile)。

跨電腦可以選擇使用網路型解決方案，最好是低額外負荷的純文字通訊協定，如 HTTP。 在此可以選擇 ASP.NET Core 使用的 Web 伺服器 [KestrelHttpServer](https://github.com/aspnet/KestrelHttpServer)。 也可以考慮選擇透過 [Castle.Core](https://github.com/castleproject/Core) 產生遠端 Proxy。

### 二進位序列化
<a id="binary-serialization" class="xliff"></a>

若要替代二進位序列化，有多種不同的序列化技術可供選擇。 您應該選擇一種適合您格式和使用量目標的技術。 熱門選項包括︰

* JSON 為 [JSON.NET](http://www.newtonsoft.com/json)
* XML 及 JSON 皆可使用 @System.Runtime.Serialization.DataContractSerializer
* XML 為 @System.Xml.Serialization.XmlSerializer
* 通訊協定緩衝區為 [protobuf net](https://github.com/mgravell/protobuf-net)

請參閱連結資源，以了解它們的優點，並選擇符合您需求的項目。 另有許多其他序列化格式與技術，其中有許多是開放原始碼。

### 沙箱
<a id="sandboxes" class="xliff"></a>

沙箱的替代方案可以使用作業系統提供的安全性界限，例如以最少權限組執行處理序的使用者帳戶。

## `project.json` 概觀
<a id="overview-of-projectjson" class="xliff"></a>

[project.json 專案模型](../tools/project-json.md)是隨附於 .NET Core SDK 1.0 Preview 2 的專案模型。 您現在可能想要利用它的某些優勢︰

* 簡單的多目標，可從單一組建產生特定目標組件。
* 能夠使用專案組建輕鬆產生 NuGet 封裝。
* 不必列出專案檔中的檔案。
* 統一 NuGet 封裝相依性以及專案對專案相依性。

> 雖然最終會淘汰 `project.json`，但現在仍可用來在 .NET Standard 上建置程式庫。

### 專案檔：`project.json`
<a id="the-project-file-projectjson" class="xliff"></a>

.NET Core 專案是由包含 `project.json` 檔案的目錄所定義。 這個檔案是各層面皆宣告的專案，如封裝相依性、編譯器設定、執行階段設定等等。

`dotnet restore` 命令會讀取此專案檔、還原專案所有相依性，以及產生 `project.lock.json` 檔案。 此檔案包含組建系統建置專案所需的所有必要資訊。

若要深入了解 `project.json` 檔案，請參閱 [project.json 參考](../tools/project-json.md)。

### 方案檔：`global.json`
<a id="the-solution-file-globaljson" class="xliff"></a>

`global.json` 檔案是選擇性檔案，以納入包含多個專案的方案。 它通常位在專案集的根目錄中。 它可用來通知組建系統可包含專案的不同子目錄。 這適合由數個專案組成的較大型系統。

例如，您可以將程式碼組織到最上層的 `/src` 和 `/test` 資料夾，像這樣︰

```json
{
    "projects":[ "src", "test" ]
}
```

然後，將多個 `project.json` 檔案放在 `/src` 和 `/test` 自己的子資料夾內。

### 如何使用 `project.json` 設定多目標
<a id="how-to-multitarget-with-projectjson" class="xliff"></a>

有許多程式庫設定多目標以盡可能廣伸觸角。 使用 .NET Core，設定多目標是「一等公民」，表示您可以使用單一組建輕鬆產生特定平台的組件。

設定多目標就像將正確的目標 Framework Moniker (TFM) 加入到 `project.json` 檔案中一樣簡單，每個目標使用正確的相依性 (.NET Core 是 `dependencies`，.NET Framework 是 `frameworkAssemblies`)，也可以使用 `#if` 指示詞有條件地編譯原始程式碼供特定平台 API 使用。

例如，假設您要建置一個程式庫，在此執行某些網路作業，而且希望此程式庫能在所有 .NET Framework 版本、可攜式類別庫 (PCL) 設定檔和 .NET Core 上執行。 .NET Core 和 .NET Framework 4.5+ 的目標可以使用 `System.Net.Http` 程式庫和 `async`/`await`。 但是舊版的 .NET Framework 無法使用這些 API。

以下是 `project.json` 的範例 `frameworks` 區段，其目標為 .NET Framework 2.0、3.5、4.0、4.5 版以及 .NET Standard 1.6：

```javascript
{
    "frameworks":{
        "net20":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net35":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net40":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net45":{
            "frameworkAssemblies":{
                "System.Net.Http":"",
                "System.Threading.Tasks":""
            }
        },
        ".NETPortable,Version=v4.5,Profile=Profile259": {
            "buildOptions": {
                "define": [ "PORTABLE" ]
             },
             "frameworkAssemblies":{
                 "mscorlib":"",
                 "System":"",
                 "System.Core":"",
                 "System.Net.Http":""
             }
        },
        "netstandard16":{
            "dependencies":{
                "NETStandard.Library":"1.6.0",
                "System.Net.Http":"4.0.1",
                "System.Threading.Tasks":"4.0.11"
            }
        },
    }
}
```

請注意，PCL 的目標很特殊︰它們需要您指定組建定義供編譯器辨識，而且需要您指定使用的全部組件，包括 `mscorlib`。

然後原始程式碼就可以使用相依性，像這樣︰

```csharp
#if (NET20 || NET35 || NET40 || PORTABLE)
using System.Net;
#else
using System.Net.Http;
using System.Threading.Tasks;
#endif
```

請注意，所有 .NET Framework 及 .NET Standard 的目標都有編譯器辨識的名稱︰

```
.NET Framework 2.0   --> NET20
.NET Framework 3.5   --> NET35
.NET Framework 4.0   --> NET40
.NET Framework 4.5   --> NET45
.NET Framework 4.5.1 --> NET451
.NET Framework 4.5.2 --> NET452
.NET Framework 4.6   --> NET46
.NET Framework 4.6.1 --> NET461
.NET Framework 4.6.2 --> NET462
.NET Standard 1.0    --> NETSTANDARD1_0
.NET Standard 1.1    --> NETSTANDARD1_1
.NET Standard 1.2    --> NETSTANDARD1_2
.NET Standard 1.3    --> NETSTANDARD1_3
.NET Standard 1.4    --> NETSTANDARD1_4
.NET Standard 1.5    --> NETSTANDARD1_5
.NET Standard 1.6    --> NETSTANDARD1_6
```

如上所述，如果您的目標是 PCL，則必須指定編譯器了解的組建定義。 沒有編譯器可以使用的任何預設定義。

### 在 Visual Studio 中使用 `project.json`
<a id="using-projectjson-in-visual-studio" class="xliff"></a>

在 Visual Studio 中使用 `project.json` 有兩個選項︰

1. 新的 xproj 專案類型。
2. 支援 .NET Standard 的重定目標 PCL 專案。

各有優缺點。

#### 挑選 Xproj 專案的時機
<a id="when-to-pick-an-xproj-project" class="xliff"></a>

Visual Studio 中的新 Xproj 專案系統利用 `project.json` 專案模型的各種功能，在現有的專案類型上提供兩大功能︰組建多個組件以順暢設定多目標，以及能夠直接在組建上產生 NuGet 封裝。

不過，代價是缺少可能用到的某些功能，例如︰

- F# 或 Visual Basic 支援
- 產生有當地語系化資源字串的附屬組件
- 直接參考檔案系統上的 `.dll` 檔案
- 能在參考管理員中參考 csproj 型專案 (但取決於是否直接支援 `.dll` 檔案)

如果您的專案需求相對較小，而且可以利用 xproj 的新功能，您應該挑選它作為專案系統。 在 Visual Studio 中完成此作業，如下所示︰

1. 確定使用的是 Visual Studio 2015 或更新版本。
2. 選取 [檔案] | [新增專案]。
3. 選取 Visual C# 下的 ".NET Core"。
4. 選取 "Class Library (.NET Core)" 範本。 

#### 挑選 PCL 專案的時機
<a id="when-to-pick-a-pcl-project" class="xliff"></a>

藉由建立可攜式類別庫 (PCL)，並在 [專案組態] 對話方塊中選取 [.NET Core]，您可以在 Visual Studio 中設定使用傳統專案系統的 .NET Core 為目標。 然後，您必須在 .NET Standard 上將用作基礎的專案重新設定為目標︰

1. 以滑鼠右鍵按一下 Visual Studio 中的專案檔案，然後選取 [內容]。
2. 在 [組建] 下，選取 「Convert to .NET Standard」 (轉換為 .NET Standard)。

如有進階的專案系統需求，這應該就是您的選擇。 請注意，如果想要透過產生特定平台組件來設定多目標，像使用 `xproj` 專案系統，您需要建立「誘導轉向」PCL，如 [How to Make Portable Class Libraries Work for You](https://blogs.msdn.microsoft.com/dsplaisted/2012/08/27/how-to-make-portable-class-libraries-work-for-you/) (如何讓可攜式類別庫為您工作) 中所述。

## 將 .NET Framework 程式碼重定目標為 .NET Framework 4.6.2
<a id="retargeting-your-net-framework-code-to-net-framework-462" class="xliff"></a>

如果您的程式碼目標不是 .NET Framework 4.6.2，建議您重新設定目標。 這可確保當 .NET Standard 不支援現有的 API 時，您能使用最新的 API 替代項目。

針對您想要移轉的每個 Visual Studio 專案，執行下列作業︰

1. 以滑鼠右鍵按一下專案，選取 [內容]。
2. 在 [目標 Framework] 下拉式清單中選取 [.NET Framework 4.6.2]。
3. 重新編譯您的專案。

就是這麼容易！ 因為您的專案現在是以 .NET Framework 4.6.2 為目標，所以您可以使用該版 .NET Framework 作為基礎移轉程式碼。

## 判斷程式碼的可攜性
<a id="determining-the-portability-of-your-code" class="xliff"></a>

下一個步驟是執行 API 可攜性分析器 (ApiPort)，以產生可以開始分析的可攜性報告。

您必須確定您了解 [API 可攜性工具 (ApiPort)](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/)，而且可以產生以 .NET Core 為目標的可攜性報告。 作法因個人需求及品味而異。 下面是幾個不同的方法，您可能會發現自己混用了各種方法，視您的程式碼結構而定。

### 主要以編譯器處理
<a id="dealing-primarily-with-the-compiler" class="xliff"></a>

這個方法大概最適合小型專案或不使用太多 .NET Framework API 的專案。 方法很簡單︰

1. 對專案選擇性執行 ApiPort。
2. 如果已執行 ApiPort，快速瀏覽報表。
3. 將所有程式碼全部複製到新的 .NET Core 專案。
4. 解決編譯器錯誤直到完成編譯，如有需要請參考可攜性報表。
5. 視需要重複執行。

雖然此方法不夠有條理，但以程式碼為主的方法可以快速解決任何問題，而且可能是最適合小型專案或程式庫的方法。 只包含資料模型的專案可能是理想的選項。

### 留在 .NET Framework 直到可攜性問題解決
<a id="staying-on-the-net-framework-until-portability-issues-are-resolved" class="xliff"></a>

如果您偏好在整個程序期間執行編譯的程式碼，這就是最佳方法。 方法如下所示︰

1. 對專案執行 ApiPort。
2. 使用不同的可攜式 API 解決問題。
3. 記下任何不能使用直接替代方案的區域。
4. 為所有移轉的專案重複步驟 1-3，直到確定每個專案皆可複製到 .NET Core 專案。
5. 將程式碼複製到新的 .NET Core 專案。
6. 解決所有記下的問題。

這個謹慎的方法比只處理編譯器錯誤更有條理，但仍相當著重在程式碼，其優點是永遠有可編譯的程式碼。 某些換個 API 無法解決的問題，其解決方式差異極大。 您可能現某些專案需要開發更完善的方案，下個方法中會加以說明。

### 開發全面的攻擊計劃
<a id="developing-a-comprehensive-plan-of-attack" class="xliff"></a>

這個方法可能最適合大型且更複雜的專案，因為可能必須重新建構程式碼或重寫特定區域才能支援 .NET Core。 方法如下所示︰

1. 對專案執行 ApiPort。
2. 了解每個非可攜式類型用在程式碼何處，以及對整體可攜性有何影響。

   a. 了解這些類型的性質。 它們數量很少但使用頻繁嗎？ 它們數量很大但很少使用嗎？ 使用集中還是分散在整個程式碼？
   
   b. 是不是非可攜式的程式碼容易隔離，所以您可以更輕鬆地處理它？
   
   c.  您需要重構程式碼嗎？
   
   d. 對於非可攜式的類型，是否有替代的 API 可以完成相同的工作？ 例如，如果您使用的是 `WebClient` 類別，可以改用 `HttpClient` 類別。
   
   e. 有不同的可攜式 API 可用來完成工作嗎，即使它不是直接替換項目？ 例如，如果使用 `XmlSchema` 協助剖析 XML，但不需要 XML 結構描述探索，您可以使用 `System.Linq.Xml` API 手動剖析資料。

3. 如果有難以移轉的組件，暫時留在 .NET Framework 是否值得？ 以下是要考量的事項：

   a. 程式庫中可能有一些功能與 .NET Core 不相容，因為它太過依賴 .NET Framework 或 Windows 特定功能。 目前暫時拋開該功能，改用功能較少的.NET Core 版程式庫是否值得？
   
   b. 重構在此是否有所助益？
   
4. 撰寫無法使用的 .NET Framework API 自有實作是否合理？

   可以考慮改用複製、修改及使用 [.NET Framework 參考來源](https://github.com/Microsoft/referencesource)的程式碼。 它在 [MIT 授權](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt) 中授權，所以您可以自由執行這項作業。 只要確定在程式碼中正確定義 Microsoft 屬性！
   
5. 視需要對不同的專案重複此程序。
6. 計劃好後，請執行該計劃。
 
分析階段可能需要一些時間，視您的程式碼基底大小而定。 花時間在這個階段徹底了解所需的變更範圍以及開發計劃，可以省下未來許多時間，特別是如果您的程式碼基底較為複雜。

您的計劃可能涉及在對程式碼基底進行重大變更時仍要以 .NET Framework 4.6.2 為目標，讓它成為前一種方法更有條理的版本。 如何執行計劃，視程式碼基底而定。

### 混合方法
<a id="mixing-approaches" class="xliff"></a>

您可能會根據每個專案混用上述各種方法。 您應該做對您和程式碼基底而言最有意義的事。

## 移轉測試
<a id="porting-your-tests" class="xliff"></a>

移轉程式碼後，確定一切正常運作的最佳方式，是在將程式碼移轉到 .NET Core 時測試程式碼。 若要這樣做，您必須使用會建置及執行 .NET Core 測試的測試架構。 目前有三個選項︰

* [xUnit](https://xunit.github.io/)
   - [使用者入門](http://xunit.github.io/docs/getting-started-dotnet-core.html)
   - [將 MSTest 專案轉換成 xUnit 的工具](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
* [NUnit](http://www.nunit.org/)
  - [使用者入門](https://github.com/nunit/docs/wiki/Installation)
  - [關於從 MSTest 移轉至 NUnit 的部落格文章](http://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
* [MSTest](https://msdn.microsoft.com/library/ms243147.aspx)

## 建議的移轉方法
<a id="recommended-approach-to-porting" class="xliff"></a>

最後，移轉程式碼！ 最終的移轉代價主要取決於 .NET Framework 程式碼的結構方式。 以下是建議的方法，非常適合您的程式碼基底。

移轉程式碼的好方法是從程式庫的「基底」開始。 這可以是資料模型，或某些其他項目直接或間接使用的其他基本類別和方法。

1. 移轉測試專案，此專案會測試目前移轉中的程式庫圖層。
2. 將程式庫的「基底」複製到新的 .NET Core 專案，然後選取您想要支援的 .NET Standard 版本。
3. 進行任何必要的變更，令程式碼執行編譯。 此工作的大部分需要將 NuGet 封裝相依性加入 `project.json` 檔案中。
4. 執行測試並進行任何必要的調整。
5. 挑選下一層要移轉的程式碼，並重複步驟 2 和 3！

如果您有條理地從程式庫基底外移，並視需要測試每一層，移轉就會是系統化的程序，問題會一次隔離至一層程式碼。

