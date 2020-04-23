---
title: 將 WPF 應用移到 .NET 核心 3.0
description: 瞭解如何將 Windows 演示文稿基礎 (WPF) 應用遷移到 .NET Core 3.0。
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: f52005e7c8a6312b8c4e09a950f1f635af1894e4
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "82071308"
---
# <a name="migrating-wpf-apps-to-net-core"></a>將 WPF 應用移到 .NET 核心

本文介紹將 Windows 演示文稿基礎 (WPF) 應用從 .NET 框架遷移到 .NET Core 3.0 所需的步驟。 如果您手頭沒有 WPF 應用,但希望嘗試此過程,則可以使用[GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader)上可用的**Bean Trader**範例套用 。 原始應用程式(目標 .NET 框架 4.7.2)可在 NetFx_BeanTraderClient 資料夾中使用。 首先,我們將解釋移植應用程式所需的步驟,然後介紹適用於**Bean Trader**示例的特定更改。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

要遷移到 .NET 核心,必須首先:

01. 瞭解並更新 NuGet 相依:

    01. 升級 NuGet 依賴`<PackageReference>`項以 使用格式。
    01. 查看 .NET 核心或 .NET 標準相容性的頂級 NuGet 依賴項。
    01. 將 NuGet 包升級到較新版本。
    01. 使用[.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md)瞭解 .NET 依賴項。

01. 將專案檔案移到新的 SDK 樣式格式:

    01. 選擇是同時定位 .NET 核心和 .NET 框架,還是僅定位 .NET 核心。
    01. 將相關的專案檔屬性和項複製到新專案檔。

01. 修復產生問題:

    01. 添加對[Microsoft.Windows.相容性](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/)包的引用。
    01. 查找並修復 API 級別差異。
    01. 刪除`appSettings``connectionStrings`或以外的*應用.config*部分。
    01. 如有必要,重新生成生成的代碼。

01. 執行時測試:

    01. 確認移植的應用按預期工作。
    01. 注意<xref:System.NotSupportedException>例外情況。

## <a name="about-the-sample"></a>關於範例

