---
title: 移轉至 .NET 5 的範例
description: 顯示如何將以 .NET Framework 為目標的範例應用程式遷移至 .NET 5。
ms.date: 01/19/2021
ms.openlocfilehash: 39ecdfa639f4d68a4a8821da839f014c8de42ab0
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216261"
---
# <a name="example-of-migrating-to-net"></a>遷移至 .NET 的範例

在本章中，我們會提供實用的指導方針，以協助您將現有的應用程式從 .NET Framework 遷移至 .NET。

我們會提供您可以遵循的結構完善程式，以及每個步驟應考慮的最重要事項。

接著，我們會記載範例傳統型應用程式（從 WinForms 和 WPF 版本）的逐步遷移程式。

## <a name="migration-process-overview"></a>移轉處理序概觀

遷移套裝程式含四個順序步驟：

1. **準備**：瞭解專案必須先瞭解的相依性。 在此步驟中，您會將目前的專案納入可簡化遷移啟動點的狀態。

2. **遷移專案檔：** .net 專案使用新的 SDK 樣式專案格式。 以這種格式建立新的專案檔，或更新您必須使用 SDK 樣式的專案檔。

3. **修正程式碼和組建：** 在 .NET 中建立程式碼，以解決 .NET Framework 與 .NET 之間的 API 層級差異。 如有需要，請將協力廠商套件更新為支援 .NET 的封裝。

4. **執行和測試：** 在執行時間之前可能不會顯示任何差異。 因此，請別忘了執行應用程式，並測試所有專案是否都能如預期般運作。

### <a name="preparation"></a>準備

#### <a name="migrate-packagesconfig-file"></a>遷移 packages.config 檔案

在 .NET Framework 應用程式中，會在 *packages.config* 檔案中宣告外部封裝的所有參考。 在 .NET 中，不再需要使用 *packages.config* 檔案。 相反地，請使用專案檔內的 [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) 屬性來指定您應用程式的 NuGet 套件。

