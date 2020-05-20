---
title: Windows 10 遷移
description: 深入探討 Windows 10 的功能，例如封裝和 XAML 群島。
ms.date: 09/16/2019
ms.openlocfilehash: cd17088b086a32fd3bb37e617d3a1047acedde0e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423205"
---
# <a name="windows-10-migration"></a>Windows 10 遷移

請考慮下列情況：您有一個在 Windows 7 天內開發的工作桌面應用程式。 它使用的是目前提供的 WPF 技術，而且可以正常運作，但當您在 Windows 10 上執行它時，它會有過時的 UI 和行為。 當您觀賞幻想式道具影片（例如矩陣），而您看到使用 Nokia 8110 裝置的 Neo 時，就是如此。 電影在20年後可正常運作，但它可以從裝置現代化中獲益。

隨著 Windows 10 的發行，Microsoft 引進了許多創新功能來支援平板電腦和觸控裝置等案例，並為 Microsoft 作業系統的使用者提供最佳的體驗。 例如，您可以：

- 使用 Windows Hello 登入您的臉部。
- 使用畫筆繪製或手寫自動辨識和 digitalized 的文字。
- 使用 WinML，在雲端上執行建置於本機的自訂 AI 模型。

Windows 開發人員可以透過 Windows 執行階段（WinRT）程式庫來啟用所有這些功能。 您可以在現有的桌面應用程式中利用這些功能，因為程式庫也會同時公開到 .NET Framework 和 .NET Core。 您甚至可以使用 XAML Islands 將您的 UI 現代化，並根據時間改善應用程式的視覺效果和行為。

這裡要注意的一點是，您不需要放棄 .NET Framework 技術，就能遵循這項現代化路徑。 您可以放心地掌握 Windows 10 的所有優點，而不需要遷移至 .NET Core。 因此，您可以同時取得選擇現代化路徑的能力和彈性。

## <a name="winrt-apis"></a>WinRT Api

WinRT Api 是物件導向、結構良好的應用程式設計介面（Api），可讓 Windows 10 開發人員存取作業系統所提供的所有專案。 透過 WinRT Api，您可以在桌面應用程式中整合功能，例如推播通知、裝置 Api、Microsoft 筆跡和 WinML。

一般來說，您可以從傳統桌面應用程式呼叫 WinRT Api。 不過，有兩個主要區域對此規則造成例外狀況：

* 需要套件身分識別的 Api。
* 需要 XAML 或複合等視覺效果的 Api。

### <a name="universal-windows-platform-uwp-packages"></a>通用 Windows 平臺（UWP）套件

#### <a name="application-package-identity"></a>應用程式套件識別

UWP 應用程式具有部署系統，作業系統會在其中管理應用程式的安裝和卸載。 這需要以宣告方式安裝，這表示在安裝期間不會執行任何使用者程式碼。 相反地，應用程式想要與系統整合的所有專案（例如通訊協定、檔案類型和擴充功能）都會在應用程式資訊清單中宣告。 在部署期間，部署管線會設定這些整合點。 作業系統管理所有這項功能並持續追蹤的唯一方法，是讓每個「套件」都有一個身分識別，也就是應用程式的唯一識別碼。

某些 WinRT Api 需要此套件身分識別才能如預期般運作。 不過，傳統的桌面應用程式（例如原生 c + + 或 .NET 應用程式）會使用不同的部署系統，而不需要套件身分識別。 如果您想要在桌面應用程式中使用這些 WinRT Api，您必須為它們提供套件識別。

其中一種方法是建立額外的封裝專案。 在封裝專案內，您要指向原始的原始程式碼專案，並指定您想要提供的身分識別資訊。如果您安裝套件並執行已安裝的應用程式，它會自動取得識別，讓您的程式碼能夠呼叫所有需要身分識別的 WinRT Api。

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

您可以藉由檢查包含 API 的類型是否以[DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute)屬性標記，以檢查哪些 api 需要已封裝的應用程式識別。如果是，您可以從未封裝的傳統桌面應用程式呼叫。 否則，您必須透過封裝專案的協助，將傳統桌面應用程式轉換成 UWP。

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a>封裝的優點

除了提供這些 Api 的存取權之外，您還可以建立桌面應用程式的 Windows 應用程式套件，以獲得一些額外的好處，包括：

* **簡化部署**。 應用程式具備絕佳的部署體驗，確保使用者可以安心地安裝應用程式並加以更新。 如果使用者選擇卸載應用程式，它會完全移除，且不會留下任何追蹤來防止 Windows rot 問題。

