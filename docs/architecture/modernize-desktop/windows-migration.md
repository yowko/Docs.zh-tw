---
title: Windows 10 遷移
description: 深入探討 Windows 10 的功能，例如封裝和 XAML 孤島。
ms.date: 12/29/2020
ms.openlocfilehash: 139a8f2354803dafeb0178b4dbfb57a95c4ddb34
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615941"
---
# <a name="windows-10-migration"></a>Windows 10 遷移

請考慮下列情況：您有在 Windows 7 天內開發的工作桌面應用程式。 它會在當時使用 WPF 技術並正常運作，但當您在 Windows 10 上執行時，它會有過期的 UI 和行為。 當您監看幻想式道具的影片（例如矩陣）時，您會看到使用 Nokia 8110 裝置的 Neo。 在20年後，電影的運作良好，但它可以從裝置現代化中獲益。

隨著 Windows 10 的發行，Microsoft 引進了許多創新來支援平板電腦和觸控裝置等案例，並為 Microsoft 作業系統的使用者提供最佳體驗。 例如，您可以：

- 使用 Windows Hello 以您的臉部登入。
- 使用畫筆繪製或手寫自動辨識和以數位化的文字。
- 使用 WinML 執行以雲端為基礎的本機自訂 AI 模型。

Windows 開發人員可透過 Windows 執行階段 (WinRT) 程式庫來啟用這些功能。 您可以在現有的桌面應用程式中利用這些功能，因為這些程式庫也會同時公開給 .NET Framework 和 .NET。 您甚至可以使用 XAML 孤島來將 UI 現代化，並根據時間來改善應用程式的視覺效果和行為。

要注意的一點是，您不需要放棄 .NET Framework 技術來遵循此現代化路徑。 您可以安全地保持在該處，並享有 Windows 10 的所有優點，而不會有遷移至 .NET 的壓力。 這樣一來，您就能同時享有選擇現代化途徑的能力和彈性。

## <a name="winrt-apis"></a>WinRT Api

WinRT Api 是物件導向、結構完善的應用程式開發介面， (Api) ，可讓 Windows 10 開發人員存取作業系統所提供的所有專案。 透過 WinRT Api，您可以將推播通知、裝置 Api、Microsoft 筆跡和 WinML 等功能整合至桌面應用程式中的其他專案。

一般來說，您可以從傳統桌面應用程式呼叫 WinRT Api。 不過，有兩個主要區域表示此規則的例外狀況：

* 需要套件身分識別的 Api。
* 需要 XAML 或組合等視覺效果的 Api。

### <a name="universal-windows-platform-uwp-packages"></a>通用 Windows 平臺 (UWP) 套件

#### <a name="application-package-identity"></a>應用程式套件識別

UWP 應用程式有一個部署系統，作業系統會在此管理應用程式的安裝和卸載。 這需要宣告安裝，這表示在安裝期間不會執行任何使用者程式碼。 相反地，應用程式會在應用程式資訊清單中宣告應用程式想要與系統整合的所有專案，例如通訊協定、檔案類型和延伸模組。 部署管線會在部署階段設定這些整合點。 作業系統管理所有這項功能並加以追蹤的唯一方法，是讓每個「套件」具有身分識別，也就是應用程式的唯一識別碼。

某些 WinRT Api 需要此套件身分識別才能如預期般運作。 不過，傳統桌面應用程式（例如原生 c + + 或 .NET 應用程式）會使用不需要套件身分識別的不同部署系統。 如果您想要在桌面應用程式中使用這些 WinRT Api，您必須為它們提供套件身分識別。

其中一個方法是建立額外的封裝專案。 在封裝專案中，您會指向原始原始程式碼專案，並指定您想要提供的身分識別資訊。 如果您安裝套件並執行已安裝的應用程式，它會自動取得識別，讓您的程式碼能夠呼叫所有需要身分識別的 WinRT Api。

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

