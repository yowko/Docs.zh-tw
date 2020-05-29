---
title: 將 WPF 應用程式遷移至 .NET Core 3。0
description: 瞭解如何將 Windows Presentation Foundation （WPF）應用程式遷移至 .NET Core 3.0。
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: fda4f618ddb4a3edbe6f2dd9fba0b10bc618e88d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201564"
---
# <a name="migrating-wpf-apps-to-net-core"></a>將 WPF 應用程式遷移至 .NET Core

本文涵蓋將 Windows Presentation Foundation （WPF）應用程式從 .NET Framework 遷移至 .NET Core 3.0 所需的步驟。 如果您沒有任何適用于埠的 WPF 應用程式，但想要嘗試執行程式，您可以使用[GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader)上提供的**Bean Trader**範例應用程式。 原始應用程式（目標為 .NET Framework 4.7.2）可在 NetFx\BeanTraderClient 資料夾中取得。 首先，我們將說明一般移植應用程式所需的步驟，然後我們會逐步解說適用于**Bean Trader**範例的特定變更。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

若要遷移至 .NET Core，您必須先：

01. 瞭解和更新 NuGet 相依性：

    01. 將 NuGet 相依性升級為使用 `<PackageReference>` 格式。
    01. 查看 .NET Core 或 .NET Standard 相容性的最上層 NuGet 相依性。
    01. 將 NuGet 套件升級至較新的版本。
    01. 使用[.net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)來瞭解 .Net 相依性。

01. 將專案檔案遷移至新的 SDK 樣式格式：

    01. 選擇要以 .NET Core 和 .NET Framework，還是僅以 .NET Core 為目標。
    01. 將相關的專案檔案屬性和專案複製到新的專案檔。

01. 修正組建問題：

    01. 新增對[Microsoft. Windows 相容性](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/)套件的參考。
    01. 尋找並修正 API 層級的差異。
    01. 移除*app.config* `appSettings` 或以外的 app.config 區段。 `connectionStrings`
    01. 視需要重新產生所產生的程式碼。

01. 執行時間測試：

    01. 確認已移植的應用程式如預期般運作。
    01. 注意 <xref:System.NotSupportedException> 例外狀況。

## <a name="about-the-sample"></a>關於範例

本文參考[Bean Trader 範例應用程式](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader)，因為它使用的相依性與實際的 WPF 應用程式可能會有的相依性相似。 應用程式並不大，而是從「Hello World」到複雜度的一個步驟。 應用程式會示範使用者在移植實際應用程式時可能會遇到的一些問題。 應用程式會與 WCF 服務通訊，因此若要讓它正常執行，您也必須執行 BeanTraderServer 專案（可在相同的 GitHub 存放庫中取得），並確定 BeanTraderClient 設定指向正確的端點。 （根據預設，此範例假設伺服器是在同一部電腦上執行 `http://localhost:8090` ，如果您在本機啟動 BeanTraderServer，這會是 true）。

請記住，此範例應用程式的目的是要示範 .NET Core 移植的挑戰和解決方案。 它不是用來示範 WPF 的最佳做法。 事實上，它刻意包含一些反模式，確保您在移植時，遇到至少幾個有趣的挑戰。

## <a name="getting-ready"></a>準備就緒

將 .NET Framework 應用程式遷移至 .NET Core 的主要挑戰，在於它的相依性可能會以不同的方式執行，或是完全不適用。 遷移比過去更容易;許多 NuGet 套件現在都是以 .NET Standard 為目標。 從 .NET Core 2.0 開始，.NET Framework 和 .NET Core 介面區已變得類似。 儘管如此，還是會保留一些差異（兩者都是來自 NuGet 套件和可用 .NET Api 的支援）。 遷移的第一個步驟是檢查應用程式的相依性，並確定參考的格式可以輕鬆地遷移至 .NET Core。

### <a name="upgrade-to-packagereference-nuget-references"></a>升級至 `<PackageReference>` NuGet 參考