* **自動更新和授權**。 您的應用程式可以參與 Microsoft Store 的內建授權和自動更新功能。 由於自動更新只會下載檔案已變更的部分，因此是一項非常可靠又有效率的機制。

* **增加觸達對象並簡化營利**。 也許不是您的案例，但如果您選擇透過 Microsoft Store 散發應用程式，就會抵達數百萬部 Windows 10 使用者。

* **新增 UWP 功能**。 您可以依照自己的步調，將 UWP 功能新增至應用程式的套件。

#### <a name="prepare-for-packaging"></a>準備封裝

在繼續封裝您的桌面應用程式之前，您必須先處理幾個重點，才能開始處理。 您的應用程式必須遵守任何 Microsoft Store 規則和原則，並在 UWP 應用程式模型中執行。 例如，它必須在 .NET Framework 4.6.2 或更新版本上執行，並寫入登錄區 `HKEY_CURRENT_USER` ，而 AppData 資料夾將會虛擬化到使用者特定的應用程式-本機位置。

封裝的設計目標是要將應用程式狀態與系統狀態分開，同時維持與其他應用程式的相容性。 Windows 10 藉由將應用程式放在 UWP 套件內來完成此目標。 它會在執行時間偵測並重新導向檔案系統和登錄的某些變更，以滿足封裝所提供之應用程式的信任和全新安裝和卸載行為的承諾。

您為桌面應用程式建立的套件是僅限桌上型電腦的完全信任應用程式，不會進行沙箱處理，雖然應用程式已套用輕量虛擬化以寫入 `HKCU` 和 `AppData` 。 此虛擬化可讓他們以傳統桌面應用程式的相同方式與其他應用程式互動。

##### <a name="installation"></a>安裝

應用程式套件會安裝在 *% ProgramFiles% \\ WindowsApps \\ package_name*底下，且可執行檔標題為  `app_name.exe` 。 每個套件資料夾都包含資訊清單（名為 `AppxManifest.xml` ），其中包含已封裝應用程式的特殊 XML 命名空間。 在該資訊清單檔案內是一個  `<EntryPoint>`   元素，它會參考完全信任的應用程式。 當該應用程式啟動時，它不會在應用程式容器內執行，而是會以一般的使用者身分執行。

部署之後，套件檔案會由作業系統標示為唯讀並嚴密地鎖定。 如果這些檔案遭到竄改，Windows 會防止這些 App 啟動。

##### <a name="file-system"></a>檔案系統

作業系統支援封裝桌面應用程式的不同層級檔案系統作業，視資料夾位置而定。

嘗試存取使用者的*AppData*資料夾時，系統會在幕後建立私用的每個使用者、每個應用程式的位置。 這會建立封裝的應用程式在實際修改私用複本時，正在編輯實際*AppData*的假像。 透過這種方式將寫入重新導向，系統就可以追蹤 App 執行的所有檔案修改。 然後，它可以在卸載減少系統 "rot" 時清除所有這些檔案，並為使用者提供更好的應用程式移除體驗。

##### <a name="registry"></a>登錄

應用程式套件包含一個登錄 .dat 檔案，其可做為  `HKLM\Software` 實際登錄中的邏輯對等檔案   。 在執行階段，此虛擬登錄會將此登錄區的內容合併至原生系統登錄區，以提供兩者的單一檢視。

所有寫入都會在封裝升級期間保留，而且只會在應用程式卸載時刪除。

##### <a name="uninstallation"></a>解除安裝

當使用者卸載套件時，位於底下的所有檔案和資料夾  `C:\Program Files\WindowsApps\package_name` 都會被移除，以及在處理過程中所捕捉到的 AppData 或登錄的任何重新導向寫入。

如需封裝的應用程式如何處理安裝、檔案存取、登錄和卸載的詳細資訊，請參閱 <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> 。

您可以取得要檢查的完整專案清單 <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> 。

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a>如何將 WinRT Api 新增至您的桌面專案

在本節中，您可以找到如何整合現有 WPF 應用程式中快顯通知的逐步解說。 雖然程式碼的觀點很簡單，但它有助於說明整個程式。 通知是您可以在 .NET 應用程式中使用的許多可用的 WinRT Api 之一。 在此情況下，API 需要套件身分識別。 如果 Api 不需要套件身分識別，則此程式更直接。

讓我們來看一個現有的 WPF 範例應用程式，它會讀取檔案，並在螢幕上顯示其內容。 其目標是要在應用程式啟動時顯示快顯通知。

![執行中範例應用程式的螢幕擷取畫面](./media/windows-migration/sample-application.png)