您可以藉由檢查包含 API 的類型是否以 [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) 屬性標記，來檢查哪些 api 需要已封裝的應用程式身分識別。 如果是，您可以從未封裝的傳統桌面應用程式呼叫。 否則，您必須在封裝專案的協助下，將您的傳統桌面應用程式轉換成 UWP。

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a>封裝的優點

除了提供這些 Api 的存取權之外，您還可以建立桌面應用程式的 Windows 應用程式套件，以獲得一些額外的優點，包括：

* **簡化部署**。 應用程式有絕佳的部署體驗，可確保使用者可以安心地安裝應用程式並加以更新。 如果使用者選擇卸載應用程式，該應用程式就會完全移除，而不會留下任何追蹤，以防止發生 Windows rot 問題。

* **自動更新和授權**。 您的應用程式可以參與 Microsoft Store 的內建授權和自動更新功能。 由於自動更新只會下載檔案已變更的部分，因此是一項非常可靠又有效率的機制。

* **增加觸達對象並簡化營利**。 也許不是您的情況，但如果您選擇透過 Microsoft Store 散發您的應用程式，您就會到達數百萬個 Windows 10 使用者。

* **新增 UWP 功能**。 您可以依照自己的步調，將 UWP 功能新增至您的應用程式套件。

#### <a name="prepare-for-packaging"></a>準備封裝

在繼續封裝您的桌面應用程式之前，您必須先解決一些需要的問題，才能開始進行處理。 您的應用程式必須遵守任何 Microsoft Store 規則和原則，並在 UWP 應用程式模型中執行。 例如，它必須在 .NET Framework 4.6.2 或更新版本上執行，並寫入登錄區 `HKEY_CURRENT_USER` ，而 AppData 資料夾將會虛擬化到使用者特定的應用程式本機位置。

封裝的設計目的是要將應用程式狀態與系統狀態分開，同時維持與其他應用程式的相容性。 Windows 10 將應用程式放在 UWP 套件內以達成此目標。 它會在執行時間偵測和重新導向檔案系統和登錄的一些變更，以滿足封裝所提供之應用程式的受信任和全新安裝和卸載行為的承諾。

您為桌面應用程式所建立的套件是僅限桌面的完全信任應用程式，不會進行沙箱化，不過會有適用于應用程式的輕量虛擬化來寫入 `HKCU` 和 `AppData` 。 此虛擬化可讓它們與傳統桌面應用程式相同的方式，與其他應用程式互動。

##### <a name="installation"></a>安裝

