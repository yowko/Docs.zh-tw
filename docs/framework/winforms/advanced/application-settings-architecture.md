---
title: 應用程式設定架構
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: c3858cfab59b63761f43f6b3eaad9bf8ca4c1dbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916699"
---
# <a name="application-settings-architecture"></a>應用程式設定架構
本主題描述應用程式設定的運作方式，並且瀏覽架構的進階功能 (例如群組設定和設定索引鍵)。

 應用程式設定架構支援以應用程式或使用者範圍定義強型別設定，也支援在應用程式工作階段之間保存設定。 此架構提供預設持續性引擎，可將設定儲存至本機檔案系統和從中載入設定。 此架構也定義介面來提供自訂持續性引擎。

 提供的介面可讓自訂元件裝載於應用程式時，保存自己的設定。 元件可以使用設定索引鍵，區隔多個元件執行個體的設定。

## <a name="defining-settings"></a>定義設定
 應用程式設定架構會同時用於 ASP.NET 和 Windows Forms 中, 而且包含許多在這兩個環境之間共用的基類。 最重要的是<xref:System.Configuration.SettingsBase>, 它會透過集合提供設定的存取權, 並提供用於載入和儲存設定的低層級方法。 每個環境都會執行自己的衍生<xref:System.Configuration.SettingsBase>自的類別, 以提供該環境的其他設定功能。 在以 Windows Forms 為基礎的應用程式中, 所有應用程式設定都必須在衍生自<xref:System.Configuration.ApplicationSettingsBase>類別的類別上定義, 這會在基類中新增下列功能:

- 較高層級的載入和儲存作業

- 支援使用者範圍的設定

- 將使用者的設定還原為預先定義的預設值

- 從舊版應用程式升級設定

- 在設定變更之前或儲存之前驗證設定

 這些設定可以使用<xref:System.Configuration>命名空間中定義的多個屬性來描述, 這些都是在[應用程式設定屬性](application-settings-attributes.md)中說明。 當您定義設定時, 您必須將它套用至<xref:System.Configuration.ApplicationScopedSettingAttribute>或<xref:System.Configuration.UserScopedSettingAttribute>, 這會描述設定是否適用于整個應用程式, 或僅套用至目前的使用者。

 下列程式碼範例定義具有單一設定的自訂設定類別：`BackgroundColor`。

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>設定持續性
 類別本身不會保存或載入設定; 此作業會落在設定提供者 (衍生自<xref:System.Configuration.SettingsProvider>的類別)。 <xref:System.Configuration.ApplicationSettingsBase> 如果的衍生類別<xref:System.Configuration.ApplicationSettingsBase>未<xref:System.Configuration.SettingsProviderAttribute>透過指定設定提供者, 則會使用預設提供者<xref:System.Configuration.LocalFileSettingsProvider>。

 原先與 .NET Framework 一起發行的設定系統, 支援透過本機電腦的 machine.config 檔案或`app.`您用來部署的 exe 檔案, 提供靜態應用程式設定資料。您的應用程式。 <xref:System.Configuration.LocalFileSettingsProvider>類別會以下列方式擴充這個原生支援:

- 應用程式範圍的設定可以儲存在 machine.config 或`app.`exe.config 檔案中。 Machine.config 永遠唯讀，但 `app`.exe.config 基於安全性考量，對大部分應用程式而言限制為唯讀。

- 使用者範圍的設定可以儲存在 `app` exe.config 檔案中，在此情況下視為靜態預設值。