首先，您應該簽入下列連結，不論您要使用的 Windows 10 API 是否需要套件身分識別：

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

我們的範例會使用 <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> 需要已封裝身分識別的 API：

![Microsoft 檔中的通知類別](./media/windows-migration/notification-class-documentation.png)

若要存取 WinRT API，請將參考新增至 `Microsoft.Windows.SDK.Contracts`   NuGet 套件，此套件將會在幕後執行魔術（請參閱中的詳細資料 <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> ）。

您現在已經準備好開始新增一些程式碼。

建立 `ShowToastNotification` 將在應用程式啟動時呼叫的方法。 它只會從 XML 模式建立快顯通知：

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

雖然專案會建立，但有一些錯誤，因為通知 API 需要套件識別，但您並未提供它。 將 Windows 封裝專案新增至方案將會修正此問題：

![Visual Studio 中 [新增專案] 對話方塊的螢幕擷取畫面](./media/windows-migration/add-packaging-project.png)

選取您想要支援的最低 Windows 版本，以及您的目標版本。 並非所有的 Windows 10 版本都支援所有 WinRT Api。 每個 Windows 10 更新都會加入僅此版本提供的新 Api;下層支援無法使用。

![選取最低 Windows 版本](./media/windows-migration/select-versions.png)

下一個步驟是藉由新增專案參考，將 WPF 應用程式新增至 Windows 封裝專案：

![將 WPF 應用程式新增至 Windows 封裝專案](./media/windows-migration/add-application.png)

![參考管理員](./media/windows-migration/reference-manager.png)

Windows 封裝專案可以封裝數個應用程式，因此您應該設定哪一個是進入點：

![設定進入點](./media/windows-migration/set-entry-point.png)

下一步是在解決方案設定中，將 WPF 專案設為啟始專案。 您可以按 F5 來編譯並查看結果。

![執行和顯示結果的範例應用程式](./media/windows-migration/sample-app-result.png)

讓我們產生套件，讓您可以安裝您的應用程式。 以滑鼠右鍵按一下 [**存放區**] [  >  **建立應用程式套件**]。

![[建立應用程式套件] 對話方塊](./media/windows-migration/create-app-packages.png)

選取 [側載] 選項以從您的電腦部署應用程式：

![選取側載選項](./media/windows-migration/select-sideloading-option.png)

選取您應用程式的應用程式架構：

![選取應用程式架構](./media/windows-migration/select-app-architecture.png)

最後，按一下 [**建立**] 來建立封裝。

## <a name="xaml-islands"></a>XAML Islands

XAML 孤島是一組元件，可讓 Windows 桌面開發人員在其現有的 Win32 應用程式（包括 Windows Forms 和 WPF）上使用 UWP XAML 控制項。

![XAML 群島的結構](./media/windows-migration/xaml-islands.png)

您可以使用您的標準控制項來進行 Win32 應用程式的映射，並在其中包含來自現代化世界之控制項的「島」 UWP UI。 概念類似于在網頁內擁有一個 iFrame，其中顯示來自的內容`different page.`

除了從 Windows 10 Api 新增功能之外，您還可以使用 XAML 島，在應用程式內新增 UWP XAML 的片段。

Windows 10 1903 update 引進了一組 Api，可讓您在 Win32 視窗中裝載 UWP XAML 內容。 只有在 Windows 10 1903 上執行的應用程式可以使用 XAML 島。

### <a name="the-road-to-xaml-islands"></a>XAML 島的道路

當 Microsoft 引進 WinRT Api 做為架構，將 Win32 應用程式（Windows Forms、WPF 和原生 Win32 應用程式）現代化時，從2012開始的 XAML 孤島。 不過，WinRT 中新的 UI 控制項適用于新的應用程式，但不適用於現有的應用程式。

隨著 Windows 10 的2015，UWP 已經出生。 UWP 可讓您建立可跨 Windows 裝置（例如 XBox、Mobile 和 Desktop）工作的應用程式。 一年後，Microsoft 宣佈了桌面橋接器（先前稱為 Project Centennial）。 桌面橋接器是一組工具，可讓開發人員將其現有的 Win32 應用程式帶入 Microsoft Store。 2017中新增了更多功能，可讓開發人員利用一些新的 Windows 10 Api 來增強其 Win32 應用程式，例如行動中心的動態磚和通知。 但還是沒有新的 UI 控制項。

在組建2018中，Microsoft 宣佈了一種方法，讓開發人員可以將新的 Windows 10 XAML 控制項用於目前的 Win32 應用程式，而不需要將其應用程式完全遷移至 UWP。 其品牌為 UWP XAML 群島。

