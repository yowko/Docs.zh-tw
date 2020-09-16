---
title: 將 WPF 應用程式遷移至 .NET Core 3。0
description: 瞭解如何將 Windows Presentation Foundation (WPF) 應用程式遷移至 .NET Core 3.0。
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: d8abcde4a941ac6e8f9f438cfe7e30f8d1e8a0bc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551942"
---
# <a name="migrating-wpf-apps-to-net-core"></a>將 WPF 應用程式遷移至 .NET Core

本文涵蓋將 Windows Presentation Foundation (WPF) 應用程式從 .NET Framework 遷移至 .NET Core 3.0 所需的步驟。 如果您沒有任何適用于埠的 WPF 應用程式，但想要嘗試此程式，您可以使用[GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader)上提供的**Bean Trader**範例應用程式。 以 .NET Framework 4.7.2) 為目標的原始應用程式 (可在 NetFx\BeanTraderClient 資料夾中取得。 首先，我們將說明在一般情況下移植應用程式所需的步驟，然後我們會逐步解說適用于 **Bean Trader** 範例的特定變更。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

若要遷移至 .NET Core，您必須先：

01. 瞭解和更新 NuGet 相依性：

    01. 升級 NuGet 相依性以使用此 `<PackageReference>` 格式。
    01. 複習適用于 .NET Core 或 .NET Standard 相容性的最上層 NuGet 相依性。
    01. 將 NuGet 套件升級至較新的版本。
    01. 使用 [.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md) 來瞭解 .Net 相依性。

01. 將專案檔案遷移至新的 SDK 樣式格式：

    01. 選擇是否要以 .NET Core 和 .NET Framework 為目標，或僅以 .NET Core 為目標。
    01. 將相關的專案檔案屬性和專案複製到新的專案檔。

01. 修正組建問題：

    01. 新增對 [Microsoft 相容性](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/) 套件的參考。
    01. 尋找並修正 API 層級的差異。
    01. 移除*app.config*或以外的app.config`appSettings` 區段 `connectionStrings` 。
    01. 視需要重新產生產生的程式碼。

01. 執行時間測試：

    01. 確認已移植的應用程式如預期般運作。
    01. 注意 <xref:System.NotSupportedException> 例外狀況。

## <a name="about-the-sample"></a>關於範例

本文參考了 [Bean Trader 範例應用程式](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) ，因為它使用的相依性類似于真實世界的 WPF 應用程式可能擁有的各種相依性。 應用程式並不大，但其目的是從「Hello World」開始，以複雜度為複雜度。 應用程式會示範在移植實際的應用程式時，使用者可能會遇到的一些問題。 應用程式會與 WCF 服務進行通訊，因此若要讓它正常執行，您也需要執行 BeanTraderServer 專案 (可在相同的 GitHub 存放庫中使用) 並確保 BeanTraderClient 設定指向正確的端點。  (預設情況下，此範例假設伺服器是在相同的電腦上執行 `http://localhost:8090` ，如果您在本機啟動 BeanTraderServer，則會是 true。 ) 

請記住，此範例應用程式的目的是要示範 .NET Core 移植的挑戰和解決方案。 它不是用來示範 WPF 最佳做法。 事實上，它會刻意包含一些反模式，以確保您在移植時遇到至少幾個有趣的挑戰。

## <a name="getting-ready"></a>準備就緒

將 .NET Framework 應用程式遷移至 .NET Core 的主要挑戰是它的相依性可能會以不同的方式運作。 遷移比以往更容易;許多 NuGet 套件現在都以 .NET Standard 為目標。 從 .NET Core 2.0 開始，.NET Framework 和 .NET Core 介面區都很類似。 儘管如此， (NuGet 套件和可用 .NET Api 中的支援也) 保留。 遷移的第一個步驟是檢查應用程式的相依性，並確保參考的格式可以輕鬆地遷移至 .NET Core。

### <a name="upgrade-to-packagereference-nuget-references"></a>升級至 `<PackageReference>` NuGet 參考

較舊的 .NET Framework 專案通常會在 *packages.config* 檔案中列出其 NuGet 相依性。 新的 SDK 樣式專案檔案格式會以 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) .csproj 檔案本身的元素，而不是在個別的設定檔中參考 NuGet 套件。

在遷移時，使用樣式參考有兩個優點 `<PackageReference>` ：

