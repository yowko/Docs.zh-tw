---
title: 應用程式設定架構
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: 078b5f3fc1cd4273af282580f41e68ca9bd8ff51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182618"
---
# <a name="application-settings-architecture"></a>應用程式設定架構
本主題描述應用程式設定的運作方式，並且瀏覽架構的進階功能 (例如群組設定和設定索引鍵)。

 應用程式設定架構支援以應用程式或使用者範圍定義強型別設定，也支援在應用程式工作階段之間保存設定。 此架構提供預設持續性引擎，可將設定儲存至本機檔案系統和從中載入設定。 此架構也定義介面來提供自訂持續性引擎。

 提供的介面可讓自訂元件裝載於應用程式時，保存自己的設定。 元件可以使用設定索引鍵，區隔多個元件執行個體的設定。

## <a name="defining-settings"></a>定義設定
 應用程式設定體系結構在ASP.NET表單和 Windows 表單中使用，它包含許多在這兩個環境中共用的基類。 最重要的是<xref:System.Configuration.SettingsBase>，它通過集合提供對設置的訪問，並提供用於載入和保存設置的低級方法。 每個環境實現其派生自己的類<xref:System.Configuration.SettingsBase>，以便為該環境提供其他設置功能。 在基於 Windows 表單的應用程式中，必須在派生自類的<xref:System.Configuration.ApplicationSettingsBase>類上定義所有應用程式設定，這將以下功能添加到基類：

- 較高層級的載入和儲存作業

- 支援使用者範圍的設定

- 將使用者的設定還原為預先定義的預設值

- 從舊版應用程式升級設定

- 在設定變更之前或儲存之前驗證設定

 可以使用命名空間中<xref:System.Configuration>定義的許多屬性來描述這些設置;這些在[應用程式設定屬性](application-settings-attributes.md)中描述。 定義設置時，必須將其應用於 或<xref:System.Configuration.ApplicationScopedSettingAttribute><xref:System.Configuration.UserScopedSettingAttribute>，其中描述該設置是應用於整個應用程式還是僅適用于當前使用者。

 下列程式碼範例定義具有單一設定的自訂設定類別：`BackgroundColor`。

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>設定持續性
 類<xref:System.Configuration.ApplicationSettingsBase>本身不保留或載入設置;否則，該類將不保留或載入設置。此作業屬於設置提供程式，該類派生自<xref:System.Configuration.SettingsProvider>。 如果 派生<xref:System.Configuration.ApplicationSettingsBase>類未通過 指定 設置提供程式<xref:System.Configuration.SettingsProviderAttribute>，則使用預設提供程式 。。 <xref:System.Configuration.LocalFileSettingsProvider>

 最初使用 .NET Framework 發佈的配置系統支援通過本地電腦的機器.config 檔或隨應用程式一起部署的`app.`exe.config 檔中提供靜態應用程式佈建資料。 類<xref:System.Configuration.LocalFileSettingsProvider>以以下方式擴展此本機支援：

- 應用程式範圍的設定可以儲存在 machine.config 或`app.`exe.config 檔案中。 Machine.config 永遠唯讀，但 `app`.exe.config 基於安全性考量，對大部分應用程式而言限制為唯讀。

- 使用者範圍的設定可以儲存在 `app` exe.config 檔案中，在此情況下視為靜態預設值。

- 非預設使用者範圍的設定儲存在新檔案 *user*config 中，其中 *user* 是目前執行應用程式之人員的使用者名稱。 可以為 具有<xref:System.Configuration.DefaultSettingValueAttribute>的使用者範圍設置指定預設值。 因為使用者範圍的設定通常會在應用程式執行期間變更，所以 `user`.config 永遠是可讀寫。

 這三個組態檔全部以 XML 格式儲存設定。 應用程式範圍設定的最上層 XML 元素是 `<appSettings>`，而 `<userSettings>` 用於使用者範圍的設定。 含有應用程式範圍的設定及使用者範圍設定預設值的 `app`.exe.config 檔案如下︰

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
        </sectionGroup>
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
        </sectionGroup>
    </configSections>
    <applicationSettings>
        <WindowsApplication1.Properties.Settings>
            <setting name="Cursor" serializeAs="String">
                <value>Default</value>
            </setting>
            <setting name="DoubleBuffering" serializeAs="String">
                <value>False</value>
            </setting>
        </WindowsApplication1.Properties.Settings>
    </applicationSettings>
    <userSettings>
        <WindowsApplication1.Properties.Settings>
            <setting name="FormTitle" serializeAs="String">
                <value>Form1</value>
            </setting>
            <setting name="FormSize" serializeAs="String">
                <value>595, 536</value>
            </setting>
        </WindowsApplication1.Properties.Settings>
    </userSettings>