### <a name="how-it-works"></a>運作方式

Windows 10 1903 update 引進數個 XAML 裝載 Api。 其中兩個是 `WindowsXamlManager`   和  `DesktopWindowXamlSource` 。

 `WindowsXamlManager`   類別會處理 UWP XAML 架構。 其 `InitializeForCurrentThread` 方法會在 Win32 應用程式的目前線程內載入 UWP XAML 架構。

 `DesktopWindowXamlSource`   是 XAML 島內容的實例。 它具有 `Content` 屬性，您必須負責具現化和設定。 會 `DesktopWindowXamlSource`   呈現並從 HWND 取得其輸入。 它需要知道它將附加 XAML 島的其他 HWND，而且您必須負責調整大小和定位父系的 HWND。

WPF 或 Windows Forms 開發人員通常不會處理其程式碼內的 HWND，因此可能很難瞭解並處理 HWND 指標和基礎接線內容，以溝通 Win32 和 UWP 的世界。

#### <a name="the-xaml-islands-net-wrappers"></a>XAML 島 .NET 包裝函式

Windows 社區工具組已設定適用于 WPF 或 Windows Forms 的 XAML 島 .NET 包裝函式，可讓您更輕鬆地使用 XAML 島。 這些包裝函式會管理 Hwnd、焦點管理及其他專案。 Windows Forms 和 WPF 開發人員應該使用這些包裝函式。

Windows 社區工具組提供兩種類型的控制項：包裝的控制項和裝載控制項。

##### <a name="wrapped-controls"></a>包裝的控制項

這些包裝的控制項會將一些 UWP 控制項包裝到 Windows Forms 或 WPF 控制項中，以隱藏這些開發人員的 UWP 概念。 這些控制項包括：

* Web 視圖和 WebViewCompatible
* InkCanvas 和 InkToolbar
* MediaPlayerElement
* MapControl

將 `Microsoft.Toolkit.Wpf.UI.Controls` 套件新增至您的專案，包括命名空間的參考，然後開始使用它們。

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

XAML 島的強大功能延伸至大部分的第一方控制項、協力廠商控制項，以及針對 UWP 所開發的自訂控制項，可以整合到 Windows Forms 和 WPF 做為具有完整功能 UI 的「群島」。 `WindowsXamlHost`WPF 和 Windows Forms 的控制項允許這麼做。

例如，若要 `WindowsXamlHost` 在 WPF 中使用控制項，請將參考新增至 `Microsoft.Toolkit.Wpf.UI.XamlHost` Windows 社區工具組所提供的封裝。

將放 `WindowsXamlHost` 入 UI 程式碼之後，請指定您要載入的 UWP 類型。 您可以選擇使用包裝的控制項，例如， `Button` 或由數個不同控制項（自訂 UWP 控制項）所組成的更複雜的控制項。

下列範例顯示如何新增 UWP `Button` ：

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

有一個清楚的建議可以解決這種情況，而且最好要有一個包含自訂複合控制項的單一且更大的 XAML 島，而不是每個有一個控制項的孤島。

XAML 的核心功能之一就是系結，而且它可以在您的 Win32 程式碼與島之間運作。 因此，您可以系結 `Textbox` 具有 UWP 的 Win32 `Textbox` 。 其中一個要考慮的重要事項是，這些系結是單向系結，從 UWP 到 Win32，因此如果您在 `Textbox` XAML 島內部更新，Win32 文字方塊就會更新，但不會有其他的影響。

若要查看如何使用 XAML Islands 的逐步解說，請參閱：

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a>新增 UWP XAML 自訂控制項

XAML 自訂控制項是由您或協力廠商（包括 WinUI 2.x 控制項）所建立的控制項（或使用者控制項）。 若要在 Windows Forms 或 WPF 應用程式中裝載自訂 UWP 控制項，您需要：

- `WindowsXamlHost`在您的 .Net Core 3.x 應用程式中使用 UWP 控制項。
- 建立可定義物件的 UWP 應用程式專案 `XamlApplication` 。

您的 WPF 或 Windows Forms 專案必須能夠存取 `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` Windows 社區工具組所提供之類別的實例。 這個物件會作為根中繼資料提供者，以便在應用程式目前目錄的元件中載入自訂 UWP XAML 類型的中繼資料。 建議的做法是將空白應用程式（通用 Windows）專案新增至與 WPF 或 Windows Forms 專案相同的方案，並修訂此專案中的預設應用程式類別。

自訂 UWP XAML 控制項可以包含在此 UWP 應用程式或獨立的 UWP 類別庫專案中，您可以在與 WPF 或 Windows Forms 專案相同的方案中參考該專案。