因此，您需要從一種格式轉換成另一種格式。 您可以手動進行更新，取得 *packages.config* 檔中所包含的相依性，並將其遷移至具有格式的專案檔 `PackageReference` 。 或者，您可以讓 Visual Studio 為您執行工作：以滑鼠右鍵按一下 *packages.config* 檔案，然後選取 [ **遷移 packages.config 至 PackageReference** 選項。

#### <a name="verify-every-dependency-compatibility-in-net"></a>確認 .NET 中的每個相依性相容性

遷移封裝參考之後，您必須檢查每個參考的相容性。 您可以探索應用程式在 [nuget.org](https://www.nuget.org/)上使用的每個 NuGet 套件的相依性。如果封裝有 .NET Standard 相依性，則會在 .NET 5.0 上運作，因為 .NET [支援](../../standard/net-standard.md#net-implementation-support) 所有版本的 .NET Standard。 下圖顯示套件的相依性 `Castle.Windsor` ：

![Castle. Windsor 套件之 NuGet 相依性的螢幕擷取畫面](./media/example-migration-core/nuget-dependencies.png)

若要檢查套件相容性，您可以使用 <https://fuget.org> 提供更詳細的版本和相依性相關資訊的工具。

可能是專案參考了不支援 .NET 的較舊套件版本，但您可能會發現支援它的較新版本。 因此，將套件更新為較新版本通常是很好的建議。 不過，您應該考慮更新套件版本可能會導致某些可能會強制您更新程式碼的重大變更。

如果找不到相容的版本，會發生什麼事？ 如果您因為這些重大變更而不想更新套件的版本，該怎麼辦？ 別擔心，因為可以依賴來自 .NET 應用程式的 .NET Framework 套件。 別忘了大量測試，因為如果外部封裝呼叫的 API 無法在 .NET 上使用，它可能會造成執行階段錯誤。 當您使用的舊套件不會進行更新，而且您可以直接將它重定為在 .NET 上運作時，這就很好用。

#### <a name="check-for-api-compatibility"></a>檢查是否有 API 相容性

由於 .NET Framework 和 .NET 中的 API 介面類別似但不完全相同，因此您必須檢查哪些 Api 可在 .NET 上使用，而不是。 您可以使用 .NET 可攜性分析器工具來呈現 .NET 上所使用的 Api。 它會查看您應用程式的二進位層級、解壓縮所有呼叫的 Api，然後列出您的目標 framework 上無法使用的 Api ( .NET 5.0 （在此案例中) ）。

您可以在下列位置找到此工具的詳細資訊：

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

這項工具的有趣之處在于，它只會顯示來自您自己程式碼的差異，而不是來自外部套件的程式碼，您無法變更這些差異。 請記住，您應該已更新大部分的封裝，才能讓它們與 .NET 搭配使用。

### <a name="migrate-with-try-convert-tool"></a>使用 Try Convert 工具進行遷移

[Try Convert](https://github.com/dotnet/try-convert/releases)工具是遷移專案的絕佳方式。 它是一種全域工具，它會嘗試將您的專案檔從舊樣式升級為新的 SDK 樣式，並將適用的專案重定到 .NET 5。 安裝之後，您可以執行下列命令：

```dotnetcli
try-convert -p "<path to your project file>"
```

或：

```dotnetcli
try-convert -w "<path to your solution>"
```

工具嘗試進行轉換之後，請在 Visual Studio 中重載您的檔案，以執行和測試。 由於您的專案細節，嘗試轉換的可能性可能無法執行轉換。 在此情況下，您可以參考下列步驟。

#### <a name="migrate-manually"></a>手動遷移

1. 建立新的 .NET 專案

在大部分情況下，您會想要將現有的專案更新為新的 .NET 格式。 不過，您也可以建立新的專案，同時保留舊專案。 更新舊專案的主要缺點是您失去了設計工具支援，這對您和開發小組來說可能很重要。 如果您想要繼續使用設計工具，您必須建立與舊專案平行的新 .NET 專案，並共用資產。 如果您需要修改設計工具中的 UI 元素，您可以切換到舊的專案來進行這項作業。 而且，因為資產已連結，所以它們也會在 .NET 專案中更新。

適用于 .NET 的 [SDK 樣式專案](../../core/project-sdk/msbuild-props.md) 比 .NET Framework 的專案格式簡單許多。 除了先前提及的 `PackageReference` 專案之外，您還不需要再做更多工作。 新的專案格式 [預設包含具有特定副檔名](../../core/project-sdk/overview.md#default-includes-and-excludes)的檔案，例如 `.cs` 和檔案 `.xaml` ，而不需要將它們明確包含在專案檔中。

#### <a name="assemblyinfo-considerations"></a>AssemblyInfo 考慮

屬性會在 .NET 專案上自動產生。 如果專案包含 *AssemblyInfo.cs* 檔案，將會複製定義，而這會導致編譯衝突。 您可以將下列專案新增至 .NET 專案檔，以刪除較舊的 *AssemblyInfo.cs* 檔案或停用自動產生：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a>資源

內嵌的資源會自動包含，但是資源不是，因此您需要將資源遷移至新的專案檔。

#### <a name="package-references"></a>套件參考

您可以使用 [將 **packages.config 遷移至 PackageReference** ] 選項，輕鬆地將外部套件參考移至新的格式，如先前所述。

#### <a name="update-package-references"></a>更新套件參考

將您找到的套件版本更新為相容，如上一節所示。

### <a name="fix-the-code-and-build"></a>修正程式碼和組建

#### <a name="microsoftwindowscompatibility"></a>Microsoft 的相容性

如果您的應用程式相依于 .NET 上無法使用的 Api （例如登錄、Acl 或 WCF），則您必須包含套件的參考， `Microsoft.Windows.Compatibility` 以新增這些 Windows 特定的 api。 它們可在 .NET 上運作，但未包含，因為它們不是跨平臺。

有一個稱為 API 分析器的工具 (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) ，可協助您識別與您的程式碼不相容的 api。

#### <a name="use-if-directives"></a>使用 \# if 指示詞

如果您在以 .NET Framework 和 .NET 為目標時需要不同的執行路徑，您應該使用編譯常數。 將某些 if 指示詞新增 \# 至您的程式碼，以保持兩個目標的相同程式碼基底。

#### <a name="technologies-not-available-on-net"></a>.NET 上無法使用的技術

有些技術無法在 .NET 上使用，例如：

* AppDomain
* 遠端
* 程式碼存取安全性
* WCF 伺服器
* Windows Workflow

這就是為什麼當您在應用程式中使用這些技術時，需要找出這些技術的取代。 如需詳細資訊，請參閱 [.Net Core 和 .net 5 + 上無法使用的 .NET Framework 技術](../../core/porting/net-framework-tech-unavailable.md) 文章。

#### <a name="regenerate-autogenerated-clients"></a>重新產生自動產生的用戶端

如果您的應用程式使用自動產生的程式碼（例如 WCF 用戶端），您可能需要重新產生此程式碼以將目標設為 .NET。 有時候，您可以找到一些遺漏的參考，因為它們可能不會包含在預設 .NET 元件集的一部分。 您可以使用類似的工具 <https://apisof.net/> ，輕鬆地找出遺漏參考所在的元件，並從 NuGet 新增該元件。

#### <a name="rolling-back-package-versions"></a>正在回復套件版本

一般來說，我們之前說過，您可以更妥善地更新每個單一套件版本，使其與 .NET 相容。 不過，您可以找到以更新版本與相容版本為目標的元件，而不需要支付任何費用。 如果無法接受變更的成本，您可以考慮將封裝版本保留在 .NET Framework 上的版本。 雖然它們可能不是以 .NET 為目標，但它們應該可以正常運作，除非它們呼叫一些不支援的 Api。

### <a name="run-and-test"></a>執行和測試

當您的應用程式在建立時沒有錯誤，您可以藉由測試每項功能來開始進行遷移的最後一個步驟。

在最後一個步驟中，您可以根據應用程式的複雜度，以及您所使用的相依性和 Api，找到幾個不同的問題。

例如，如果您使用設定檔 (*app.config*) ，您可能會在執行時間發現某些錯誤，例如不存在的設定區段。 使用 `Microsoft.Extensions.Configuration` NuGet 套件應該可修正該錯誤。

錯誤的另一個原因是使用 `BeginInvoke` 和方法， `EndInvoke` 因為它們在 .net 上不受支援。 .NET 不支援它們，因為它們相依于不存在於 .NET 的遠端處理。 若要解決此問題，請嘗試使用 `await` 關鍵字 (（如果有) 或 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 方法）。

您可以使用相容性分析器，來識別程式碼中的 Api 和程式碼模式，其可能會在執行時間使用 .NET 來產生問題。 移至 <https://github.com/dotnet/platform-compat> 並在您的專案上使用 .NET API 分析器。

## <a name="migrating-a-windows-forms-application"></a>遷移 Windows Forms 應用程式

為了展示 Windows Forms 應用程式的完整遷移程式，我們選擇遷移中提供的 eShop 範例應用程式 <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> 。 您可以在中找到遷移的完整結果 <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> 。

此應用程式會顯示產品目錄，並可讓使用者流覽、篩選和搜尋產品。 從架構的觀點來看，應用程式依賴作為後端資料庫外觀的外部 WCF 服務。

您可以在下圖中看到主要的應用程式視窗：

![主應用程式視窗](./media/example-migration-core/main-application-window.png)

如果您開啟 *.csproj* 專案檔，則會看到如下的內容：

![.Csproj 檔案內容的螢幕擷取畫面](./media/example-migration-core/csproj-file.png)

如先前所述，.NET 專案有更精簡的樣式，而您需要將專案結構遷移至新的 .NET SDK 樣式。

在 [方案總管中，以滑鼠右鍵按一下 Windows Forms 專案，然後選取 **[卸載專案**  >  **編輯**]。

現在您可以更新 .csproj 檔案。 您將刪除整個內容，並將它取代為下列程式碼：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

儲存並重載專案。 您現在已完成更新專案檔案，且專案的目標為 .NET。

如果您在此時編譯專案，您會發現一些與 WCF 用戶端參考相關的錯誤。 因為此程式碼會自動產生，所以您必須將它重新產生成以 .NET 為目標。

![Visual Studio 上編譯錯誤的螢幕擷取畫面](./media/example-migration-core/winforms-compilation-errors.png)

刪除 *Reference.cs* 檔案並產生新的服務用戶端。

以滑鼠右鍵按一下 **已連線的服務** ，然後選取 [ **加入已連接服務** ] 選項。

![已選取 [加入已連接服務] 選項之 [已連線的服務] 功能表的螢幕擷取畫面](./media/example-migration-core/add-connected-service.png)

已連線的服務] 視窗隨即開啟。 選取 [ **MICROSOFT WCF Web 服務** ] 選項。

![已連線的服務視窗的螢幕擷取畫面](./media/example-migration-core/connected-services-window.png)

如果您在此範例中的相同方案中有 WCF 服務，您可以選取 [ **探索** ] 選項，而不是指定服務 URL。

![[設定 WCF Web Service Reference] 視窗的螢幕擷取畫面](./media/example-migration-core/configure-wcf-reference.png)

一旦找到服務之後，此工具就會反映服務所執行的 API 合約。 將命名空間的名稱變更如下 `eShopServiceReference` 圖所示：

![API 合約和命名空間已變更的螢幕擷取畫面](./media/example-migration-core/api-contract-namespace.png)

選取 [ **完成]** 按鈕。 經過一段時間之後，您會看到產生的程式碼。

您應該會看到三個自動產生的檔案：

1. *開始使用*： GitHub 的連結，可提供 WCF 的一些資訊。
2. *ConnectedService.json*：用來連接到服務的設定參數。
3. *Reference.cs*：實際的 WCF 用戶端程式代碼。

![包含三個自動產生檔案之方案總管視窗的螢幕擷取畫面](./media/example-migration-core/autogenerated-files.png)

如果您再次編譯，您將會看到來自協助 *程式資料夾內* *.cs* 檔案的許多錯誤。 此資料夾存在於 .NET Framework 版本中，但不包含在舊的 *.csproj* 中。 但在新的 SDK 樣式專案中，預設會包含專案檔位置底下的每個程式碼檔案。 也就是說，新的 .NET Core 專案會嘗試編譯 *Helper* 資料夾內的檔案。 因為不需要該資料夾，所以您可以安全地將其刪除。

如果您重新編譯專案並加以執行，您將不會看到產品影像。 問題在於現在檔案的路徑稍有變更。 若要修正此問題，您必須在路徑中新增另一個深度層級，並在檔案中更新 `CatalogView.cs` ：

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

to

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

在此變更之後，您可以檢查應用程式在 .NET Core 上啟動並如預期般執行。

## <a name="migrating-a-wpf-application"></a>遷移 WPF 應用程式

我們將使用 `Shop.ClassicWPF` 範例應用程式來執行遷移。 下圖顯示在遷移之前的應用程式螢幕擷取畫面：

![遷移之前的範例應用程式](./media/example-migration-core/app-before-migration.png)

此應用程式會使用本機 SQL Server Express 資料庫來保存產品目錄資訊。 您可以直接從 WPF 應用程式存取此資料庫。

首先，您必須將 *.csproj* 檔案更新為 .net Core 應用程式所使用的新 SDK 樣式。 您將遵循 Windows Forms 遷移中所述的相同步驟：您將卸載專案、開啟 *.csproj* 檔案、更新其內容，然後重載專案。

在此情況下，請刪除 *.csproj* 檔案的所有內容，並將它取代為下列程式碼：

```xml
 <Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWpf>true</UseWpf>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

如果您重載專案並加以編譯，您將會收到下列錯誤：

![Visual Studio 上編譯錯誤的螢幕擷取畫面](./media/example-migration-core/wpf-compilation-error.png)

由於您已刪除所有 *.csproj* 內容，因此您已遺失存在於舊專案中的專案參考規格。 您只需要將這一行新增至 *.csproj* 檔案，就可以包含專案參考：

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

您也可以在 [相依性] 節點上按一下滑鼠右鍵，然後選取 [**加入專案參考** **]** ，讓 Visual Studio 協助您。 從方案中選取專案，然後按一下 **[確定]**：

![已選取 eShop SqlProvider 專案的 [參考管理員] 對話方塊螢幕擷取畫面](./media/example-migration-core/reference-manager.png)

一旦您加入遺漏的專案參考之後，應用程式就會在 .NET 上以預期的方式編譯和執行。

>[!div class="step-by-step"]
>[上一個](windows-migration.md) 
>[下一步](deploy-modern-applications.md)