- 這是新的 .NET Core 專案檔案所需的 NuGet 參考樣式。 如果您已在使用 `<PackageReference>` 中，可以將這些專案檔專案直接複製並貼到新的專案中。
- 不同于 packages.config 檔案， `<PackageReference>` 元素只會參考您的專案相依的最上層相依性。 所有其他的可轉移 NuGet 套件將會在還原時決定，並記錄在自動產生的 obj\project.assets.js檔案中。 這可讓您更輕鬆地判斷專案的相依性，這在判斷所需的相依性是否可在 .NET Core 上運作時相當實用。

將 .NET Framework 應用程式遷移至 .NET Core 的第一個步驟是將其更新為使用 `<PackageReference>` NuGet 參考。 Visual Studio 讓這種情況變得簡單。 您只需在 Visual Studio 的**方案總管**中，以滑鼠右鍵按一下專案的*packages.config*檔案，然後選取 [**將 packages.config 遷移至 PackageReference**]。

![升級至 PackageReference](./media/convert-project-from-net-framework/package-reference-migration.png)

隨即出現一個對話方塊，顯示計算最上層的 NuGet 相依性，並詢問哪些其他 NuGet 套件應升級為最上層。 這些其他封裝都不需要是 Bean Trader 範例的最上層，所以您可以取消選取所有這些方塊。 然後按一下 **[確定]** ，就會移除 *packages.config* 的檔案，並將 `<PackageReference>` 專案新增至專案檔。

`<PackageReference>`-樣式參考不會將 NuGet 套件儲存在本機的封裝資料夾中。 相反地，它們會在全域儲存為優化。 完成遷移之後，請編輯 .csproj 檔案，並移除任何 `<Analyzer>` 參考先前來自的分析器的元素 *。\packages* 目錄。 別擔心，因為您仍有 NuGet 套件參考，所以分析器將包含在專案中。 您只需要清除舊的 packages.config 樣式 `<Analyzer>` 元素。

### <a name="review-nuget-packages"></a>檢查 NuGet 套件