您可以在下列位置查看詳細的逐步程式描述：

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a>Windows UI 程式庫（WinUI 2）

除了作業系統隨附的收件匣 Windows 10 控制項以外，相同的 UWP XAML 小組也會在 Windows UI 程式庫（**WinUI 2**）中提供其他控制項。 WinUI 2 為 Windows UWP 應用程式提供官方的原生 Microsoft UI 控制項和功能，這些控制項可以在 XAML 島內使用。

WinUI 2 是開放原始碼，您可以在找到資訊 <https://github.com/microsoft/microsoft-ui-xaml> 。

下列文章示範如何從 WinUI 2 程式庫裝載 UWP XAML 控制項：<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

### <a name="do-you-need-xaml-islands"></a>您需要 XAML 群島

XAML 島適用于現有的 Win32 應用程式，想要利用新的 UWP 控制項和行為來改善其使用者體驗，而不需要完整重寫應用程式。 您可以使用 [Windows 10 api](/windows/uwp/porting/desktop-to-uwp-enhance)，但必須等到 XAML Islands 才會使用非 UI 相關的 api。

如果您正在開發新的 Windows 應用程式， [UWP 應用程式](/windows/uwp/get-started/universal-application-platform-guide)   可能是正確的方法。

### <a name="the-road-ahead-xaml-islands-winui-30"></a>更早的 XAML 島： WinUI 3。0

從 Windows 8 開始，Windows UI 平臺（包括 XAML UI 架構、視覺組合圖層和輸入處理）已隨附為 Windows 不可或缺的一部分。 這表示若要受益于最新的 UI 技術改良功能，您必須升級至最新版本的 UI，並在開發應用程式時減緩創新的步調。 為了分離這兩個進化週期並促進創新，Microsoft 正積極處理 WinUI 專案。

從2018開始，Microsoft 已開始將一些新的 XAML UI 控制項和功能當做以 UWP SDK 為基礎的個別 NuGet 套件來傳送。

![WinUI 2.0 的結構](./media/windows-migration/winui2.png)

WinUI 3 正在開發中，將大幅擴充 WinUI 的範圍，以包含完整的 UI 平臺，這會與 UWP SDK 完全分離：

![WinUI 3.0 的結構](./media/windows-migration/winui3.png)

XAML 架構現在會在 GitHub 上開發，並以 [NuGet](/nuget/what-is-nuget)套件的頻外發行   。

隨附于 OS 一部分的現有 UWP XAML Api 將不再收到新的功能更新。 他們仍然會根據 Windows 10 支援週期來接收安全性更新和重大修正程式。

通用 Windows 平臺包含的不只是 XAML 架構（例如，應用程式和安全性模型、媒體管線、Xbox 和 Windows 10 shell 整合、廣泛的裝置支援），而且會繼續進化。 所有新的 XAML 功能只會當做 WinUI 的一部分來開發和傳送。

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a>桌面應用程式中的 WinUI 3 和 WinUI XAML 群島

如您所見，WinUI 3 是 UWP XAML 的演進，它會在 UWP 應用程式模型及其所有需求（MSIX 封裝識別碼、沙箱、CoreWindow 等等）中自然運作。 若只要在 Win32 應用程式模型中使用 WinUI 3，WinUI 內容應該使用**WINUI XAML Islands**由另一個 UI 架構（WINDOWS FORMS、WPF 等等）主控。 如果您想要演變應用程式和混合技術，這是正確的路徑。 不過，如果您想要取代 WinUI 的整個舊 UI，您的應用程式就不應該載入僅裝載 WinUI 的 UI 架構。

WinUI 3 將解決**在桌面應用程式中新增 WinUI 的這項**重要意見反應。 這可讓 Win32 應用程式以獨立 UI 架構的形式使用 WinUI 3;不需要載入 Windows Forms 或 WPF。

在此匯總中，WinUI 3 可讓開發人員輕鬆地混合和比對的正確組合：

* 應用程式模型： UWP、Win32
* 平臺： .NET Core 或原生
* Language： .NET （C \# ，Visual Basic），Standard c + +
* 封裝： MSIX，AppX 用於 Microsoft Store，未封裝
* Interop：使用 WinUI 3 來延伸現有的 WPF、WinForms 和 MFC 應用程式（使用 WinUI XAML Islands）。

如果您想要瞭解更多詳細資料，Microsoft 會在中分享此藍圖 <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> 。

>[!div class="step-by-step"]
>[上一個](migrate-modern-applications.md) 
>[下一步](example-migration-core.md)