- 非預設使用者範圍的設定儲存在新檔案 *user*config 中，其中 *user* 是目前執行應用程式之人員的使用者名稱。 您可以使用<xref:System.Configuration.DefaultSettingValueAttribute>指定使用者範圍設定的預設值。 因為使用者範圍的設定通常會在應用程式執行期間變更，所以 `user`.config 永遠是可讀寫。

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

 您只能將應用程式設定系結至支援<xref:System.Windows.Forms.IBindableComponent>介面的元件。 此外, 元件必須針對特定的系結屬性執行變更事件, 或通知應用程式設定屬性已透過<xref:System.ComponentModel.INotifyPropertyChanged>介面變更。 如果元件未執行<xref:System.Windows.Forms.IBindableComponent> , 而且您是透過 Visual Studio 進行系結, 則會第一次設定系結的屬性, 但不會更新。 如果元件<xref:System.Windows.Forms.IBindableComponent>會執行, 但不支援屬性變更通知, 則當屬性變更時, 系結將不會在設定檔中更新。

 某些 Windows Forms 元件 (例如<xref:System.Windows.Forms.ToolStripItem>) 不支援設定系結。

### <a name="settings-serialization"></a>設定序列化
 當<xref:System.Configuration.LocalFileSettingsProvider>必須將設定儲存到磁片時, 它會執行下列動作:

1. 會<xref:System.Configuration.ApplicationSettingsBase> 使用反映來檢查<xref:System.Configuration.UserScopedSettingAttribute>在衍生類別上定義的所有屬性, 並尋找套用或的屬性。<xref:System.Configuration.ApplicationScopedSettingAttribute>

2. 將屬性序列化至磁碟。 它會先嘗試呼叫<xref:System.ComponentModel.TypeConverter.ConvertToString%2A>或<xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> (在相關聯<xref:System.ComponentModel.TypeConverter>的類型上)。 如果不成功，則改用 XML 序列化。

3. 根據設定的屬性，判斷哪些設定在哪些檔案中。

 如果您執行自己的設定類別, 您可以使用<xref:System.Configuration.SettingsSerializeAsAttribute>來標示二進位或自訂序列化的設定, 方法是<xref:System.Configuration.SettingsSerializeAs>使用列舉。 如需有關如何在程式碼中建立您自己的設定[類別的詳細資訊, 請參閱如何:建立應用程式](how-to-create-application-settings.md)設定。

### <a name="settings-file-locations"></a>設定檔案位置
 根據應用程式的安裝方式，`app`.exe.config 和 *user*.config 檔案的位置會有所不同。 若為複製到本機電腦上的 Windows Forms 型應用程式`app`, .exe .config 將位於與應用程式主要可執行檔的基底目錄相同的目錄中, 而*user*.config 則位於所指定的位置。<xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType>屬性。 對於透過 ClickOnce 安裝的應用程式, 這兩個檔案都位於 [%installroot%\documents and settings] 和 [設定\\] [使用者*名稱*] \Local 設定底下的 ClickOnce 資料目錄中。

 如果使用者啟用漫遊設定檔，這些檔案的儲存位置會稍微不同，這可讓使用者在使用網域內的其他電腦時，定義不同的 Windows 和應用程式設定。 在這種情況下, ClickOnce 應用程式和非 ClickOnce 應用程式會`app`將其 .exe 和 app.config 檔案儲存在%installroot%\documents and settings 和設定\\*使用者* *名稱*\Application 資料之下。

 如需應用程式設定功能如何搭配新的部署技術的詳細資訊，請參閱 [ClickOnce 和應用程式設定](/visualstudio/deployment/clickonce-and-application-settings)。 如需 ClickOnce 資料目錄的詳細資訊, 請參閱[在 Clickonce 應用程式中存取本機和遠端資料](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)。

## <a name="application-settings-and-security"></a>應用程式設定和安全性
 應用程式設定設計為在部分信任情況下運作，這是裝載於網際網路或內部網路上的 Windows Forms 應用程式預設的受限制環境。 使用應用程式設定搭配預設的設定提供者時，不需要任何超過部分信任的特殊權限。

 在 clickonce 應用程式中使用應用程式設定時, `user`.config 檔案會儲存在 clickonce 資料目錄中。 應用程式的`user`.config 檔案大小不能超過 ClickOnce 所設定的資料目錄配額。 如需詳細資訊，請參閱 [ClickOnce 和應用程式設定](/visualstudio/deployment/clickonce-and-application-settings)。