現在您可以看到專案所相依的最上層 NuGet 套件，您可以複習這些封裝是否可在 .NET Core 上使用。 您可以在 [nuget.org](https://www.nuget.org/)上查看套件的相依性，以判斷套件是否支援 .net Core。建立社區的 [fuget.org](https://www.fuget.org/) 網站會在 [套件資訊] 頁面的頂端醒目顯示這項資訊。

以 .net core 3.0 為目標時，以 .NET core 或 .NET Standard 為目標的任何套件都應可運作 (因為 .NET Core 會執行 .NET Standard 介面區) 。 在某些情況下，所使用套件的特定版本不會以 .NET Core 或 .NET Standard 為目標，但較新的版本將會。 在此情況下，您應該考慮升級為最新版本的套件。

您也可以使用以 .NET Framework 為目標的封裝，但這會帶來一些風險。 您可以使用 .NET Core 來 .NET Framework 相依性，因為 .NET Core 和 .NET Framework 介面區十分類似，這類的相依性 *通常* 可以運作。 不過，如果套件嘗試使用 .net Core 中不存在的 .NET API，您將會遇到執行時間例外狀況。 因此，當沒有其他可用的選項時，您應該只參考 .NET Framework 套件，並瞭解這麼做會造成測試負擔。

如果參考的套件未以 .NET Core 或 .NET Standard 為目標，您必須考慮其他替代方案：

- 是否有其他類似的套件可以改用？ 有時候 NuGet 作者會發佈個別的 '。其程式庫的核心版本，專門以 .NET Core 為目標。 企業程式庫套件是「社區發佈」的範例。NetCore "替代方案。 在其他情況下，特定服務的較新 Sdk (有時會有不同的封裝名稱) 可供 .NET Standard 使用。 如果沒有可用的替代方案，您可以繼續使用 .NET Framework 目標套件，並記住，在 .NET Core 上執行之後，您必須徹底測試它們。

Bean Trader 範例具有下列最上層 NuGet 相依性：

- [**Castle. Windsor，version 4.1。1**](https://www.castleproject.org/projects/windsor/)  

  此封裝的目標 .NET Standard 1.6，因此可在 .NET Core 上運作。

- [**CodeAnalysis. 將 microsoft.codeanalysis.fxcopanalyzers，version 2.6。3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  這是中繼套件，因此不會立即察覺它所支援的平臺，但 [檔](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers) 會指出其最新版本 (2.9.2) 適用于 .NET FRAMEWORK 和 .net Core。

- [**Nito. AsyncEx，version 4.0。1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  此套件不是以 .NET Core 為目標，但較新的5.0 版本會執行。 這在遷移時很常見，因為許多 NuGet 套件已新增 .NET Standard 的支援，但較舊的專案版本只會以 .NET Framework 為目標。 如果版本差異只是次要版本差異，通常可以輕鬆地升級至較新的版本。 因為這是主要版本變更，所以您必須謹慎升級，因為封裝中可能有重大變更。 但有一個途徑是不錯的。

- [**MahApps Metro，version 1.6。5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  此套件也不是以 .NET Core 為目標，但是有較新的發行前版本 (2.0-Alpha) 。 同樣地，您必須瞭解是否有重大變更，但較新的封裝很鼓勵。

Bean Trader 範例的 NuGet 相依性全都以 .NET Standard/.NET Core 為目標，或有較新的版本，因此這裡不太可能發生任何封鎖問題。

### <a name="upgrade-nuget-packages"></a>升級 NuGet 套件

可能的話，最好先升級所有以 .NET Core 為目標的套件版本，或在此時以較新版本為目標 .NET Standard 套件的版本， (專案仍以 .NET Framework) 的目標，以及早探索及解決任何重大變更。

如果您不想對現有的 .NET Framework 版本的應用程式進行任何內容變更，則可以等到您有以 .NET Core 為目標的新專案檔。 不過，事先將 NuGet 套件升級為 .NET Core 相容版本，可讓您更輕鬆地建立新的專案檔，並減少應用程式 .NET Framework 和 .NET Core 版本之間的差異數目。

使用 Bean Trader 範例，您可以使用 Visual Studio 的 NuGet 套件) 管理員，輕鬆地 (所有必要的升級，但有一項例外：從 **MahApps** 升級至 **2.0** 會顯示與主題和輔色管理 api 相關的重大變更。

在理想的情況下，應用程式會更新為使用較新版本的套件 (，因為這比較可能是在 .NET Core) 上運作。 不過，在某些情況下，這可能不可行。 在這些情況下，請勿升級 **MahApps** ，因為必要的變更並不重要，而本教學課程著重于遷移至 .net Core 3，而不是 **MahApps。 Metro 2。** 此外，這也是低風險的 .NET Framework 相依性，因為 Trader 應用程式只會練習 **MahApps**的一小部分。 當然，它也需要進行測試，以確保完成遷移後，一切都能正常運作。 如果這是真實世界的案例，則最好提出問題來追蹤移至 **MahApps** 2.0 版的工作，因為未進行遷移，現在會保留在某些技術債務的背後。

將 NuGet 套件更新至最新版本之後， `<PackageReference>` Bean Trader 範例的專案檔中的專案群組看起來應該像這樣。

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

### <a name="net-framework-portability-analysis"></a>.NET Framework 可攜性分析

一旦您瞭解專案的 NuGet 相依性狀態之後，接下來要考慮的事項是 .NET Framework API 相依性。 [.Net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)工具很適合用來瞭解您的專案所使用的哪些 .net api 可在其他 .net 平臺上使用。

此工具是 [Visual Studio 外掛程式](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)、 [命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)，或包裝在 [簡單的 GUI](https://github.com/Microsoft/dotnet-apiport-ui)中，可簡化其選項。 您可以使用將 [桌面應用程式移植到 .Net Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) blog 文章中的 GUI，深入瞭解如何使用 .Net 可攜性分析器 (API 埠) 。 如果您偏好使用命令列，則必要的步驟如下：

1. 如果您還沒有 [.net 可攜性分析器](https://github.com/Microsoft/dotnet-apiport/releases) ，請加以下載。
1. 請確定要成功移植組建的 .NET Framework 應用程式， (這在遷移之前是不錯的想法，無論) 。
1. 使用如下的命令列執行 API 埠。

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    `-f`引數會指定包含要分析之二進位檔的路徑。 `-r`引數會指定您想要的輸出檔案格式。 `-t`引數會指定要對其分析 API 使用量的 .net 平臺。 在此情況下，您需要 .NET Core。

當您開啟 HTML 報表時，第一個區段會列出所有已分析的二進位檔，以及它們所使用的 .NET Api 百分比在目標平臺上可供使用。 百分比本身並沒有意義。 更有用的是查看遺失的特定 Api。 若要這樣做，請選取元件名稱，或向下滾動至個別元件的報表。

將焦點放在您擁有原始程式碼的元件上。 例如，在 [Bean Trader ApiPort] 報表中，有許多二進位檔列出，但大部分都屬於 NuGet 套件。 `Castle.Windsor` 顯示它相依于 .NET Core 中遺失的一些 Web.config Api。 這不是問題，因為您先前已確認是否 `Castle.Windsor` 支援 .Net Core。 NuGet 套件通常會有不同的二進位檔可與不同的 .NET 平臺搭配使用，因此 `Castle.Windsor` 只要封裝也是以 .NET Standard 或 .Net Core (（) ）為目標，則 .NET Framework 版的會是不相關的。

使用 Bean Trader 範例，您需要考慮的唯一二進位檔是 **BeanTraderClient** ，而且報表會顯示只有兩個 .net api 遺失： `System.ServiceModel.ClientBase<T>.Close` 和 `System.ServiceModel.ClientBase<T>.Open` 。

![BeanTraderClient 可攜性報表](./media/convert-project-from-net-framework/portability-report.png)

因為 WCF 用戶端 Api 大多 (.NET Core 上的) 支援，所以這些核心用戶端 Api 很不可能發生封鎖問題，因此這些中央 Api 必須有替代方案。 事實上，查看 `System.ServiceModel` .Net core 介面區 (使用 <https://apisof.net>) ，您會看到 .net core 中有非同步替代方案。

根據這份報告和先前的 NuGet 相依性分析，您似乎不會有將 Bean Trader 範例遷移至 .NET Core 的主要問題。 您已經準備好進行下一個步驟，您將在其中實際開始進行遷移。

## <a name="migrating-the-project-file"></a>移轉專案檔

如果您的應用程式未使用新的 [SDK 樣式專案檔案格式](../../core/tools/csproj.md)，您將需要以 .net Core 為目標的新專案檔。 您可以取代現有的 .csproj 檔案，或者，如果您想要讓現有的專案保持不變，您可以加入以 .NET Core 為目標的新 .csproj 檔案。 您可以使用單一 SDK 樣式專案檔來建立 .NET Framework 和 .NET Core 的應用程式版本，並使用 [多目標](../../standard/library-guidance/cross-platform-targeting.md) (指定多個 `<TargetFrameworks>` 目標) 。

若要建立新的專案檔，您可以在 Visual Studio 中建立新的 WPF 專案，或在 `dotnet new wpf` 臨時目錄中使用命令來產生專案檔，然後將它複製/重新命名為正確的位置。 另外還有一個 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017)的工具，可將部分專案檔案遷移自動化。 此工具很有説明，但仍需要人力來檢查結果，以確保遷移的所有詳細資料都正確無誤。 工具未以最佳方式處理的某個特定區域是從 *packages.config* 檔案遷移 NuGet 套件。 如果此工具是在仍使用 *packages.config* 檔案參考 NuGet 套件的專案檔上執行，它會自動遷移至專案 `<PackageReference>` ，但會 `<PackageReference>` 為 *所有* 封裝（而不只是最上層的封裝）新增元素。 如果您已經使用 Visual Studio (來遷移至專案 `<PackageReference>` ，則) 此工具可協助您進行其餘的轉換。 如同 Scott Hanselman，建議在他的文章中，介紹如何 [遷移 .csproj](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx)檔案、手動移植是教育版，而且如果您只有幾個專案要移植，則會提供更好的結果。 但是，如果您要移植數十個或數百個專案檔，則 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) 之類的工具可能會是一項協助。

若要為 Bean Trader 範例建立新的專案檔，請 `dotnet new wpf` 在臨時目錄中執行，並將產生的 *.csproj*檔案移至*BeanTraderClient*資料夾，然後將它重新命名為**BeanTraderClient。**

由於新的專案檔格式會自動包含 c # 檔案、 *resx* 檔案，以及它在目錄中找到的 XAML 檔案，因此專案檔已經幾乎完成了！ 若要完成遷移，請並存開啟舊的和新的專案檔，並查看舊的專案檔，以查看是否有任何包含的資訊需要遷移。 在 [Bean Trader] 範例案例中，應該將下列專案複製到新的專案：

- `<RootNamespace>` `<AssemblyName>` `<ApplicationIcon>` 應該全部複製、和屬性。

- 您也必須將屬性加入 `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` 至新的專案檔，因為 Bean Trader 範例包含元件層級屬性 (例如 `[AssemblyTitle]` AssemblyInfo.cs 檔中的) 。 根據預設，新的 SDK 樣式專案會根據 .csproj 檔案中的屬性自動產生這些屬性。 因為您不想在這種情況下發生此情況 (自動產生的屬性會與來自 AssemblyInfo.cs) 的屬性衝突，所以您可以停用自動產生的屬性 `<GenerateAssemblyInfo>` 。

- 雖然 *resx* 檔會自動包含為內嵌資源，但其他 `<Resource>` 專案（例如影像）則否。 因此，請複製內嵌 `<Resource>` 影像和圖示檔的元素。 您可以使用新的專案檔案格式支援萬用字元模式，將 png 參考簡化為單一行： `<Resource Include="**\*.png" />` 。

- 同樣地， `<None>` 專案會自動包含在內，但預設不會將它們複製到輸出目錄。 由於 Bean Trader 專案包含 `<None>` 複製到輸出目錄*is*的專案， (使用 `PreserveNewest`) 的行為，因此您必須更新該檔案的自動填入 `<None>` 專案，如下所示。

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- Bean Trader 範例包含 XAML 檔案 (預設) 為 `Content` (而不是 `Page`) ，因為此檔案中所定義的主題和重音會在執行時間從檔案的 XAML 載入，而不是內嵌在應用程式本身中。 不過，新的專案系統會自動將這個檔案包含在 `<Page>` 中，因為它是 XAML 檔案。 因此，您必須將 XAML 檔案移除為頁面 (`<Page Remove="**\Default.Accent.xaml" />`) ，並將它新增為內容。

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- 最後，藉由複製包含所有元素的來新增 NuGet 參考 `<ItemGroup>` `<PackageReference>` 。 如果您先前未將 NuGet 套件升級為 .NET Core 相容版本，您可以完成套件參考是在 .NET Core 特定專案中。

此時，應該可以將新的專案加入至 BeanTrader 方案，並在 Visual Studio 中開啟它。 專案應該會在 **方案總管**中看起來正確，而且 `dotnet restore BeanTraderClient.Core.csproj` 應該會成功地將封裝還原 (有兩個預期的警告，也就是您使用目標 .NET Framework) 的 MahApps 版本。

雖然您可以將這兩個專案檔並存 (，但如果您想要讓舊的專案完全依照) 的方式來建立舊的專案，它會使遷移程式變得更複雜 (這兩個專案會嘗試使用相同的 bin 和 obj 資料夾) ，通常並不是必要的。 如果您想要建立 .NET Core 和 .NET Framework 目標，您可以 `<TargetFramework>netcoreapp3.0</TargetFramework>` 改為將新專案檔中的屬性取代為 `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` 。 針對 Bean Trader 範例，請刪除舊的專案檔 (BeanTraderClient) ，因為不再需要它。 如果您想要保留這兩個專案檔，請務必將它們建立為不同的輸出和中繼輸出路徑。

## <a name="fix-build-issues"></a>修正組建問題

移植程式的第三個步驟是取得專案的組建。 當專案檔轉換成 SDK 樣式專案之後，有些應用程式就已成功建立。 如果您的應用程式是這種情況，恭喜您！ 您可以繼續進行步驟4。 其他應用程式將需要一些更新才能讓它們建立 .NET Core。 比方說，如果您嘗試 `dotnet build` 在 Bean Trader 範例專案上執行，例如 (或建立在 Visual Studio) 中，將會有許多錯誤，但您將會快速地修正這些錯誤。

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>System.servicemodel 參考和 Microsoft Windows 相容性

常見的錯誤來源缺少適用于 .NET Core 的 Api 參考，但不會自動包含在 .NET Core 應用程式中繼套件中。 若要解決此情況，您應該參考該 `Microsoft.Windows.Compatibility` 套件。 相容性套件包含一組廣泛的 Api，在 Windows 桌面應用程式中很常見，例如 WCF 用戶端、目錄服務、登錄、設定、Acl Api 等等。

使用 Bean Trader 範例，大部分的組建錯誤都是因為遺漏 <xref:System.ServiceModel> 類型。 您可以參考必要的 WCF NuGet 套件來解決這些問題。 WCF 用戶端 Api 是套件中的應用 `Microsoft.Windows.Compatibility` 程式開發介面，因此參考相容性套件是更好的解決方案 (，因為它也可解決與 api 相關的任何問題，以及相容性套件可供) 使用的 wcf 問題解決方案。 `Microsoft.Windows.Compatibility`封裝有助於大部分的 .Net Core 3.0 WPF 和 WinForms 移植案例。 將 NuGet 參考新增至之後 `Microsoft.Windows.Compatibility` ，只會保留一個組建錯誤！

### <a name="cleaning-up-unused-files"></a>清除未使用的檔案

通常會產生的一種遷移問題，與先前未包含在新的 SDK 樣式專案（包含 *所有* 來源）所挑選的組建中的 c # 和 XAML 檔案相關。

您在 Bean Trader 範例中看到的下一個組建錯誤，是指 *OldUnusedViewModel.cs*中有不正確的介面執行。 檔案名是提示，但在檢查時，您會發現此原始程式檔不正確。 它不會造成先前的問題，因為它未包含在原始 .NET Framework 專案中。 存在於磁片上但未包含在舊的 *.csproj* 中的原始程式檔，現在會自動包含在內。

針對這類的一次性問題，您可以輕鬆地與先前的 *.csproj* 進行比較，以確認不需要該檔案，然後再將 `<Compile Remove="" />` 它刪除，或者，如果來源檔案不再需要，請刪除它。 在此情況下，只需刪除 *OldUnusedViewModel.cs*即可安全。

如果您有許多需要以這種方式排除的原始程式檔，您可以 `<EnableDefaultCompileItems>` 在專案檔中將屬性設為 false，以停用自動包含 c # 檔案。 然後，您可以將 `<Compile Include>` 舊專案檔中的專案複製到新的專案檔，以便只建立您要包含的來源。 同樣地， `<EnableDefaultPageItems>` 可以使用來關閉自動包含 XAML 頁面，而且 `<EnableDefaultItems>` 可以使用單一屬性來控制兩者。

### <a name="a-brief-aside-on-multi-pass-compilers"></a>多階段編譯器簡介

從 Bean Trader 範例中移除有問題的檔案之後，您可以重新建立，並會收到四個錯誤。 您之前沒有一個嗎？ 為什麼會出現錯誤數目？ C # 編譯器是 [多重傳遞編譯器](/archive/blogs/ericlippert/how-many-passes)。 這表示每個原始程式檔會執行兩次。 首先，編譯器只會查看每個原始檔中的中繼資料和宣告，並識別任何宣告層級的問題。 這些是您已修正的錯誤。 然後，它會再次執行程式碼，以將 c # 原始檔建立成 IL。這些是您現在看到的第二組錯誤。

> [!NOTE]
> C # 編譯器只會執行 [兩次以上](/archive/blogs/ericlippert/how-many-passes)的結果，但最終結果是大型程式碼變更的編譯器錯誤通常會以兩種方式進行。

### <a name="third-party-dependency-fixes-castlewindsor"></a>協力廠商相依性修正 (Castle Windsor) 

在某些遷移案例中引發的另一個問題類別，是 .NET Framework 和 .NET Core 版本的相依性之間的 API 差異。 即使 NuGet 套件同時以 .NET Framework 和 .NET Standard 或 .NET Core 為目標，也可能會有不同的程式庫可搭配不同的 .NET 目標使用。 這可讓套件支援許多不同的 .NET 平臺，而這些平臺可能需要不同的執行方式。 這也表示以不同的 .NET 平臺為目標時，程式庫中可能會有小型的 API 差異。

您將在 Bean Trader 範例中看到的下一組錯誤與 api 相關 `Castle.Windsor` 。 .NET Core Bean Trader 專案所使用的版本， `Castle.Windsor` 與 .NET Framework 目標專案 (4.1.1) 相同，但這兩個平臺的執行方式稍有不同。

在此情況下，您會看到下列需要修正的問題：

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly` 無法在 .NET Core 上使用。 不過，您可以使用類似的 API `Classes.FromAssemblyContaining` ，因此我們可以將的這兩個用途取代 `Classes.FromThisAssembly()` 為的 `Classes.FromAssemblyContaining(t)` ，其中 `t` 是進行呼叫的型別。
1. 同樣地，在 *Bootstrapper.cs*中 `Castle.Windsor.Installer.FromAssembly` 。這無法在 .NET Core 上使用。 相反地，該呼叫可以取代為 `FromAssembly.Containing(typeof(Bootstrapper))` 。

### <a name="updating-wcf-client-usage"></a>更新 WCF 用戶端使用方式

修正 `Castle.Windsor` 差異之後，.Net Core Bean Trader 專案中最後剩下的組建錯誤就是 `BeanTraderServiceClient` 衍生自) 的 (`DuplexClientBase` 沒有 `Open` 方法。 這並不令人驚訝，因為這是在這個遷移程式開始時，由 .NET 可攜性分析器所強調的 API。 `BeanTraderServiceClient`不過，查看會將重點放在更大的問題。 此 WCF 用戶端是由 [Svcutil.exe](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具自動產生。

**Svcutil 所產生的 WCF 用戶端旨在用於 .NET Framework。**

使用 svcutil 產生之 WCF 用戶端的解決方案，將需要重新產生與 .NET Core 搭配使用 .NET Standard 相容的用戶端。 舊用戶端無法運作的主要原因之一，是它們依存于定義 WCF 系結和端點的應用程式設定。 因為 .NET Standard WCF Api 可跨平臺運作 (System.Configuration Api 無法) ，所以 .NET Core 和 .NET Standard 案例的 WCF 用戶端必須以程式設計的方式定義系結和端點，而不是在設定中。

事實上，相依于 app.config 區段)  (的任何 WCF 用戶端使用， `<system.serviceModel>` 都必須變更為在 .Net Core 上運作。

有兩種方式可以自動產生 .NET Standard 相容的 WCF 用戶端：

- 此 `dotnet-svcutil` 工具是一種 .net 工具，其產生 WCF 用戶端的方式類似于 Svcutil 之前的運作方式。
- Visual Studio 可以使用其已連線的服務功能的 [WCF Web Service Reference](../../core/additional-tools/wcf-web-service-reference-guide.md) 選項來產生 WCF 用戶端。

這兩種方法都能順利運作。 當然，您也可以自行撰寫 WCF 用戶端程式代碼。 在此範例中，我選擇使用 Visual Studio Connected Service 功能。 若要這樣做，請以滑鼠右鍵按一下 Visual Studio 的 [solution explorer] 中的 [ *BeanTraderClient* ] 專案，然後選取 [**加入**  >  **已連接服務**]。 接下來，選擇 WCF Web Service Reference 提供者。 這會顯示一個對話方塊，您可以在其中指定後端 Bean Trader web 服務的位址 (`localhost:8080` 如果您是在本機執行伺服器) ，而且產生的型別應該使用 (**BeanTrader**的命名空間，例如) 。

![WCF Web Service Reference 已連接服務] 對話方塊](./media/convert-project-from-net-framework/connected-service-dialog.png)

當您選取 [ **完成]** 按鈕之後，就會將新的已連線的服務節點新增至專案，並在該節點下加入 Reference.cs 檔案，其中包含用來存取 Bean Trader 服務的新 .NET Standard WCF 用戶端。 如果您查看該檔案 `GetEndpointAddress` 中的或 `GetBindingForEndpoint` 方法，您會看到現在以程式設計的方式產生系結和端點 (而不是透過應用程式設定) 。 「新增已連線的服務」功能也可能會在專案檔中加入某些 System.servicemodel 封裝的參考，因為所有必要的 WCF 封裝都包含在 Windows 的相容性中，所以不需要這些專案。 檢查 .csproj 以查看是否已新增任何額外的 System.servicemodel `<PackageReference>` 專案，如果有的話，請將它們移除。

我們的專案現在有新的 WCF 用戶端類別 (在 *Reference.cs*) 中，但在 BeanTrader.cs) 中仍有舊的 (。 此時有兩個選項：

- 如果您想要能夠建立原始的 .NET Framework 專案 (與新的 .NET Core （以一個) 為目標），您可以使用 `<Compile Remove="BeanTrader.cs" />` .Net core 專案 .csproj 檔案中的專案，讓應用程式的 .NET Framework 和 .Net Core 版本使用不同的 WCF 用戶端。 這樣做的優點是讓現有的 .NET Framework 專案保持不變，但缺點是，使用所產生 WCF 用戶端的程式碼在 .NET Core 案例中可能需要與在 .NET Framework 專案中稍有不同，因此您可能需要使用指示詞，有 `#if` 條件地編譯一些 WCF 用戶端使用方式， (建立用戶端，例如，) 在針對 .Net Core 建立時使用一種方式，並在建立 .NET Framework 時使用另一種方式。

- 另一方面，在現有的 .NET Framework 專案中，某些程式碼變換是可接受的，您可以同時移除 *BeanTrader.cs* 。 由於新的 WCF 用戶端是針對 .NET Standard 所建立，因此可在 .NET Core 和 .NET Framework 案例中運作。 如果您要建立的 .NET Framework 除了 .NET (Core 之外，您還可以透過多重目標或在) 中使用兩個 .csproj 檔案，將這個新的 *Reference.cs* 檔用於這兩個目標。 這種方法的優點是，程式碼不需要 bifurcate 以支援兩個不同的 WCF 用戶端;相同的程式碼將會在所有位置使用。 缺點是，它牽涉到變更 (可能穩定的) .NET Framework 專案。

在 Bean Trader 範例的案例中，您可以對原始專案進行較小的變更，如果它讓遷移更容易，請遵循下列步驟來協調 WCF 用戶端使用：

01. 使用 [方案 Reference.cs] 中的 [加入現有專案] 內容功能表，將新的檔案加入至 .NET Framework *BeanTraderClient .csproj* 專案。 請務必新增 ' as link '，使兩個專案都使用相同的檔案 (而不是複製 c # 檔案) 。 如果您同時使用多目標) 來建立 .NET Core 和 .NET Framework 與單一 .csproj (，則不需要此步驟。

01. 刪除 *BeanTrader.cs*。

01. 新的 WCF 用戶端類似舊的 WCF 用戶端，但產生的程式碼中有許多命名空間不同。 基於這個原因，您必須更新專案，才能使用 BeanTrader 中的 WCF 用戶端類型 (或您選擇的任何命名空間名稱) 而不是 BeanTrader，而不是命名空間。 建立 *BeanTraderClient* 可協助您找出需要進行這些變更的位置。 C # 和 XAML 原始程式檔中都需要修正。

01. 最後，您會發現 *BeanTraderServiceClientFactory.cs* 中有錯誤，因為類型的可用函式 `BeanTraderServiceClient` 已變更。 它可用來提供自 `InstanceContext` 變數， (使用 `CallbackHandler` 從 `Castle.Windsor` IoC 容器) 所建立的引數。 新的函式會建立新的 `CallbackHandler` 。 不過，基底類型中的函式 `BeanTraderServiceClient` 符合您的需要。 由於自動產生的 WCF 用戶端程式代碼都存在於部分類別中，因此您可以輕鬆地加以擴充。 若要這樣做，請建立名為 *BeanTraderServiceClient.cs* 的新檔案，然後使用 BeanTrader 命名空間) 來建立具有相同名稱 (部分類別。 然後，將一個函式加入至部分類型，如下所示。

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

完成這些變更後，Bean Trader 範例現在會使用新的 .NET Standard 相容 WCF 用戶端，而您可以進行最後的修正，將 `Open` *TradingService.cs* 中的呼叫改為改用 `await OpenAsync` 。

解決 WCF 問題之後，.NET Core 版本的 Bean Trader 範例現在已完全建立！

## <a name="runtime-testing"></a>執行時間測試

您可以很容易忘記，當專案完全以 .NET Core 為基礎建立時，就不會完成遷移工作。 也請務必保留測試移植應用程式的時間。 一旦成功建立專案之後，請確定應用程式會如預期般執行並正常運作，尤其是當您使用以 .NET Framework 為目標的任何封裝時。

讓我們試著啟動移植的 Bean Trader 應用程式，看看會發生什麼事。 在發生下列例外狀況之前，應用程式不會有太多的處理失敗。

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

當然，這也是合理的。 請記住，WCF 不再使用應用程式設定，因此必須移除 app.config 檔案的舊 System.servicemodel 區段。 更新的 WCF 用戶端會在其程式碼中包含所有相同的資訊，因此不再需要 config 區段。 如果您想要在 app.config 中設定 WCF 端點，可以將它新增為應用程式設定，並更新 WCF 用戶端程式代碼，以從設定中取出 WCF 服務端點。

移除 *app.config*的 system.servicemodel 區段之後，應用程式會啟動，但會在使用者登入時發生另一個例外狀況而失敗。

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

不支援的 API 為 `Func<T>.BeginInvoke` 。 如 [dotnet/corefx # 5940](https://github.com/dotnet/corefx/issues/5940)中所述，.net Core 不支援 `BeginInvoke` `EndInvoke` 委派類型上的和方法，因為基礎遠端相依性。 此問題及其修正會在遷移委派中更詳細地說明 [。 BeginInvoke 呼叫 .Net Core 的](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/) blog 文章，但 gist 是， `BeginInvoke` `EndInvoke` `Task.Run` 如果可能) 的話，應該將呼叫取代為 (或非同步替代專案。 在這裡套用一般方案， `BeginInvoke` 呼叫可以用啟動的呼叫取代 `Invoke` `Task.Run` 。

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

移除使用方式之後 `BeginInvoke` ，Bean Trader 應用程式就會在 .Net Core 上成功執行！

![在 .NET Core 上執行的 Bean Trader](./media/convert-project-from-net-framework/running-on-core.png)

所有應用程式不同，因此將您自己的應用程式遷移至 .NET Core 所需的特定步驟會有所不同。 但希望 Bean Trader 範例會示範一般工作流程，以及可能預期的問題類型。 而且，儘管本文的長度的限制，Bean Trader 範例中所需的實際變更，使其在 .NET Core 上運作相當有限。 許多應用程式都會以同樣的方式遷移至 .NET Core;但不需要變更任何程式碼。