</configuration>
```

 如需組態檔的應用程式設定區段中的元素定義，請參閱[應用程式設定結構描述](../../configure-apps/file-schema/application-settings-schema.md)。

### <a name="settings-bindings"></a>設定繫結關係
 應用程式設定使用 Windows Forms 資料繫結架構，提供設定物件和元件之間設定更新的雙向通訊。 如果您使用 Visual Studio 建立應用程式設定，並將它們指派給元件的屬性，則會自動產生這些繫結關係。

 只能將應用程式設定綁定到支援介面的<xref:System.Windows.Forms.IBindableComponent>元件。 此外，元件必須為特定的綁定屬性實現變更事件，或者通知應用程式設定該屬性已通過<xref:System.ComponentModel.INotifyPropertyChanged>介面更改。 如果元件未實現<xref:System.Windows.Forms.IBindableComponent>，並且您正在通過 Visual Studio 綁定，則綁定屬性將在第一次設置，但不會更新。 如果元件實現<xref:System.Windows.Forms.IBindableComponent>但不支援屬性更改通知，則當更改屬性時，綁定將不會在設置檔中更新。

 某些 Windows 表單元件（<xref:System.Windows.Forms.ToolStripItem>如 ）不支援設置綁定。

### <a name="settings-serialization"></a>設定序列化
 當<xref:System.Configuration.LocalFileSettingsProvider>必須將設置保存到磁片時，它將執行以下操作：

1. 使用反射檢查<xref:System.Configuration.ApplicationSettingsBase>派生類上定義的所有屬性，查找使用 或<xref:System.Configuration.ApplicationScopedSettingAttribute><xref:System.Configuration.UserScopedSettingAttribute>應用的屬性。

2. 將屬性序列化至磁碟。 它首先嘗試調用<xref:System.ComponentModel.TypeConverter.ConvertToString%2A>或<xref:System.ComponentModel.TypeConverter.ConvertFromString%2A>上的關聯<xref:System.ComponentModel.TypeConverter>。 如果不成功，則改用 XML 序列化。

3. 根據設定的屬性，判斷哪些設定在哪些檔案中。

 如果實現自己的設置類，則可以使用<xref:System.Configuration.SettingsSerializeAsAttribute>標記二進位或自訂序列化設置。 <xref:System.Configuration.SettingsSerializeAs> 如需有關如何在程式碼中建立您自己的設定類別的詳細資訊，請參閱[如何︰建立應用程式設定](how-to-create-application-settings.md)。

### <a name="settings-file-locations"></a>設定檔案位置
 根據應用程式的安裝方式，`app`.exe.config 和 *user*.config 檔案的位置會有所不同。 對於複製到本地電腦上的基於 Windows 表單的應用程式，.exe.config`app`將駐留在與應用程式主可執行檔的基礎目錄相同的目錄中，*並且使用者*.config 將駐留在<xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType>屬性指定的位置。 對於通過 ClickOnce 安裝的應用程式，這兩個檔將駐留在 %InstallRoot%_文檔和設置\\*使用者名*[本地設置）下方的 ClickOnce 資料目錄中。

 如果使用者啟用了漫遊設定檔，這些檔的存儲位置略有不同，這使使用者能夠在域中使用其他電腦時定義不同的 Windows 和應用程式設定。 在這種情況下，ClickOnce 應用程式和非 ClickOnce 應用程式都將`app`將其 .exe.config 和*user*.config 檔存儲在 %InstallRoot%_文檔\\和設置*使用者名*[應用程式資料下。

 如需應用程式設定功能如何搭配新的部署技術的詳細資訊，請參閱 [ClickOnce 和應用程式設定](/visualstudio/deployment/clickonce-and-application-settings)。 有關 ClickOnce 資料目錄的詳細資訊，請參閱[在 ClickOnce 應用程式中訪問本地和遠端資料](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)。

## <a name="application-settings-and-security"></a>應用程式設定和安全性
 應用程式設定設計為在部分信任情況下運作，這是裝載於網際網路或內部網路上的 Windows Forms 應用程式預設的受限制環境。 使用應用程式設定搭配預設的設定提供者時，不需要任何超過部分信任的特殊權限。

 在 ClickOnce 應用程式中使用應用程式設定時`user`，.config 檔存儲在 ClickOnce 資料目錄中。 應用程式的`user`.config 檔的大小不能超過 ClickOnce 設置的資料目錄配額。 如需詳細資訊，請參閱 [ClickOnce 和應用程式設定](/visualstudio/deployment/clickonce-and-application-settings)。

## <a name="custom-settings-providers"></a>自訂設定提供者
 在應用程式設定體系結構中，應用程式設定包裝類（派生自<xref:System.Configuration.ApplicationSettingsBase>） 與派生自<xref:System.Configuration.SettingsProvider>的關聯設置提供程式或提供程式之間存在鬆散耦合。 此關聯僅由<xref:System.Configuration.SettingsProviderAttribute>應用於包裝類或其單個屬性定義。 如果未顯式指定設置提供程式，則使用預設提供程式 ， <xref:System.Configuration.LocalFileSettingsProvider>。 因此，此架構支援建立和使用自訂設定提供者。

 例如，假設您想要開發及使用 `SqlSettingsProvider`，此提供者會將所有設定資料儲存在 Microsoft SQL Server 資料庫中。 派生<xref:System.Configuration.SettingsProvider>類將在其`Initialize`方法中作為類型的<xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>參數接收此資訊。 然後，您將實現從<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A>資料存儲中檢索設置並<xref:System.Configuration.SettingsProvider.SetPropertyValues%2A>保存它們的方法。 提供程式可以使用<xref:System.Configuration.SettingsPropertyCollection>提供的<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A>來確定屬性的名稱、類型和範圍，以及為該屬性定義的任何其他設置屬性。

 您的提供者必須實作一個屬性和一個方法，其實作可能不明顯。 屬性<xref:System.Configuration.SettingsProvider.ApplicationName%2A>是<xref:System.Configuration.SettingsProvider>中的抽象屬性。您應該對它進行程式設計以返回以下內容：

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 您的衍生類別也必須實作 `Initialize` 方法，不接受任何引數，也不傳回任何值。 此方法不由 定義<xref:System.Configuration.SettingsProvider>。

 最後，在提供程式<xref:System.Configuration.IApplicationSettingsProvider>上實現支援刷新設置、將設置還原到其預設值以及將設置從一個應用程式版本升級到另一個應用程式版本。

 實作並編譯您的提供者之後，您必須指示設定類別使用此提供者來代替預設值。 通過 來完成此目的<xref:System.Configuration.SettingsProviderAttribute>。 如果應用於整個設置類，則提供程式用於類定義的每個設置;如果將提供程式應用於該類定義的每個設置。如果應用於單個設置，則應用程式設定體系結構僅對這些設置使用該提供程式，並為其餘<xref:System.Configuration.LocalFileSettingsProvider>設置使用。 下列程式碼範例示範如何指示設定類別來使用您的自訂提供者。

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 一個提供者可供多個執行緒同時呼叫，但永遠寫入相同的儲存位置。因此，應用程式設定架構只會具現化提供者類別的單一執行個體。

> [!IMPORTANT]
> 您應該確定您的提供者是安全執行緒，而且一次只允許一個執行緒寫入組態檔。

 提供程式不需要<xref:System.Configuration?displayProperty=nameWithType>支援命名空間中定義的所有設置屬性，儘管它必須至少<xref:System.Configuration.ApplicationScopedSettingAttribute>支援 和<xref:System.Configuration.UserScopedSettingAttribute>，並且還應支援<xref:System.Configuration.DefaultSettingValueAttribute>。 對於不支援的屬性，您的提供者應該失敗且不需要通知，也就是不應該擲回例外狀況。 但是，如果設置類使用不正確屬性組合（例如應用<xref:System.Configuration.ApplicationScopedSettingAttribute>和<xref:System.Configuration.UserScopedSettingAttribute>到同一設置），則提供程式應引發異常並停止操作。

## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [應用程式設定概述](application-settings-overview.md)
- [自訂控制項的應用程式設定](application-settings-for-custom-controls.md)
- [按一下"設置"和"應用程式設定"](/visualstudio/deployment/clickonce-and-application-settings)
- [應用程式設定結構描述](../../configure-apps/file-schema/application-settings-schema.md)