本文引用[Bean Trader 範例應用](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader),因為它使用各種依賴項,類似於現實世界的 WPF 應用可能具有的依賴項。 該應用程式並不大,但在複雜性方面,它意味著從"你好世界"中邁出一步。 該應用程式演示了使用者在移植實際應用時可能會遇到的一些問題。 該應用程式與 WCF 服務通訊,因此要正常執行,您還需要運行 BeanTraderServer 專案(在同一 GitHub 儲存庫中可用),並確保 BeanTraderClient 配置指向正確的終結點。 (預設情況下,該範例假定伺服器在的同一台電腦上運行,*http://localhost:8090*如果您在本地啟動 BeanTraderServer,則為 true。

請記住,此示例應用旨在演示 .NET Core 移植挑戰和解決方案。 它不是要演示 WPF 最佳實踐。 事實上,它故意包括一些反模式,以確保你在移植時至少遇到幾個有趣的挑戰。

## <a name="getting-ready"></a>準備就緒

將 .NET Framework 應用遷移到 .NET Core 的主要挑戰是其依賴項可能以不同的方式工作,或者根本不工作。 遷移比過去容易得多;許多 NuGet 套件現在都針對 .NET 標準。 從 .NET Core 2.0 開始,.NET 框架和 .NET 核心曲面區域變得相似。 即便如此,仍然存在一些差異(在 NuGet 包和可用的 .NET API 中支援方面)。 遷移的第一步是查看應用的依賴項,並確保引用的格式易於遷移到 .NET Core。

### <a name="upgrade-to-packagereference-nuget-references"></a>升級到`<PackageReference>`NuGet 引用

較舊的 .NET 框架專案通常在*包*中列出其 NuGet 依賴項。 新的 SDK 樣式的專案檔案格式將[`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files)NuGet 套件作為 csproj 檔本身中的元素引用,而不是在單獨的設定檔中。

移轉時,使用`<PackageReference>`-style 引用有兩個優點:

- 這是新的 .NET Core 專案檔所需的 NuGet 引用樣式。 如果您已在使用`<PackageReference>`,則可以將這些專案檔元素直接複製並粘貼到新專案中。
- 與包.config 檔`<PackageReference>`不同 ,元素僅引用專案直接依賴的頂級依賴項。 所有其他傳遞 NuGet 包將在還原時確定,並記錄在自動生成的 obj_project.assets.json 檔中。 這樣可以更輕鬆地確定專案具有哪些依賴項,這在確定必要的依賴項是否適用於 .NET Core 上非常有用。

將 .NET Framework 應用遷移到 .NET Core 的第`<PackageReference>`一步是更新它以 使用 NuGet 引用。 視覺工作室使這一點變得簡單。 只需右鍵單擊 Visual Studio**的解決方案資源管理器**中的*包.config*檔,然後選擇 **「遷移包.config 到包參考**」。

![升級到包參考](./media/convert-project-from-net-framework/package-reference-migration.png)

將顯示一個對話框,顯示計算的頂級 NuGet 依賴項,並詢問應將哪些其他 NuGet 包提升到頂級。 這些其他包都不需要是 Bean Trader 範例的頂級,因此您可以取消選中所有這些框。 然後,按下 **「確定」** 並刪除*包.config*檔`<PackageReference>`,並將元素添加到專案檔中。

`<PackageReference>`-樣式引用不會將 NuGet 套件本地儲存在套件資料夾中。 相反,它們作為優化存儲在全域。 移轉完成後,編輯 csproj 檔並刪除參考`<Analyzer>`以前來自的分析器的任何元素 *。\包*目錄。 別擔心,由於您仍然具有 NuGet 包引用,因此分析器將包含在專案中。 你只需要清理舊包。 `<Analyzer>`

### <a name="review-nuget-packages"></a>檢視 NuGet 套件

現在,您可以看到項目所依賴的頂級 NuGet 包,您可以查看這些包是否在 .NET Core 上可用。 您可以通過查看包對[nuget.org](https://www.nuget.org/)的依賴項來確定包是否支援 .NET Core。社區創建的[fuget.org](https://www.fuget.org/)網站在包信息頁面頂部醒目地顯示此資訊。

當定位 .NET Core 3.0 時,任何針對 .NET Core 或 .NET 標準包都應工作(因為 .NET Core 實現了 .NET 標準表面積)。 在某些情況下,所使用的包的特定版本不會針對 .NET Core 或 .NET 標準,但較新版本將面向. 在這種情況下,應考慮升級到最新版本的包。

您也可以使用針對 .NET 框架的包,但這會帶來一些風險。 .NET Core 到 .NET 框架依賴項是允許的,因為 .NET Core 和 .NET 框架曲面區域足夠相似,因此此類依賴項*通常*工作。 但是,如果包嘗試使用 .NET Core 中不存在的 .NET API,則會遇到運行時異常。 因此,您應該僅在沒有其他選項可用時引用 .NET Framework 包,並瞭解這樣做會帶來測試負擔。

如果引用的包不針對 .NET Core 或 .NET 標準,則必須考慮其他備選方案:

- 是否有其他類似的軟體包可以代替使用? 有時 NuGet 作者發佈單獨的」。核心的庫版本專門針對 .NET Core。 企業庫包是社區發佈的一個示例」。NetCore"替代方案。 在其他情況下,對於 .NET標準,可用於特定服務的較新的 SDK(有時具有不同的包名)。 如果沒有可用的替代方案,則可以繼續使用 .NET Framework 目標包,同時請記住,在 .NET Core 上運行後,需要對其進行徹底測試。

Bean 交易者範例具有以下頂級 NuGet 相依:

- [**城堡.溫莎,版本 4.1.1**](https://www.castleproject.org/projects/windsor/)  

  此包以 .NET 標準 1.6 為目標,因此適用於 .NET 核心。

- [**微軟.代碼分析.FxCopAnalyzers,版本2.6.3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  這是一個元包,因此它支援哪些平臺並不立即明顯,但[文檔](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers)表明其最新版本 (2.9.2) 將同時適用於 .NET 框架和 .NET Core。

- [**Nito.AsyncEx,版本 4.0.1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  此包不針對 .NET Core,但較新的 5.0 版本支援. 遷移時很常見,因為許多 NuGet 包最近添加了 .NET 標準支援,但較舊的專案版本將僅針對 .NET 框架。 如果版本差異只是一個較小的版本差異,則通常很容易升級到較新版本。 由於這是一個重大版本更改,因此需要謹慎升級,因為包中可能會有重大更改。 不過,有一條前進的道路,這很好。

- [**MahApps.Metro,版本 1.6.5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  此包也不針對 .NET Core,但有較新的預發行版本 (2.0-alpha)。 同樣,你必須留意重大的變化,但較新的軟體包是令人鼓舞的。

Bean Trader 範例的 NuGet 依賴項都針對 .NET 標準/.NET Core,或者具有較新版本,因此這裡不太可能存在任何阻塞問題。

### <a name="upgrade-nuget-packages"></a>升級 NuGet 套件

如果可能,最好升級僅針對 .NET Core 或 .NET 標準的任何包的版本,此時更新版本(專案仍以 .NET Framework 為目標),以便及早發現和解決任何重大更改。

如果您不希望對應用的現有 .NET Framework 版本進行任何實質性更改,則可以等到您有針對 .NET Core 的新專案檔。 但是,提前將 NuGet 包升級到 .NET Core 相容版本,一旦創建新的專案檔並減少應用 .NET Framework 和 .NET Core 版本之間的差異,遷移過程就變得更加容易。

使用 Bean Trader 範例,所有必要的升級都可以輕鬆進行(使用 Visual Studio 的 NuGet 軟體包管理器),但有一個例外:從**MahApps.Metro 1.6.5**升級到**2.0**揭示了與主題和重音管理 API 相關的重大更改。

理想情況下,應用將更新以使用包的較新版本(因為這更有可能適用於 .NET Core)。 然而,在某些情況下,這可能不可行。 在這些情況下,不要升級**MahApps.Metro,** 因為必要的更改是非瑣碎的,本教程側重於遷移到 .NET Core 3,而不是**MahApps.Metro 2。** 此外,這是一個低風險 .NET 框架依賴項,因為 Bean Trader 應用程式只行使**MahApps.Metro 的**一小部分。 當然,它將需要測試,以確保遷移完成後一切工作。 如果這是一個真實的場景,最好提交一個問題來跟蹤工作移動到**MahApps.Metro**版本2.0,因為不做遷移現在留下一些技術債務。

將 NuGet 套件更新到最新版本後,「Bean `<PackageReference>` Trader」範例的專案檔中的專案組應如下所示。

```xml
<ItemGroup>
  <PackageReference Include="Castle.Windsor">
    <Version>4.1.1</Version>
  </PackageReference>
  <PackageReference Include="MahApps.Metro">
    <Version>1.6.5</Version>
  </PackageReference>
  <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers">
    <Version>2.9.2</Version>
  </PackageReference>
  <PackageReference Include="Nito.AsyncEx">
    <Version>5.0.0</Version>
  </PackageReference>
</ItemGroup>
```

### <a name="net-framework-portability-analysis"></a>.NET 框架可移植性分析

瞭解專案的 NuGet 依賴項的狀態後,需要考慮的下一件事是 .NET Framework API 依賴項。 [.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md)工具可用於瞭解專案使用的 .NET API 在其他 .NET 平臺上可用。

該工具作為[Visual Studio 外掛程式](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer),[一個命令列工具](https://github.com/Microsoft/dotnet-apiport/releases),或包裝在一[個簡單的 GUI,](https://github.com/Microsoft/dotnet-apiport-ui)這簡化了它的選項。 您可以閱讀有關使用 .NET 可移植性分析器 (API 連接埠) 在[將桌面應用移植到 .NET Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/)部落格文章中的 GUI 的詳細資訊。 如果希望使用命令行,則必要的步驟是:

1. 如果您還沒有[.NET 可移植性分析器](https://github.com/Microsoft/dotnet-apiport/releases),請下載它。
1. 確保成功移植 .NET Framework 應用(無論在遷移之前,這是一個好主意)。
1. 使用這樣的命令列運行 API 連接埠。

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    參數`-f`指定包含要分析的二進位檔案的路徑。 參數`-r`指定所需的輸出檔格式。 參數`-t`指定要針對哪個 .NET 平臺分析 API 使用方式。 在這種情況下,您需要 .NET 核心。

打開 HTML 報表時,第一部分將列出所有分析的二進位檔案,以及他們使用的 .NET API 的百分比在目標平臺上可用。 這個百分比本身沒有意義。 更有用的是查看缺少的特定 API。 為此,請選擇程式集名稱或向下滾動到各個程式集的報表。

關注您擁有的原始碼的程式集。 例如,在 Bean Trader ApiPort 報告中,列出了許多二進位檔,但大多數都屬於 NuGet 包。 `Castle.Windsor`顯示它依賴於 .NET Core 中缺少的某些 System.Web API。 這不是問題,因為您以前已驗證支援`Castle.Windsor`.NET Core。 NuGet 套件具有不同的二進位檔案用於不同的 .NET 平臺是很常見的,因此,只要包也`Castle.Windsor`針對 .NET 標準或 .NET Core(它這樣做),.NET 框架版本是否使用 System.Web API 都無關緊要。

使用 Bean Trader 表示例時,您需要考慮的唯一二進位檔案是**BeanTraderClient,** 報告顯示`System.ServiceModel.ClientBase<T>.Close`僅缺少兩`System.ServiceModel.ClientBase<T>.Open`個 .NET API: 和 。

![豆交易用戶端可移植性報告](./media/convert-project-from-net-framework/portability-report.png)

這些不太可能阻止問題,因為 WCF 用戶端 API(大部分)在 .NET Core 上受支援,因此必須為這些中央 API 提供替代方案。 事實上,查看`System.ServiceModel`.NET 核心表面積<https://apisof.net>(使用 ),您會看到 .NET Core 中有異步替代方案。

基於此報告和以前的 NuGet 依賴項分析,似乎不應存在將 Bean Trader 範例遷移到 .NET Core 的大問題。 您已準備好下一步,在此步驟中,您將實際開始遷移。

## <a name="migrating-the-project-file"></a>移轉專案檔

如果你的應用沒有使用新的[SDK 風格的專案檔案格式](../../core/tools/csproj.md),則需要一個新的專案檔來定位 .NET Core。 您可以替換現有的 csproj 檔,或者,如果您希望保持現有專案保持其當前狀態不變,則可以添加針對 .NET Core 的新 csproj 檔。 您可以使用具有[多目標的](../../standard/library-guidance/cross-platform-targeting.md)單個 SDK 樣式專案檔`<TargetFrameworks>`(指定多個目標)為 .NET 框架和 .NET Core 構建應用版本。

要建立新的專案檔,可以在 Visual Studio 中建立新的 WPF 專案,或者`dotnet new wpf`使用暫存目錄中的命令生成專案檔,然後將其複製/重命名到正確的位置。 還有一個社區創建的工具[,CsprojToVs2017,](https://github.com/hvanbakel/CsprojToVs2017)它可以自動執行一些專案檔遷移。 該工具很有用,但仍需要人工查看結果,以確保遷移的所有詳細資訊都正確無誤。 此工具無法將最好處理的特定區域是從包遷移 NuGet 套件 *。* 如果該工具在仍使用*包.config*檔案引用 NuGet 套件的專案檔上運行,它將`<PackageReference>`自動遷移到 元素,但`<PackageReference>`會為所有包添加*all*元素,而不僅僅是頂級 包的元素。 如果您已經遷移到`<PackageReference>`了使用 Visual Studio 的元素(如本示例中所做的那樣),則該工具可以説明完成轉換的其餘部分。 像斯科特·漢塞爾曼[在他的博客文章中建議遷移csproj檔](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx),手工移植是教育性的,如果你只有幾個專案移植,將提供更好的結果。 但是,如果您移植了幾十個或數百個專案檔,那麼像 [CprojToVs2017] 這樣的工具可能是一個説明。

要為 Bean Trader 範例建立新的項目`dotnet new wpf`檔,請執行暫存目錄中,並將產生的 *.csproj*檔案移動到*BeanTraderClient*資料夾中,並將其重新命名為**BeanTraderClient.Core.csproj**。

由於新的項目檔格式自動包括 C# 檔 *、resx*檔和 XAML 檔,它在其目錄中或在其目錄下找到,因此專案檔已幾乎完成! 要完成移轉,請並排打開新舊專案檔,並查看舊專案檔以查看是否需要遷移其中包含的任何資訊。 在「豆交易」示例案例中,應將以下專案複製到新專案:

- 全部`<RootNamespace>`應`<AssemblyName>`複製`<ApplicationIcon>`和屬性。

- 您還需要向新專案檔添加`<GenerateAssemblyInfo>false</GenerateAssemblyInfo>`屬性,因為 Bean Trader 範例在 AssemblyInfo.cs 檔中包含`[AssemblyTitle]`程式集級屬性(如 )。"屬性"。 默認情況下,新的 SDK 樣式專案將根據 csproj 檔中的屬性自動生成這些屬性。 由於在這種情況下不希望這種情況發生(自動產生的屬性將與AssemblyInfo.cs的屬性衝突),因此使用關閉自動產生的屬性`<GenerateAssemblyInfo>`。

- 儘管*resx*檔自動作為嵌入資源包含`<Resource>`在內 ,但其他專案(如圖像)則不包括在內。 因此,`<Resource>`複製嵌入影像和圖示檔案的元素。 您可以使用新項目檔案格式對 globing 模式的支援來簡化對單行的 png`<Resource Include="**\*.png" />`引用: 。

- 同樣,`<None>`專案會自動包含,但默認情況下不會將其複製到輸出目錄。 由於 Bean Trader`<None>`專案 包含*複製到*輸出目錄(使用`PreserveNewest`行為)的專案,因此您需要更新`<None>`該檔自動填充的項,如下所示。

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- Bean Trader 範例包括 XAML 檔 (Default.Accent.xaml) 作為`Content`(`Page`而不是作為 ),因為在此檔案中定義的主題和重音在執行時從檔案的 XAML 載入,而不是嵌入到應用本身中。 但是,新項目系統會自動將此檔作為`<Page>`,因為它是 XAML 檔。 因此,您需要同時刪除 XAML 檔作為`<Page Remove="**\Default.Accent.xaml" />`頁面 ( ), 並將其添加為內容。

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- 最後,通過複製`<ItemGroup>`所有`<PackageReference>`元素來添加 NuGet 引用。 如果您以前沒有將 NuGet 包升級到 .NET Core 相容版本,則現在可以執行此操作,因為包引用位於 .NET Core 特定的專案中。

此時,應該可以將新專案添加到 BeanTrader 解決方案並在 Visual Studio 中打開它。 專案在**解決方案資源管理器**中應看起來正確,`dotnet restore BeanTraderClient.Core.csproj`並應成功還原包(與 MahApps.Metro 版本相關的兩個預期警告,您使用的定位目標 .NET Framework)。

儘管可以同時保留兩個專案檔(如果要保持舊專案完全按照現在的身份構建,甚至可能是可取的),但它使遷移過程複雜化(這兩個專案將嘗試使用相同的 bin 和 obj 資料夾),通常沒有必要。 如果要同時為 .NET Core 和 .NET 框架`<TargetFramework>netcoreapp3.0</TargetFramework>``<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>`目標生成,則可以改為替換新專案檔中的屬性。 對於 Bean Trader 範例,請刪除舊專案檔(BeanTraderClient.csproj),因為它不再需要。 如果您希望保留這兩個專案檔,請確保將它們構建到不同的輸出和中間輸出路徑。

## <a name="fix-build-issues"></a>修復產生問題

移植過程的第三步是生成專案。 一旦專案檔轉換為 SDK 樣式的專案,某些應用將成功生成。 如果你的應用如此,恭喜你! 您可以繼續執行步驟 4。 其他應用將需要一些更新,以使它們為 .NET Core 構建。 如果您嘗試現在`dotnet build`運行 Bean Trader 範例專案(例如,或在 Visual Studio 中建譯),將有許多錯誤,但很快就會修復它們。

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>系統.服務模型引用和微軟.Windows.相容性

常見的錯誤來源是缺少可用於 .NET Core 但未自動包含在 .NET Core 應用元包中的 API 的引用。 為此,應引用該`Microsoft.Windows.Compatibility`包。 相容性包包括 Windows 桌面應用中常見的廣泛 API 集,例如 WCF 用戶端、目錄服務、註冊表、配置、ACL API 等。

使用 Bean Trader 範例,大多數生成錯誤<xref:System.ServiceModel>是由於缺少 類型造成的。 這些可以通過引用必要的 WCF NuGet 套件來解決。 但是,WCF 用戶端 API 是`Microsoft.Windows.Compatibility`包中存在的一部分,因此引用相容性包是一個更好的解決方案(因為它還解決了與 API 相關的任何問題以及相容性包提供的 WCF 問題的解決方案)。 在大多數`Microsoft.Windows.Compatibility`.NET Core 3.0 WPF 和 WinForms 移植方案中,該包都很有説明。 將 NuGet 引用`Microsoft.Windows.Compatibility`新增到 後,僅保留一個產生錯誤!

### <a name="cleaning-up-unused-files"></a>清除未使用的檔案

出現一種類型的遷移問題通常與以前未包含在生成中的新 SDK 樣式項目(自動包含*所有*來源)的 C# 和 XAML 檔有關。

您在 Bean Trader 範例看到的下一個生成錯誤是指*OldUnusedViewModel.cs*中的一個錯誤介面實現。 檔名是提示,但在檢查時,您會發現此源檔不正確。 它以前沒有引起問題,因為它未包含在原始的 .NET 框架專案中。 磁碟上存在但未包含在舊*csproj*中的源文件現在會自動包含。

對於這樣的一次性問題,很容易與以前的*csproj*進行比較,以確認該檔不需要`<Compile Remove="" />`,然後 要麼它,要麼,如果源檔不再需要任何地方,請將其刪除。 在這種情況下,只需刪除*OldUnusedViewModel.cs*是安全的。

如果有許多需要以這種方式排除的源檔,則可以通過在專案檔中`<EnableDefaultCompileItems>`將 屬性設置為 false 來禁用自動包含 C# 檔。 然後,您可以將專案從`<Compile Include>`舊專案檔複製到新專案檔,以便僅生成要包括的源。 同樣,`<EnableDefaultPageItems>`可用於關閉 XAML 頁面的自動`<EnableDefaultItems>`包含,並且可以使用單個屬性控制這兩個頁面。

### <a name="a-brief-aside-on-multi-pass-compilers"></a>多通道編譯器的簡短旁加

從 Bean Trader 範例中刪除違規檔後,您可以重新生成,並將得到四個錯誤。 你以前沒有嗎? 為什麼錯誤數會上升? C# 編譯器是[多通道編譯器](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes)。 這意味著它遍遍每個源檔兩次。 首先,編譯器只查看每個源檔中的元數據和聲明,並標識任何聲明級問題。 這些是您修復的錯誤。 然後,它再次通過代碼將 C# 源構建到 IL;這些是你現在看到的第二組錯誤。

> [!NOTE]
> C# 編譯器[執行的不僅僅是兩個傳遞](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes),但最終結果是,對於像這樣的大型代碼更改的編譯器錯誤往往以兩個波表示。

### <a name="third-party-dependency-fixes-castlewindsor"></a>第三方依賴項修復(城堡.溫莎)

某些遷移方案中出現的另一類問題是依賴項 .NET Framework 和 .NET Core 版本之間的 API 差異。 即使 NuGet 套件同時面向 .NET 框架和 .NET 標準或 .NET Core,也可能有不同的函式庫可用於不同的 .NET 目標。 這允許包支援許多不同的 .NET 平臺,這可能需要不同的實現。 這也意味著,當針對不同的 .NET 平臺時,庫中可能存在較小的 API 差異。

您將在「豆交易」範例中看到的下一組錯誤與`Castle.Windsor`API 相關。 .NET 核心 Bean Trader`Castle.Windsor`專案使用與 .NET Framework 目標專案 (4.1.1) 相同的版本,但這兩個平臺的實現略有不同。

在這種情況下,您將看到需要修復的以下問題:

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`不在 .NET 核心上可用。 但是,有類似的`Classes.FromAssemblyContaining`API 可用,因此我們可以將調`Classes.FromThisAssembly()`用 的兩個`Classes.FromAssemblyContaining(t)`用途替換`t`為調用 ,其中發出調用的類型在哪裡。
1. 同樣,在*Bootstrapper.cs*`Castle.Windsor.Installer.FromAssembly`中。這在 .NET 核心上不可用。 相反,該呼叫可以取代為`FromAssembly.Containing(typeof(Bootstrapper))`。

### <a name="updating-wcf-client-usage"></a>更新 WCF 用戶端使用方式

修復了`Castle.Windsor`差異后,.NET Core Bean Trader 專案中最後`BeanTraderServiceClient`剩餘的生成錯誤`DuplexClientBase`是`Open`(派生自 )沒有方法。 這並不奇怪,因為這是在此遷移過程開始時由 .NET 可移植性分析器突出顯示的 API。 不過,`BeanTraderServiceClient`讓我們注意到一個更大的問題。 此 WCF 用戶端由[Svcutil.exe](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具自動生成。

**Svcutil 生成的 WCF 用戶端用於 .NET 框架。**

使用 svcutil 生成的 WCF 用戶端的解決方案需要重新生成 .NET 標準相容的用戶端,以便與 .NET Core 一起使用。 舊用戶端無法工作的主要原因之一是,它們依賴於應用配置來定義 WCF 綁定和終結點。 由於 .NET 標準 WCF API 可以跨平臺工作(其中 System.配置 API 不可用),因此 .NET 核心和 .NET 標準方案的 WCF 用戶端必須以程式設計方式定義綁定和終結點,而不是在配置中定義綁定和終結點。

事實上,任何 WCF 用戶端使用`<system.serviceModel>`依賴於 app.config 部分(無論是使用 Svcutil 還是手動創建的)都需要更改為在 .NET Core 上工作。

有兩種方法可以自動產生與 .NET 標準相容的 WCF 用戶端:

- 該工具`dotnet-svcutil`是一個 .NET 工具,以類似於 Svcutil 以前的工作方式的方式生成 WCF 用戶端。
- Visual Studio 可以使用其連接服務功能的[WCF Web 服務參考](../../core/additional-tools/wcf-web-service-reference-guide.md)選項生成 WCF 用戶端。

兩種方法都有效。 或者,當然,您可以自己編寫 WCF 客戶端代碼。 對於此示例,我選擇使用可視化工作室連接服務功能。 為此,請右鍵單擊 Visual Studio 解決方案資源管理員中的*BeanTraderClient.Core*專案,然後選擇「**添加** > **連接服務**」 。 接下來,選擇 WCF Web 服務參考提供程式。 這將彈出一個對話框,您可以在其中指定後端 Bean Trader Web`localhost:8080`服務的位址( 如果您在本地端執行伺服器)和生成類型的命名空間應使用(例如**BeanTrader.Service)。**

![WCF Web 服務參考連線的服務對話框](./media/convert-project-from-net-framework/connected-service-dialog.png)

選擇 **"完成"** 按鈕後,將添加新的"已連接服務"節點,並在該節點下添加一個Reference.cs檔,其中包含用於存取 Bean Trader 服務的新 .NET 標準 WCF 用戶端。 如果查看該檔中的`GetEndpointAddress``GetBindingForEndpoint`或 方法,您將看到綁定和終結點現在以程式設計方式生成(而不是透過應用配置)。 "添加已連接服務"功能還可能添加對專案檔中某些 System.ServiceModel 包的引用,因為所有必需的 WCF 包都通過 Microsoft.Windows.相容性包含在內,因此不需要這些引用。 檢查 csproj 以查看是否添加了任何額外的 System.ServiceModel`<PackageReference>`專案,如果是,請刪除它們。

我們的項目現在有新的WCF用戶端類(*在Reference.cs),* 但它也有舊的(在BeanTrader.cs)。 此時有兩個選項:

- 如果希望能夠構建原始的 .NET Framework 專案(以及新的 .NET Core 目標`<Compile Remove="BeanTrader.cs" />`專案),則可以使用 .NET Core 專案的 csproj 檔中的專案,以便應用程式的 .NET 框架和 .NET Core 版本使用不同的 WCF 用戶端。 這樣做的好處是使現有的 .NET Framework 專案保持不變,但缺點是使用生成的 WCF 用戶端的代碼可能需要在 .NET Core 案例中與 .NET 框架專案`#if`中的代碼略有不同,因此您可能需要使用 指令有條件地編譯某些 WCF 用戶端使用方式(例如創建用戶端),以便在為 .NET Core 構建時採用單向方式工作,在為 .NET 框架構建時,可能需要另一種方式。

- 另一方面,如果現有的 .NET Framework 專案中的某些代碼改動是可以接受的,則可以同時刪除*BeanTrader.cs。* 由於新的 WCF 用戶端是為 .NET 標準構建的,因此它將同時在 .NET Core 和 .NET 框架方案中工作。 如果要為 .NET 框架構建 .NET 框架(通過多目標或具有兩個 csproj 檔案),則可以對兩個目標使用此新的*Reference.cs*檔。 此方法的優點是,代碼不需要分叉來支援兩個不同的 WCF 用戶端;相同的代碼將在任何地方使用。 缺點是它涉及更改 (大概穩定) .NET 框架專案。

在 Bean Trader 範例中,如果原始專案使遷移更容易,則可以對原始專案進行少量更改,因此請按照以下步驟協調 WCF 用戶端使用方式:

01. 使用解決方案資源管理員中的「添加現有專案」上下文選單將新的Reference.cs檔添加到 .NET 框架*BeanTraderClient.csproj*專案中。 請務必添加"作為連結",以便兩個專案使用相同的檔(而不是複製 C# 檔案)。 如果要使用單個 csproj(使用多目標)為 .NET Core 和 .NET 框架構建,則此步驟是不必要的。

01. 刪除*BeanTrader.cs*BeanTrader.cs 。

01. 新的 WCF 用戶端與舊用戶端類似,但生成的代碼中的多個命名空間不同。 因此,有必要更新專案,以便 WCF 用戶端類型從 BeanTrader.Service.Service(或您選擇的任何命名空間名稱)而不是 BeanTrader.Model 或沒有命名空間使用。 構建*BeanTraderClient.Core.csproj*將有助於確定需要進行更改的位置。 在 C# 和 XAML 源檔中都需要修復。

01. 最後,您將發現*BeanTraderServiceClientFactory.cs*存在錯誤,因為`BeanTraderServiceClient`類型的可用構造函數已更改。 它曾經可以提供一個`InstanceContext`參數(這是`CallbackHandler``Castle.Windsor`使用 IoC 容器創建的)。 新的構造函數創建新`CallbackHandler`的 s。 但是,在基類型中`BeanTraderServiceClient`,構造函數與所需內容相匹配。 由於自動生成的 WCF 用戶端代碼都存在於部分類中,因此可以輕鬆地擴展它。 為此,請創建一個名為*BeanTraderServiceClient.cs*的新檔案,然後創建具有相同名稱的部分類(使用 BeanTrader.Service 命名空間)。 然後,將一個構造函數添加到部分類型,如下所示。

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

進行這些更改後,Bean Trader 範例現在將使用新的 .NET 標準相容的 WCF 用戶端,您可以TradingService.cs改為更改`Open`呼叫*TradingService.cs*`await OpenAsync`的最後修復方法。

隨著 WCF 問題的解決,Bean Trader 示例的 .NET 核心版本現在構建乾淨!

## <a name="runtime-testing"></a>執行時測試

很容易忘記,一旦項目針對 .NET Core 乾淨地構建,遷移工作就不會完成。 留出時間測試移植的應用程式也很重要。 成功生成內容後,請確保應用按預期運行並工作,尤其是在使用針對 .NET Framework 的任何包時。

讓我們嘗試啟動移植的豆交易應用程式,看看會發生什麼。 除了以下例外情況外,應用在失敗之前不會走得太遠。

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

當然,這是有道理的。 請記住,WCF 不再使用應用配置,因此需要刪除 app.config 檔的舊系統.serviceModel 部分。 更新後的 WCF 用戶端在其代碼中包含所有相同的資訊,因此不再需要配置部分。 如果希望 WCF 終結點在 app.config 中可配置,則可以將其添加為應用設置,並更新 WCF 用戶端代碼以從配置中檢索 WCF 服務終結點。

刪除*app.config*的 system.serviceModel 部分後,應用啟動,但在使用者登錄時失敗,但另一個例外。

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

不支援的 API`Func<T>.BeginInvoke`是 。 如[dotnet/corefx_5940](https://github.com/dotnet/corefx/issues/5940)中所述,.NET Core 不支援`BeginInvoke`委託`EndInvoke`類型和方法,因為存在基礎的遠端處理依賴關係。 此問題及其修復程式在遷移委託中進行了更詳細的解釋[。 BeginInvoke 呼叫 .NET Core](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/)部落`BeginInvoke``EndInvoke`格文章,但要`Task.Run`點是, 呼叫應取代為 (或異步替代,如果可能)。 在此處應用常規解決方案,`BeginInvoke`呼叫可以取代為`Invoke``Task.Run`由啟動的呼叫。

```csharp
Task.Run(() =>
{
    return userInfoRetriever.Invoke();
}).ContinueWith(result =>
{
    // BeginInvoke's callback is replaced with ContinueWith
    var task = result.ConfigureAwait(false);
    CurrentTrader = task.GetAwaiter().GetResult();
}, TaskScheduler.Default);
```

刪除`BeginInvoke`使用後,豆交易者應用程式在 .NET 核心上成功運行!

![在 .NET 核心上執行的豆交易者](./media/convert-project-from-net-framework/running-on-core.png)

所有應用都不同,因此將您自己的應用遷移到 .NET Core 所需的特定步驟會有所不同。 但希望 Bean Trader 範例演示了常規工作流和可以預期的問題類型。 而且,儘管本文的長度,豆交易者樣本中所需的實際更改,使其在 .NET Core 上工作相當有限。 許多應用以同樣方式遷移到 .NET Core;需要有限甚至無需更改代碼。