應用程式套件會安裝在 *% ProgramFiles% \\ WindowsApps \\ package_name* 下，並具有標題為的可執行檔 `app_name.exe` 。 每個套件資料夾都包含名為 `AppxManifest.xml`) 的資訊清單 (，其中包含已封裝應用程式的特殊 XML 命名空間。 該資訊清單檔案內部是一個 `<EntryPoint>` 項目，它會參考完全信任的 App。 當該應用程式啟動時，它不會在應用程式容器內執行，而是以一般使用者的身份執行。

部署之後，套件檔案會由作業系統標示為唯讀並嚴密地鎖定。 如果這些檔案遭到竄改，Windows 會防止這些 App 啟動。

##### <a name="file-system"></a>檔案系統

作業系統針對封裝的桌面應用程式支援不同層級的檔案系統作業，視資料夾位置而定。

當您嘗試存取使用者的 *AppData* 資料夾時，系統會在幕後建立私用每位使用者、每個應用程式的位置。 這會建立封裝的應用程式在實際修改私用複本時，正在編輯真正 *AppData* 的假像。 透過這種方式將寫入重新導向，系統就可以追蹤 App 執行的所有檔案修改。 然後，它會在卸載減少系統 "rot" 時清除所有這些檔案，並為使用者提供更好的應用程式移除體驗。

##### <a name="registry"></a>登錄

應用程式套件包含登錄 .dat 檔案，其可做為實際登錄中的邏輯對等專案 `HKLM\Software` 。 在執行階段，此虛擬登錄會將此登錄區的內容合併至原生系統登錄區，以提供兩者的單一檢視。

所有寫入都會在封裝升級期間保留，而且只會在應用程式卸載時刪除。

##### <a name="uninstallation"></a>解除安裝

當使用者卸載套件時，會移除位於下的所有檔案和資料夾，以及在 `C:\Program Files\WindowsApps\package_name` 處理過程中所捕捉到 AppData 或登錄的任何重新導向的寫入。

如需封裝的應用程式如何處理安裝、檔案存取、登錄和卸載的詳細資訊，請參閱 <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> 。

您可以取得要檢查的完整專案清單 <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> 。

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a>如何將 WinRT Api 新增至您的桌面專案

在本節中，您可以找到如何在現有的 WPF 應用程式中整合快顯通知的逐步解說。 雖然從程式碼的觀點來看很簡單，但它有助於說明整個過程。 通知是可在 .NET 應用程式中使用的許多可用的 WinRT Api 之一。 在此情況下，API 需要套件身分識別。 如果 Api 不需要套件身分識別，此程式會比較簡單。

讓我們來看一個現有的 WPF 範例應用程式，它會讀取檔案，並在畫面上顯示其內容。 其目標是要在應用程式啟動時顯示快顯通知。

![執行範例應用程式的螢幕擷取畫面](./media/windows-migration/sample-application.png)

首先，您應該簽入下列連結，指出您將使用的 Windows 10 API 是否需要套件身分識別：

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

我們的範例會使用 <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> 需要已封裝身分識別的 API：

![Microsoft 檔中的通知類別](./media/windows-migration/notification-class-documentation.png)

若要存取 WinRT API，請新增 NuGet 套件的參考， `Microsoft.Windows.SDK.Contracts` 此套件將會在幕後進行魔術 (查看) 的詳細資料 <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> 。

您現在已經準備好開始加入一些程式碼。

建立 `ShowToastNotification` 在應用程式啟動時所要呼叫的方法。 它只會從 XML 模式建立快顯通知：

```csharp
private void ShowNotification(string title, string content, string image)
{
    string xmlString = $@"<toast><visual><binding template = 'ToastGeneric'><text>{title}</text><text>{content}</text><image src=>'{image}'</image></binding></visual></toast>";
    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);
    ToastNotification toast = new ToastNotification(toastXml);
    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

雖然專案會建立，但有錯誤，因為通知 API 需要套件身分識別，但您未提供。 將 Windows 封裝專案新增至方案將可修正此問題：

![Visual Studio 中 [新增專案] 對話方塊的螢幕擷取畫面](./media/windows-migration/add-packaging-project.png)

選取您要支援的最低 Windows 版本和您的目標版本。 並非所有的 WinRT Api 都支援所有的 Windows 10 版本。 每個 Windows 10 更新都會新增僅適用于此版本的新 Api;無法使用下層支援。

![選取最小 Windows 版本](./media/windows-migration/select-versions.png)

下一步是新增專案參考，以將 WPF 應用程式新增至 Windows 封裝專案：

![將 WPF 應用程式新增至 Windows 封裝專案](./media/windows-migration/add-application.png)

![參考管理員](./media/windows-migration/reference-manager.png)

Windows 封裝專案可以封裝數個應用程式，因此您應該設定哪一個是進入點：

![設定進入點](./media/windows-migration/set-entry-point.png)

下一步是要將 WPF 專案設定為方案設定中的啟始專案。 您可以按 F5 來編譯和建立結果，並查看結果。

![執行範例應用程式並顯示結果](./media/windows-migration/sample-app-result.png)

讓我們產生套件，讓您可以安裝應用程式。 以滑鼠右鍵按一下 [**存放區**  >  **建立應用程式套件**]。

![[建立應用程式套件] 對話方塊](./media/windows-migration/create-app-packages.png)

選取側載選項以從您的電腦部署應用程式：

![選取側載選項](./media/windows-migration/select-sideloading-option.png)

選取應用程式的應用程式架構：

![選取應用程式架構](./media/windows-migration/select-app-architecture.png)

最後，按一下 [ **建立**] 建立封裝。

## <a name="xaml-islands"></a>XAML Islands

XAML 孤島是一組元件，可讓 Windows 桌面開發人員在其現有的 Win32 應用程式（包括 Windows Forms 和 WPF）上使用 UWP XAML 控制項。

![XAML 島的結構](./media/windows-migration/xaml-islands.png)

您可以使用標準控制項來為您的 Win32 應用程式進行映射處理，並在其中提供 UWP UI 的「島」，其中包含來自現代化世界的控制項。 概念類似于在 web 網頁內擁有 iFrame，以顯示來自 `different page.`

除了從 Windows 10 Api 新增功能之外，您還可以使用 XAML 孤島，在應用程式內新增 UWP XAML 的片段。

Windows 10 1903 update 引進了一組 Api，可讓您在 Win32 視窗中裝載 UWP XAML 內容。 只有在 Windows 10 1903 上執行的應用程式可以使用 XAML 孤島。

### <a name="the-road-to-xaml-islands"></a>XAML 島的道路

從2012開始，在 Microsoft 推出 WinRT Api 作為架構，將 Win32 應用程式 (Windows Forms、WPF 和原生 Win32 應用程式) 。 不過，WinRT 內的新 UI 控制項可用於新的應用程式，但不適用於現有的應用程式。

在2015中，除了 Windows 10 之外，還誕生了 UWP。 UWP 可讓您建立可跨 Windows 裝置運作的應用程式，例如 XBox、行動裝置和桌上型電腦。 一年之後，Microsoft 宣佈傳統型橋接器 (之前稱為 Project Centennial) 。 傳統型橋接器是一組工具，可以讓開發人員將其現有的 Win32 應用程式帶入 Microsoft Store。 2017中新增了更多功能，讓開發人員能夠利用一些新的 Windows 10 Api （例如控制中心上的動態磚和通知）來增強其 Win32 應用程式。 但還是沒有新的 UI 控制項。

在組建2018中，Microsoft 宣佈了一個方法，讓開發人員能夠使用新的 Windows 10 XAML 控制項進入其目前的 Win32 應用程式，而不需將應用程式完整遷移至 UWP。 其品牌為 UWP XAML 島。

### <a name="how-it-works"></a>運作方式

Windows 10 1903 更新導入了數個 XAML 裝載 Api。 其中兩個是 `WindowsXamlManager` 和 `DesktopWindowXamlSource` 。

`WindowsXamlManager`類別會處理 UWP XAML 架構。 其 `InitializeForCurrentThread` 方法會將 UWP XAML 架構載入至 Win32 應用程式的目前線程內。

`DesktopWindowXamlSource`是您的 XAML 島內容實例。 它有 `Content` 您負責具現化和設定的屬性。 會 `DesktopWindowXamlSource` 呈現並從 HWND 取得其輸入。 它必須知道它將附加 XAML 島的其他 HWND，而且您必須負責調整父項的 HWND 的大小與位置。

WPF 或 Windows Forms 開發人員通常不會在程式碼中處理 HWND，因此很難瞭解並處理 HWND 指標和基礎接線內容，以傳達 Win32 和 UWP 的世界。

#### <a name="the-xaml-islands-net-wrappers"></a>XAML 島 .NET 包裝函式

Windows 社群工具組有一組適用于 WPF 或 Windows Forms 的 XAML 島 .NET 包裝函式，可讓您更輕鬆地使用 XAML 孤島。 這些包裝函式會管理 Hwnd、焦點管理及其他專案。 Windows Forms 和 WPF 開發人員應該使用這些包裝函式。

Windows 社群工具組提供兩種類型的控制項：包裝的控制項和裝載控制項。

##### <a name="wrapped-controls"></a>包裝的控制項

這些包裝的控制項會將某些 UWP 控制項包裝成 Windows Forms 或 WPF 控制項，為這些開發人員隱藏 UWP 概念。 這些控制項包括：

* Web 上和 WebViewCompatible
* InkCanvas 和 InkToolbar
* MediaPlayerElement
* MapControl

將 `Microsoft.Toolkit.Wpf.UI.Controls` 套件新增至您的專案，並包含命名空間的參考，然後開始使用。

```xml
<Window
        ...
        xmlns:uwpControls="clr-namespace:Microsoft.Toolkit.Wpf.UI.Controls;assembly=Microsoft.Toolkit.Wpf.UI.Controls">
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="\*"/>
    </Grid.RowDefinitions>
    <uwpControls:InkToolbar TargetInkCanvas="{x:Reference Name=inkCanvas}"/>
    <uwpControls:InkCanvas Grid.Row="1" x:Name="inkCanvas" />
</Grid>
```

##### <a name="hosting-controls"></a>裝載控制項

XAML 島的威力延伸至大部分的第一方控制項、協力廠商控制項，以及針對 UWP 開發的自訂控制項，這些控制項可整合至 Windows Forms 和 WPF 作為具有完整功能的 UI 的「孤島」。 `WindowsXamlHost`WPF 和 Windows Forms 的控制項可讓您這樣做。

例如，若要 `WindowsXamlHost` 在 WPF 中使用控制項，請將參考加入 `Microsoft.Toolkit.Wpf.UI.XamlHost` Windows 社群工具組所提供的封裝。

將放 `WindowsXamlHost` 入您的 UI 程式碼之後，請指定您想要載入的 UWP 類型。 您可以選擇使用包裝的控制項（例如 `Button` 或更複雜的控制項），其由數個不同的控制項（自訂 UWP 控制項）所組成。

下列範例顯示如何新增 UWP `Button` ：

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

有一個清楚的建議，就是如何進行這項處理，最好有一個包含自訂複合控制項的單一和大型 XAML 島，而不是每個島都有一個控制項。

XAML 的其中一個核心功能是系結，而且可在您的 Win32 程式碼和島之間運作。 如此一來，您就可以系結 `Textbox` 具有 UWP 的 Win32 `Textbox` 。 要考慮的一個重要事項是，這些系結是從 UWP 到 Win32 的單向系結，因此，如果您在 `Textbox` XAML 島內部更新，Win32 Textbox 將會更新，但不會以其他方式進行更新。

若要查看如何使用 XAML 孤島的逐步解說，請參閱：

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a>新增 UWP XAML 自訂控制項

XAML 自訂控制項是由您或協力廠商所建立的控制項 (或使用者控制項)  (包括 WinUI 2.x 控制項) 。 若要在 Windows Forms 或 WPF 應用程式中裝載自訂 UWP 控制項，您需要：

- `WindowsXamlHost`在您的 .net 應用程式中使用 UWP 控制項。
- 建立定義物件的 UWP 應用程式專案 `XamlApplication` 。

您的 WPF 或 Windows Forms 專案必須能夠存取 Windows 社群工具組所 `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` 提供之類別的實例。 此物件可作為根中繼資料提供者，以在應用程式目前目錄中的元件中載入自訂 UWP XAML 類型的中繼資料。 建議的作法是將空白應用程式 (通用 Windows) 專案加入至與 WPF 或 Windows Forms 專案相同的方案，並在此專案中修改預設的應用程式類別。

自訂 UWP XAML 控制項可以包含在此 UWP 應用程式或獨立的 UWP 類別庫專案中，您可以在與 WPF 或 Windows Forms 專案相同的方案中參考此專案。

您可以在下列位置查看詳細的逐步流程說明：

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a>Windows UI 程式庫 (WinUI 2) 

除了隨附于作業系統的收件匣 Windows 10 控制項，相同的 UWP XAML 小組也提供 Windows UI 程式庫中的其他控制項， (**WinUI 2**) 。 WinUI 2 為 Windows UWP 應用程式提供官方的原生 Microsoft UI 控制項和功能，這些控制項可以在 XAML 孤島內使用。

WinUI 2 是開放原始碼，您可以在中找到資訊 <https://github.com/microsoft/microsoft-ui-xaml> 。

下列文章示範如何從 WinUI 2 程式庫裝載 UWP XAML 控制項： <https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

### <a name="do-you-need-xaml-islands"></a>您需要 XAML 島

XAML 孤島適用于現有的 Win32 應用程式，這些應用程式想要藉由利用新的 UWP 控制項和行為來改善使用者體驗，而不需要完整重寫應用程式。 您可以 [充分利用 Windows 10 api](/windows/uwp/porting/desktop-to-uwp-enhance)，但在 XAML 孤島之前，只能使用非 UI 相關的 api。

如果您正在開發新的 Windows 應用程式， [UWP 應用程式](/windows/uwp/get-started/universal-application-platform-guide) 可能是正確的方法。

### <a name="the-road-ahead-xaml-islands-winui-30"></a>前方的 XAML 島： WinUI 3。0

由於 Windows 8，Windows UI 平臺（包括 XAML UI 架構、視覺效果組合圖層和輸入處理）已作為 Windows 不可或缺的一部分來出貨。 這表示若要受益于 UI 技術的最新改善，您必須升級至最新版本的 UI，並在開發應用程式時減緩創新的步調。 為了將這兩個演進週期分離並促進創新，Microsoft 正積極處理 WinUI 專案。

從2018的 WinUI 2 開始，Microsoft 開始將一些新的 XAML UI 控制項和功能，作為以 UWP SDK 為基礎的個別 NuGet 套件來傳送。

![WinUI 2.0 的結構](./media/windows-migration/winui2.png)

WinUI 3 正在進行開發，並且將大幅擴展 WinUI 的範圍，以包含完整的 UI 平臺，這會與 UWP SDK 完全分離：

![WinUI 3.0 的結構](./media/windows-migration/winui3.png)

XAML 架構現在會在 GitHub 上開發，並隨附于 [NuGet](/nuget/what-is-nuget) 套件外。

隨附於作業系統的現有 UWP XAML API 將不會再收到新的功能更新。 它們仍會根據 Windows 10 支援生命週期來接收安全性更新和重大修正。

通用 Windows 平臺包含的不只是 XAML 架構 (例如，應用程式和安全性模型、媒體管線、Xbox 和 Windows 10 shell 整合、廣泛裝置支援) ，而且會繼續演進。 所有新的 XAML 功能都只會在 WinUI 中開發和傳送。

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a>桌面應用程式中的 WinUI 3 和 WinUI XAML 島

如您所見，WinUI 3 是 UWP XAML 的演進，它可以自然地在 UWP 應用程式模型內運作，而且它的所有需求都 (MSIX 封裝識別碼、沙箱、CoreWindow 等等。 若只要在 Win32 應用程式模型中使用 WinUI 3，WinUI 內容應該由另一個 UI 架構（ (Windows Forms、WPF 等）裝載，而) 使用 **WINUI XAML 孤島**。 如果您想要發展您的應用程式和混合技術，這是正確的途徑。 但是，如果您想要將整個舊的 UI 取代為 WinUI，您的應用程式不應該載入僅裝載 WinUI 的 UI 架構。

WinUI 3 將解決 **在桌面應用程式中新增 WinUI 的** 重要意見反應。 這可讓 Win32 應用程式使用 WinUI 3 作為獨立 UI 架構;不需要載入 Windows Forms 或 WPF。

在此匯總中，WinUI 3 將可讓開發人員輕鬆地混合並符合下列各項的正確組合：

* 應用程式模型： UWP、Win32
* 平臺： .NET 或原生
* Language： .NET (C \# ，Visual Basic) ，Standard c + +
* 封裝： MSIX，AppX Microsoft Store，未封裝
* Interop：使用 WinUI 3，利用 WinUI XAML 孤島來擴充現有的 WPF、WinForms 和 MFC 應用程式。

如果您想要瞭解更多詳細資料，Microsoft 會在中分享此藍圖 <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> 。

>[!div class="step-by-step"]
>[上一個](migrate-modern-applications.md) 
>[下一步](example-migration.md)