較舊的 .NET Framework 專案通常會在*封裝 .config*檔案中列出其 NuGet 相依性。 新的 SDK 樣式專案檔案格式會將 NuGet 套件當做 .csproj 檔案本身的元素來參考， [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 而不是在個別的設定檔中。

在遷移時，使用樣式參考有兩個優點 `<PackageReference>` ：

- 這是新的 .NET Core 專案檔所需的 NuGet 參考樣式。 如果您已經在使用 `<PackageReference>` ，則可以將這些專案檔案元素直接複製並貼到新的專案中。
- 不同于封裝 .config 檔案， `<PackageReference>` 元素只會參考您的專案直接依存的最上層相依性。 所有其他可轉移的 NuGet 套件將會在還原時決定，並記錄在自動產生的 obj\project.assets.json 檔案中。 這可讓您更輕鬆地判斷專案具有哪些相依性，這在判斷必要的相依性是否適用于 .NET Core 時非常有用。

將 .NET Framework 應用程式遷移至 .NET Core 的第一個步驟是將它更新為使用 `<PackageReference>` NuGet 參考。 Visual Studio 讓這簡單。 只要以滑鼠右鍵按一下 Visual Studio 的**方案總管**中專案的*封裝 .config*檔案，然後選取 [**將 PackageReference 遷移至] 即可**。

![升級至 PackageReference](./media/convert-project-from-net-framework/package-reference-migration.png)

隨即出現一個對話方塊，顯示計算的最上層 NuGet 相依性，並詢問哪些其他 NuGet 套件應升級為最上層。 這些其他套件都不需要是 Bean Trader 範例的頂層，因此您可以取消選取所有這些方塊。 然後，按一下 **[確定]** ，就會移除*封裝 .config*檔案，並將 `<PackageReference>` 元素加入至專案檔。

`<PackageReference>`-樣式參考不會將 NuGet 套件儲存在本機的套件資料夾中。 相反地，它們會全域儲存為優化。 完成遷移之後，請編輯 .csproj 檔案，並移除任何 `<Analyzer>` 參考先前來自之分析器的元素 *。\packages*目錄。 別擔心;由於您仍有 NuGet 套件參考，因此分析器會包含在專案中。 您只需要清除舊的封裝 .config 樣式 `<Analyzer>` 元素。

### <a name="review-nuget-packages"></a>審查 NuGet 套件

現在您可以看到專案相依的最上層 NuGet 套件，您可以檢查這些封裝是否可在 .NET Core 上使用。 您可以藉由查看[nuget.org](https://www.nuget.org/)上的相依性，判斷封裝是否支援 .net Core。建立社區的[fuget.org](https://www.fuget.org/)網站會在 [套件資訊] 頁面的頂端，以醒目方式顯示這項資訊。

以 .NET Core 3.0 為目標時，任何以 .NET core 或 .NET Standard 為目標的套件都應該可行（因為 .NET Core 會執行 .NET Standard 介面區）。 在某些情況下，所使用之套件的特定版本不會以 .NET Core 或 .NET Standard 為目標，但較新的版本將會。 在此情況下，您應該考慮升級至套件的最新版本。

您也可以使用以 .NET Framework 為目標的套件，但這會帶來一些風險。 由於 .NET Core 和 .NET Framework 介面區域很類似，因此這類相依性*通常*是可行的，因此可以使用 .net core 來 .NET Framework 相依性。 不過，如果套件嘗試使用 .NET Core 中不存在的 .NET API，您將會遇到執行時間例外狀況。 因此，您應該只在沒有其他可用選項時參考 .NET Framework 套件，並瞭解這麼做會造成測試負擔。

如果有參考的套件不是以 .NET Core 或 .NET Standard 為目標，您就必須考慮其他替代方法：

- 是否有其他類似的套件可以改用？ 有時 NuGet 作者會發佈個別的 '。核心版本的程式庫，特別以 .NET Core 為目標。 企業程式庫套件是「社區發行」的範例。NetCore 「替代方案」。 在其他情況下，可 .NET Standard 特定服務的較新 Sdk （有時具有不同的套件名稱）。 如果沒有可用的替代專案，您可以繼續使用以 .NET Framework 為目標的套件，請注意，在 .NET Core 上執行之後，您必須徹底進行測試。

[Bean Trader 範例] 具有下列最上層的 NuGet 相依性：

- [**Castle. Windsor，版本4.1。1**](https://www.castleproject.org/projects/windsor/)  

  此套件的目標為 .NET Standard 1.6，因此可在 .NET Core 上運作。

- [**CodeAnalysis. FxCopAnalyzers，版本2.6。3**](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  這是中繼套件，因此不會立即察覺它支援的平臺，但[檔](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers)會指出其最新版本（2.9.2）適用于 .NET FRAMEWORK 和 .net Core。

- [**Nito. AsyncEx，版本4.0。1**](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  此套件不是以 .NET Core 為目標，但較新的5.0 版本則會這麼做。 這在遷移時很常見，因為許多 NuGet 封裝已新增 .NET Standard 的支援，但較舊的專案版本只會以 .NET Framework 為目標。 如果版本差異只是次要版本的差異，通常可以輕鬆地升級至較新的版本。 因為這是主要的版本變更，所以您必須小心升級，因為封裝中可能會有重大變更。 不過，有一個路徑向前邁進，這是很好的方法。

- [**MahApps，版本1.6。5**](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  此套件也不會以 .NET Core 為目標，但具有較新的發行前版本（2.0-Alpha），其會執行。 同樣地，您必須找出重大變更，但較新的套件鼓勵您。

Bean Trader 範例的 NuGet 相依性全都以 .NET Standard/.NET Core 為目標，或具有較新的版本，因此這裡不太可能發生任何封鎖問題。

### <a name="upgrade-nuget-packages"></a>升級 NuGet 套件

可能的話，最好是升級僅以 .NET Core 為目標的任何封裝版本，或目前以較新版本 .NET Standard 的任何套件（專案仍以 .NET Framework 為目標），以及早探索並解決任何重大變更。

如果您不想對應用程式的現有 .NET Framework 版本進行任何材質變更，這可以等到您有以 .NET Core 為目標的新專案檔。 不過，預先將 NuGet 套件升級至 .NET Core 相容版本，可讓您在建立新的專案檔之後更輕鬆地進行遷移程式，並減少 .NET Framework 與 .NET Core 版本的應用程式之間的差異。

使用 Bean Trader 範例，可以輕鬆地進行所有必要的升級（使用 Visual Studio 的 NuGet 套件管理員），但有一個例外：從**MahApps**升級到**2.0** ，會顯示與主題和輔色管理 api 相關的重大變更。

在理想的情況下，應用程式會更新為使用較新版本的套件（因為這較可能在 .NET Core 上使用）。 不過，在某些情況下，這可能不可行。 在這些情況下，請不要升級**MahApps** ，因為必要的變更並不簡單，而本教學課程著重于遷移至 .net Core 3，而不是**MahApps。 Metro 2。** 此外，這是一項低風險 .NET Framework 相依性，因為 Bean Trader 應用程式只會練習**MahApps**的一小部分。 當然，它還需要進行測試，以確保在完成遷移之後，一切都能正常運作。 如果這是真實世界的案例，建議您提出問題以追蹤移至**MahApps** 2.0 版的工作，因為不會進行遷移，因此現在不會留下一些技術債務。

將 NuGet 套件更新為最新版本之後， `<PackageReference>` Bean Trader 範例的專案檔中的專案群組看起來應該像這樣。

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

一旦您瞭解專案的 NuGet 相依性狀態之後，接下來要考慮的事項是 .NET Framework API 相依性。 [.Net 可攜性分析器](../../standard/analyzers/portability-analyzer.md)工具適合用來瞭解您的專案所使用的 .net api 在其他 .net 平臺上是否可用。

此工具會做為[Visual Studio 外掛程式](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)、[命令列工具](https://github.com/Microsoft/dotnet-apiport/releases)，或包裝在[簡單的 GUI](https://github.com/Microsoft/dotnet-apiport-ui)中，以簡化其選項。 若要深入瞭解如何使用 .NET 可攜性分析器（API 埠），請參閱將[桌面應用程式移植到 .Net Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/)的 blog 文章。 如果您想要使用命令列，所需的步驟如下：

1. 下載[.net 可攜性分析器](https://github.com/Microsoft/dotnet-apiport/releases)（如果尚未安裝的話）。
1. 請確定 .NET Framework 應用程式可以成功地進行移植（這在遷移之前是不錯的主意）。
1. 使用類似如下的命令列來執行 API 埠。

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    `-f`引數會指定包含要分析之二進位檔的路徑。 `-r`引數會指定您想要的輸出檔案格式。 `-t`引數會指定分析 API 使用的目標 .net 平臺。 在此情況下，您會想要 .NET Core。

當您開啟 HTML 報表時，第一個區段會列出所有分析的二進位檔，以及它們使用的 .NET Api 的百分比在目標平臺上可用。 百分比本身並沒有意義。 最有用的是查看遺漏的特定 Api。 若要這麼做，請選取元件名稱，或向下移動至個別元件的報表。

將焦點放在您擁有原始程式碼的元件上。 例如，在 [Bean Trader ApiPort] 報告中，列出許多二進位檔，但其中大部分都屬於 NuGet 套件。 `Castle.Windsor`顯示相依于 .NET Core 中遺漏的一些 System.web Api。 這不是問題，因為您先前已確認 `Castle.Windsor` 支援 .Net Core。 NuGet 套件通常會有不同的二進位檔，以便與不同的 .NET 平臺搭配使用，因此， `Castle.Windsor` 只要封裝也以 .NET Standard 或 .Net Core 為目標（其具備），.NET Framework 版本的就會使用 System.web api 或不相關。

使用 Bean Trader 範例時，您唯一需要考慮的二進位檔是**BeanTraderClient** ，而且報表會顯示只有兩個 .net api 遺失： `System.ServiceModel.ClientBase<T>.Close` 和 `System.ServiceModel.ClientBase<T>.Open` 。

![BeanTraderClient 可攜性報告](./media/convert-project-from-net-framework/portability-report.png)

這不太可能會造成封鎖問題，因為 WCF 用戶端 Api （大多）在 .NET Core 上受到支援，因此這些中央 Api 必須有替代方案。 事實上，在查看 `System.ServiceModel` .Net core 介面區（使用）時 <https://apisof.net> ，您會看到 .net core 中有非同步替代專案。

根據這份報告和先前的 NuGet 相依性分析，將 Bean Trader 範例遷移至 .NET Core 時似乎不會有任何重大問題。 您已準備好進行下一個步驟，也就是您將會實際開始進行遷移。

## <a name="migrating-the-project-file"></a>移轉專案檔

如果您的應用程式未使用新的[SDK 樣式專案檔案格式](../../core/tools/csproj.md)，您將需要新的專案檔來以 .net Core 為目標。 您可以取代現有的 .csproj 檔案，或者，如果您想要讓現有專案保持不變的目前狀態，您可以加入以 .NET Core 為目標的新 .csproj 檔案。 您可以使用具有[多目標](../../standard/library-guidance/cross-platform-targeting.md)（指定多個目標）的單一 SDK 樣式專案檔，建立適用于 .NET FRAMEWORK 和 .net Core 的應用程式版本 `<TargetFrameworks>` 。

若要建立新的專案檔，您可以在 Visual Studio 中建立新的 WPF 專案，或在 `dotnet new wpf` 臨時目錄中使用命令來產生專案檔案，然後將它複製/重新命名為正確的位置。 另外還有一個以社區建立的工具[CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017)，可以自動化部分專案檔案遷移。 此工具很有説明，但仍需要人工檢查結果，以確保所有的遷移詳細資料都正確無誤。 工具無法以最佳方式處理的一個特定區域是從*套件 .config*檔案遷移 NuGet 套件。 如果此工具在專案檔上執行，而該檔案仍使用*封裝 .config*檔案來參考 NuGet 套件，它會自動遷移至 `<PackageReference>` 元素，但會 `<PackageReference>` 為*所有*封裝加入元素，而不只是最上層的套件。 如果您已經使用 Visual Studio 遷移至專案 `<PackageReference>` （如您在此範例中所做的），則工具可以協助進行其餘的轉換。 就像 Scott Hanselman 在[他的](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx)文章中建議您在遷移 .csproj 檔案時，以手動方式移植是教育的，如果您只需要幾個專案，就會得到更好的結果。 但是，如果您要移植數十個或數百個專案檔，那麼[CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017)之類的工具就可以提供協助。

若要建立 Bean Trader 範例的新專案檔，請 `dotnet new wpf` 在臨時目錄中執行，並將產生的 *.csproj*檔案移至*BeanTraderClient*資料夾，並將它重新命名為 BeanTraderClient. **Core .csproj**。

因為新的專案檔案格式會自動包含 c # 檔案、 *resx*檔案和 XAML 檔案，其可在或其目錄底下找到，所以專案檔已幾乎完成！ 若要完成遷移，請並存開啟舊的和新的專案檔，並查看舊的專案檔，以查看是否需要遷移其中包含的任何資訊。 在 Bean Trader 範例案例中，下列專案應該複製到新的專案：

- `<RootNamespace>`、 `<AssemblyName>` 和 `<ApplicationIcon>` 屬性應全部複製。

- 您也需要將屬性加入 `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` 至新的專案檔，因為「Bean Trader 範例會在 AssemblyInfo.cs 檔中包含元件層級屬性（例如 `[AssemblyTitle]` ）。 根據預設，新的 SDK 樣式專案會依據 .csproj 檔案中的屬性來自動產生這些屬性。 因為您不想在這種情況下發生這種情況（自動產生的屬性會與 AssemblyInfo.cs 中的屬性衝突），所以您可以使用來停用自動產生的屬性 `<GenerateAssemblyInfo>` 。

- 雖然*resx*檔案會自動納入為內嵌資源，但其他 `<Resource>` 專案（例如影像）則不會。 因此，請複製 `<Resource>` 用於內嵌影像和圖示檔的元素。 您可以使用新的專案檔案格式對萬用字元模式的支援，來簡化單一行的 png 參考： `<Resource Include="**\*.png" />` 。

- 同樣地，系統 `<None>` 會自動包含專案，但預設不會將它們複製到輸出目錄。 由於 Bean Trader 專案包含 `<None>` 複製到輸出目錄*is* （使用行為）的專案，因此 `PreserveNewest` 您必須更新該檔案的自動填入 `<None>` 專案，如下所示。

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- [Bean Trader] 範例包含 XAML 檔案（預設值）做為 `Content` （而不是 `Page` ），因為在執行時間會從檔案的 XAML 載入這個檔案中定義的主題和重音，而不是內嵌在應用程式本身。 不過，新的專案系統會自動將此檔案包含在 `<Page>` 中，因為它是 XAML 檔案。 因此，您必須將 XAML 檔案移除為頁面（ `<Page Remove="**\Default.Accent.xaml" />` ），並將它新增為內容。

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- 最後，藉由複製包含所有元素的來新增 NuGet 參考 `<ItemGroup>` `<PackageReference>` 。 如果您先前未將 NuGet 套件升級為 .NET Core 相容版本，您可以執行這項操作，因為套件參考是在 .NET Core 特定的專案中。

此時，您應該可以將新專案新增至 BeanTrader 方案，並在 Visual Studio 中開啟它。 專案在**方案總管**中應該看起來是正確的，而且 `dotnet restore BeanTraderClient.Core.csproj` 應該成功還原套件（有兩個預期的警告，與您使用的目標是 .NET Framework 的 MahApps 版本有關）。

雖然可以同時保留這兩個專案檔（如果您想要保持完全相同的專案，可能也會需要），它會使遷移程式變得更複雜（這兩個專案會嘗試使用相同的 bin 和 obj 資料夾），而且通常不是必要的。 如果您想要同時建立 .NET Core 和 .NET Framework 目標，您可以 `<TargetFramework>netcoreapp3.0</TargetFramework>` 改為將新專案檔中的屬性取代 `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>` 為。 針對 [Bean Trader 範例]，刪除舊的專案檔（BeanTraderClient），因為已不再需要它。 如果您想要保留這兩個專案檔，請務必將它們建立成不同的輸出和中繼輸出路徑。

## <a name="fix-build-issues"></a>修正組建問題

移植程式的第三個步驟是取得要建立的專案。 專案檔轉換成 SDK 樣式的專案之後，某些應用程式就已成功建立。 如果您的應用程式是這種情況，恭喜您！ 您可以移至步驟4。 其他應用程式將需要一些更新，才能為 .NET Core 建立。 如果您 `dotnet build` 現在嘗試在 Bean Trader 範例專案上執行，例如（或在 Visual Studio 中建立），則會有許多錯誤，但您會很快地解決問題。

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>System.servicemodel 參考和 Microsoft. Windows 相容性

錯誤的常見來源缺少適用于 .NET Core 但不會自動包含在 .NET Core 應用程式中繼套件中的 Api 參考。 若要解決此情況，您應該參考該 `Microsoft.Windows.Compatibility` 套件。 相容性套件包含一組廣泛的 Api，在 Windows 桌面應用程式中很常見，例如 WCF 用戶端、目錄服務、登錄、設定、Acl Api 等等。

使用 Bean Trader 範例時，大部分的組建錯誤都是因為遺漏類型所致 <xref:System.ServiceModel> 。 藉由參考必要的 WCF NuGet 套件，即可解決這些問題。 不過，WCF 用戶端 Api 是封裝中的應用程式開發介面 `Microsoft.Windows.Compatibility` ，因此參考相容性套件是一個更好的解決方案（因為它也能解決與 api 相關的任何問題，以及相容性套件所提供之 WCF 問題的解決方案）。 在 `Microsoft.Windows.Compatibility` 大部分 .Net Core 3.0 WPF 和 WinForms 移植案例中，封裝都有説明。 將 NuGet 參考新增至之後 `Microsoft.Windows.Compatibility` ，只會保留一個組建錯誤！

### <a name="cleaning-up-unused-files"></a>清除未使用的檔案

其中一種會產生的遷移問題，通常與先前未包含在組建中的 c # 和 XAML 檔案有關，這些檔案會自動包含*所有*來源，並由新的 SDK 樣式專案所挑選。

您在 Bean Trader 範例中看到的下一個組建錯誤是指*OldUnusedViewModel.cs*中的不正確介面實。 檔案名是提示，但在檢查時，您會發現這個原始程式檔不正確。 它不會造成先前的問題，因為它並未包含在原始的 .NET Framework 專案中。 出現在磁片上但未包含在舊的 *.csproj*中的原始程式檔，現在會自動包含在內。

對於這類的一次性問題，很容易就能與先前的 *.csproj*進行比較，以確認不需要該檔案， `<Compile Remove="" />` 或者，如果在任何地方不需要來源檔案，請將它刪除。 在此情況下，只需刪除*OldUnusedViewModel.cs*即可安全。

如果您有許多需要以這種方式排除的原始程式檔，您可以 `<EnableDefaultCompileItems>` 在專案檔中將屬性設定為 false，以停用自動包含 c # 檔案。 然後，您可以將 `<Compile Include>` 舊專案檔中的專案複製到新的專案檔，以便只建立您要包含的來源。 同樣地， `<EnableDefaultPageItems>` 可以用來關閉自動包含 XAML 頁面，而且 `<EnableDefaultItems>` 可以使用單一屬性來控制兩者。

### <a name="a-brief-aside-on-multi-pass-compilers"></a>多階段編譯器簡介

從 Bean Trader 範例中移除有問題的檔案之後，您可以重新建立，而且會收到四個錯誤。 您之前沒有人嗎？ 為什麼會出現錯誤數目？ C # 編譯器是[多階段編譯器](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes)。 這表示它會逐一處理每個來源檔案兩次。 首先，編譯器只會查看每個來源檔案中的中繼資料和宣告，並識別任何宣告層級的問題。 這些是您已修正的錯誤。 然後，它會再次流覽程式碼，將 c # 原始檔建立為 IL;這些是您現在看到的第二組錯誤。

> [!NOTE]
> C # 編譯器不[只](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes)會執行兩個階段，但最終結果是，大型程式碼變更的編譯器錯誤，這通常會出現在兩個波狀中。

### <a name="third-party-dependency-fixes-castlewindsor"></a>協力廠商相依性修正（Castle. Windsor）

在某些遷移案例中出現的另一個問題，就是 .NET Framework 和 .NET Core 版本的相依性之間的 API 差異。 即使 NuGet 套件同時以 .NET Framework 和 .NET Standard 或 .NET Core 為目標，也可能有不同的程式庫可與不同的 .NET 目標搭配使用。 這可讓封裝支援許多不同的 .NET 平臺，這可能需要不同的執行方式。 這也表示以不同的 .NET 平臺為目標時，程式庫中可能會有小型的 API 差異。

您會在 Bean Trader 範例中看到的下一組錯誤與 api 相關 `Castle.Windsor` 。 .NET Core Bean Trader 專案使用與 `Castle.Windsor` .NET Framework 目標專案（4.1.1）相同的版本，但這兩個平臺的執行方式稍有不同。

在此情況下，您會看到下列需要修正的問題：

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly`無法在 .NET Core 上使用。 不過，有類似的 API `Classes.FromAssemblyContaining` 可供使用，因此我們可以將的兩個用法取代 `Classes.FromThisAssembly()` 為的呼叫 `Classes.FromAssemblyContaining(t)` ，其中 `t` 是發出呼叫的類型。
1. 同樣地，在*Bootstrapper.cs*中， `Castle.Windsor.Installer.FromAssembly` 。這無法在 .NET Core 上使用。 相反地，可以使用取代該呼叫 `FromAssembly.Containing(typeof(Bootstrapper))` 。

### <a name="updating-wcf-client-usage"></a>更新 WCF 用戶端使用方式

修正了 `Castle.Windsor` 差異，.Net Core Bean Trader 專案中最後一個剩餘的組建錯誤是 `BeanTraderServiceClient` （衍生自 `DuplexClientBase` ）沒有 `Open` 方法。 這並不令人驚訝，因為這是在此遷移程式開始時由 .NET 可攜性分析器反白顯示的 API。 `BeanTraderServiceClient`不過，查看會將我們的注意力繪製到較大的問題。 此 WCF 用戶端是由[Svcutil](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)自動產生。

**Svcutil 所產生的 WCF 用戶端是用於 .NET Framework 上。**

使用 svcutil 產生之 WCF 用戶端的解決方案，必須重新產生與 .NET Standard 相容的用戶端，以與 .NET Core 搭配使用。 舊用戶端無法使用的主要原因之一，是它們相依于定義 WCF 系結和端點的應用程式設定。 由於 .NET Standard WCF Api 可跨平臺運作（其中不提供系統設定 Api），因此 .NET Core 和 .NET Standard 案例的 WCF 用戶端必須以程式設計方式（而不是在設定中）定義系結和端點。

事實上，相依于 `<system.serviceModel>` app.config 區段（不論是使用 Svcutil 或手動建立）的任何 WCF 用戶端使用方式都必須變更，才能在 .Net Core 上使用。

有兩種方式可以自動產生 .NET Standard 相容的 WCF 用戶端：

- 此 `dotnet-svcutil` 工具是一種 .net 工具，其產生的 WCF 用戶端與 Svcutil 之前的運作方式類似。
- Visual Studio 可以使用其已連線的服務功能的[Wcf Web 服務參考](../../core/additional-tools/wcf-web-service-reference-guide.md)選項來產生 wcf 用戶端。

這兩種方法都很好用。 當然，您也可以自行撰寫 WCF 用戶端程式代碼。 在此範例中，我選擇使用 Visual Studio 連接的服務功能。 若要這麼做，請以滑鼠右鍵按一下 Visual Studio 的 [方案瀏覽器] 中的 [ *BeanTraderClient* ] 專案，然後選取 [**新增**  >  **已連線的服務**]。 接下來，選擇 [WCF Web 服務參考提供者]。 這會顯示一個對話方塊，您可以在其中指定後端 Bean Trader web 服務的位址（ `localhost:8080` 如果您是在本機執行伺服器），以及產生的類型應使用的命名空間（例如**BeanTrader**）。

![WCF Web 服務參考已連接服務對話方塊](./media/convert-project-from-net-framework/connected-service-dialog.png)

選取 [**完成]** 按鈕之後，會將新的已連線的服務節點加入至專案，並在該節點下加入 Reference.cs 檔案，其中包含用來存取 Bean Trader 服務的新 .NET Standard WCF 用戶端。 如果您查看該檔案 `GetEndpointAddress` 中的或 `GetBindingForEndpoint` 方法，您會看到現在以程式設計方式產生系結和端點（而不是透過 app config）。 「新增已連線的服務」功能也可能會將參考新增至專案檔中的某些 System.servicemodel 封裝，因為所有必要的 WCF 封裝都是透過 Microsoft 所包含，所以不需要這麼做。 檢查 .csproj 以查看是否已加入任何額外的 System.servicemodel `<PackageReference>` 專案，如果有的話，請將它們移除。

我們的專案現在有新的 WCF 用戶端類別（在*Reference.cs*中），但它仍然具有舊的（在 BeanTrader.cs 中）。 此時有兩個選項：

- 如果您想要能夠建立原始的 .NET Framework 專案（連同新的 .NET Core 目標），您可以使用 `<Compile Remove="BeanTrader.cs" />` .Net Core 專案的 .csproj 檔案中的專案，讓應用程式的 .NET Framework 和 .Net Core 版本使用不同的 WCF 用戶端。 這樣做的優點是讓現有的 .NET Framework 專案保持不變，但缺點是，在 .NET Core 案例中，使用產生的 WCF 用戶端的程式碼可能需要與 .NET Framework 專案中的略有不同，因此您可能需要使用指示詞 `#if` ，有條件地編譯一些 wcf 用戶端使用方式（例如，建立用戶端），以便在針對 .Net core 建立時，以另一種方式來工作，並在建立時進行 .NET Framework。

- 另一方面，如果現有 .NET Framework 專案中的某些程式碼變換是可接受的，您就可以將*BeanTrader.cs*全部移除。 由於新的 WCF 用戶端是針對 .NET Standard 所建立，因此可在 .NET Core 和 .NET Framework 案例中使用。 如果您要建立的是除了 .NET Core 以外的 .NET Framework （由多目標或有兩個 .csproj 檔案），您可以針對這兩個目標使用這個新的*Reference.cs*檔案。 這種方法的優點是，程式碼不需要 bifurcate 以支援兩個不同的 WCF 用戶端;所有地方都會使用相同的程式碼。 缺點是，它牽涉到變更（可能是穩定的） .NET Framework 專案。

在 Bean Trader 範例的案例中，您可以對原始專案進行較小的變更，讓您更輕鬆地進行遷移，因此請遵循下列步驟來協調 WCF 用戶端的使用方式：

01. 使用 [方案瀏覽器] 中的 [加入現有專案] 操作功能表，將新的 Reference.cs 檔案加入至 .NET Framework *BeanTraderClient. .csproj*專案。 請務必加入 ' as link '，讓這兩個專案都使用相同的檔案（相對於複製 c # 檔案）。 如果您使用單一 .csproj 同時建立 .NET Core 和 .NET Framework （使用多目標），則不需要執行此步驟。

01. 刪除*BeanTrader.cs*。

01. 新的 WCF 用戶端與舊版類似，但產生的程式碼中有數個命名空間不同。 因此，您必須更新專案，以便從 BeanTrader （或您選擇的任何命名空間名稱）使用 WCF 用戶端類型，而不是 BeanTrader 或沒有命名空間。 建立*BeanTraderClient*有助於識別需要進行這些變更的位置。 C # 和 XAML 原始程式檔都需要修正。

01. 最後，您會發現*BeanTraderServiceClientFactory.cs*中發生錯誤，因為類型的可用的函式 `BeanTraderServiceClient` 已變更。 它可用來提供 `InstanceContext` 引數（使用 `CallbackHandler` 來自 IoC 容器的來建立 `Castle.Windsor` ）。 新的函式會建立新的 `CallbackHandler` 。 不過，在 `BeanTraderServiceClient` 的基底型別中，會符合您想要的函式。 因為自動產生的 WCF 用戶端程式代碼都存在於部分類別中，所以您可以輕鬆地將它擴充。 若要這麼做，請建立名為*BeanTraderServiceClient.cs*的新檔案，然後建立具有該相同名稱的部分類別（使用 BeanTrader 命名空間）。 然後，將一個函式加入至部分型別，如下所示。

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

進行這些變更之後，Bean Trader 範例現在會使用新的 .NET Standard 相容 WCF 用戶端，而您可以在 `Open` *TradingService.cs*中變更呼叫以改用 `await OpenAsync` 。

在解決 WCF 問題的情況下，現在就能完全建立 .NET Core 版本的 Bean Trader 範例！

## <a name="runtime-testing"></a>執行時間測試

只要專案完全針對 .NET Core 建立，就不會忘記遷移工作的完成。 請務必保留測試已移植應用程式的時間。 成功建立專案之後，請確定應用程式執行並如預期般運作，特別是當您使用任何以 .NET Framework 為目標的套件時。

讓我們嘗試啟動已移植的 Bean Trader 應用程式，並瞭解會發生什麼事。 應用程式在失敗前不會遇到下列例外狀況。

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

當然，這就是合理的。 請記住，WCF 不再使用應用程式設定，因此必須移除 app.config 檔案的舊 System.servicemodel 區段。 更新的 WCF 用戶端會在其程式碼中包含所有相同的資訊，因此不再需要 config 區段。 如果您想要在 app.config 中設定 WCF 端點，您可以將它新增為應用程式設定，並更新 WCF 用戶端程式代碼，以從設定中取出 WCF 服務端點。

移除*app.config*的 system.servicemodel 區段之後，應用程式會啟動，但在使用者登入時發生另一個例外狀況。

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

不支援的 API 是 `Func<T>.BeginInvoke` 。 如[dotnet/corefx # 5940](https://github.com/dotnet/corefx/issues/5940)中所述，.net Core 不支援 `BeginInvoke` `EndInvoke` 委派類型上的和方法，因為基礎遠端相依性的關係。 此問題及其修正程式會在遷移委派中更詳細地說明[。 BeginInvoke 呼叫 .Net Core 的](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/)blog 文章，但 gist 是， `BeginInvoke` 而 `EndInvoke` 呼叫應取代為 `Task.Run` （或非同步替代專案，如果可能的話）。 在此套用一般解決方案， `BeginInvoke` 可以使用由啟動的呼叫來取代呼叫 `Invoke` `Task.Run` 。

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

移除使用量之後 `BeginInvoke` ，Bean Trader 應用程式會在 .Net Core 上成功執行！

![在 .NET Core 上執行的 Bean Trader](./media/convert-project-from-net-framework/running-on-core.png)

所有應用程式都不同，因此將您自己的應用程式遷移至 .NET Core 所需的特定步驟會有所不同。 但希望 Bean Trader 範例會示範一般工作流程，以及可預期的問題類型。 而且雖然這篇文章的長度，但在 Trader 範例中，為了讓它能夠在 .NET Core 上工作，所需的實際變更相當有限。 許多應用程式都會以同樣的方式遷移至 .NET Core;但不需要變更程式碼。