## <a name="custom-settings-providers"></a>自訂設定提供者
 在應用程式設定架構中, 應用程式設定包裝函式類別 (衍生自<xref:System.Configuration.ApplicationSettingsBase>) 與相關聯的設定提供者或提供者 (衍生自<xref:System.Configuration.SettingsProvider>) 之間會有鬆散的結合。 只有套用至包裝函式類別<xref:System.Configuration.SettingsProviderAttribute>或其個別屬性的才會定義此關聯。 如果未明確指定設定提供者, 則會使用預設提供<xref:System.Configuration.LocalFileSettingsProvider>者。 因此，此架構支援建立和使用自訂設定提供者。

 例如，假設您想要開發及使用 `SqlSettingsProvider`，此提供者會將所有設定資料儲存在 Microsoft SQL Server 資料庫中。 衍生的類別會以類型<xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>的參數形式, `Initialize`在其方法中接收這項資訊。 <xref:System.Configuration.SettingsProvider> 接著, 您會執行<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A>方法, 從資料存放區抓取您的設定, <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A>並加以儲存。 您的提供者可以<xref:System.Configuration.SettingsPropertyCollection>使用提供<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A>的來判斷屬性的名稱、類型和範圍, 以及為該屬性定義的任何其他設定屬性。

 您的提供者必須實作一個屬性和一個方法，其實作可能不明顯。 屬性是的<xref:System.Configuration.SettingsProvider>抽象屬性, 您應該將它程式設計成傳回下列內容: <xref:System.Configuration.SettingsProvider.ApplicationName%2A>

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 您的衍生類別也必須實作 `Initialize` 方法，不接受任何引數，也不傳回任何值。 這個方法不是由<xref:System.Configuration.SettingsProvider>所定義。

 最後, 您會<xref:System.Configuration.IApplicationSettingsProvider>在您的提供者上執行, 以提供重新整理設定、將設定還原為預設值, 以及將設定從一個應用程式版本升級到另一個的支援。

 實作並編譯您的提供者之後，您必須指示設定類別使用此提供者來代替預設值。 您可以透過<xref:System.Configuration.SettingsProviderAttribute>完成此動作。 如果套用至整個設定類別, 則會針對類別所定義的每個設定使用提供者;如果套用至個別設定, 應用程式設定架構只會針對那些設定使用該提供者<xref:System.Configuration.LocalFileSettingsProvider> , 並針對其餘的使用。 下列程式碼範例示範如何指示設定類別來使用您的自訂提供者。

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 一個提供者可供多個執行緒同時呼叫，但永遠寫入相同的儲存位置。因此，應用程式設定架構只會具現化提供者類別的單一執行個體。

> [!IMPORTANT]
> 您應該確定您的提供者是安全執行緒，而且一次只允許一個執行緒寫入組態檔。

 您的提供者<xref:System.Configuration?displayProperty=nameWithType>不需要支援命名空間中定義的所有設定屬性, 但至少<xref:System.Configuration.ApplicationScopedSettingAttribute>必須支援和<xref:System.Configuration.UserScopedSettingAttribute>, 而且也應該支援<xref:System.Configuration.DefaultSettingValueAttribute>。 對於不支援的屬性，您的提供者應該失敗且不需要通知，也就是不應該擲回例外狀況。 不過, 如果 settings 類別使用不正確屬性組合 (例如<xref:System.Configuration.ApplicationScopedSettingAttribute> , 將和<xref:System.Configuration.UserScopedSettingAttribute>套用至相同的設定), 您的提供者應該會擲回例外狀況並停止作業。

## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [應用程式設定概觀](application-settings-overview.md)
- [Application Settings for Custom Controls](application-settings-for-custom-controls.md)
- [ClickOnce 和應用程式設定](/visualstudio/deployment/clickonce-and-application-settings)
- [應用程式設定結構描述](../../configure-apps/file-schema/application-settings-schema.md)
