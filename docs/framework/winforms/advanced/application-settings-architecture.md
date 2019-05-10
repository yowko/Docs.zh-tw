---
title: 應用程式設定架構
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: c9cb40cb318bd044cb9204ba2ed384b41b475d57
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625768"
---
# <a name="application-settings-architecture"></a>應用程式設定架構
本主題描述應用程式設定的運作方式，並且瀏覽架構的進階功能 (例如群組設定和設定索引鍵)。  
  
 應用程式設定架構支援以應用程式或使用者範圍定義強型別設定，也支援在應用程式工作階段之間保存設定。 此架構提供預設持續性引擎，可將設定儲存至本機檔案系統和從中載入設定。 此架構也定義介面來提供自訂持續性引擎。  
  
 提供的介面可讓自訂元件裝載於應用程式時，保存自己的設定。 元件可以使用設定索引鍵，區隔多個元件執行個體的設定。  
  
## <a name="defining-settings"></a>定義設定  
 應用程式設定架構同時用於 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 和 Windows Forms，且包含數個在這兩種環境之間共用的基底類別。 最重要的是<xref:System.Configuration.SettingsBase>，其提供存取集合，透過設定，並提供低階方法來載入和儲存設定。 每個環境會實作自己的類別衍生自<xref:System.Configuration.SettingsBase>該環境提供額外的設定功能。 在 Windows Form 為基礎的應用程式，所有的應用程式設定必須定義衍生自的類別上<xref:System.Configuration.ApplicationSettingsBase>類別的基底類別新增下列功能：  
  
- 較高層級的載入和儲存作業  
  
- 支援使用者範圍的設定  
  
- 將使用者的設定還原為預先定義的預設值  
  
- 從舊版應用程式升級設定  
  
- 在設定變更之前或儲存之前驗證設定  
  
 可以使用多個定義內的屬性所設定的描述<xref:System.Configuration>命名空間; 這些所述[應用程式設定屬性](application-settings-attributes.md)。 當您定義一項設定時，您就必須將它套用以<xref:System.Configuration.ApplicationScopedSettingAttribute>或<xref:System.Configuration.UserScopedSettingAttribute>，其中描述此設定套用至整個應用程式，或只用於目前的使用者。  
  
 下列程式碼範例定義具有單一設定的自訂設定類別：`BackgroundColor`。  
  
 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>設定持續性  
 <xref:System.Configuration.ApplicationSettingsBase>類別不會自行保存或載入設定，這項工作由設定提供者類別衍生自<xref:System.Configuration.SettingsProvider>。 如果在衍生類別的<xref:System.Configuration.ApplicationSettingsBase>未指定設定提供者透過<xref:System.Configuration.SettingsProviderAttribute>，則預設的提供者， <xref:System.Configuration.LocalFileSettingsProvider>，會使用。  
  
 最初隨著 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 一起發行的組態系統，支援透過本機電腦的 machine.config 檔案，或在您隨著應用程式部署的 `app.`exe.config 檔案內，提供靜態應用程式組態資料。 <xref:System.Configuration.LocalFileSettingsProvider>類別以下列方式展開此原生支援：  
  
- 應用程式範圍的設定可以儲存在 machine.config 或`app.`exe.config 檔案中。 Machine.config 永遠唯讀，但 `app`.exe.config 基於安全性考量，對大部分應用程式而言限制為唯讀。  
  
- 使用者範圍的設定可以儲存在 `app` exe.config 檔案中，在此情況下視為靜態預設值。  
  
- 非預設使用者範圍的設定儲存在新檔案 *user*config 中，其中 *user* 是目前執行應用程式之人員的使用者名稱。 您可以指定的使用者範圍設定的預設值<xref:System.Configuration.DefaultSettingValueAttribute>。 因為使用者範圍的設定通常會在應用程式執行期間變更，所以 `user`.config 永遠是可讀寫。  
  
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
  
 您可以只有繫結應用程式設定支援的元件<xref:System.Windows.Forms.IBindableComponent>介面。 此外，元件必須實作變更事件的特定繫結屬性，或應用程式設定知道屬性已變更透過<xref:System.ComponentModel.INotifyPropertyChanged>介面。 如果元件未實作<xref:System.Windows.Forms.IBindableComponent>和您要透過 Visual Studio 的繫結、 繫結的屬性會設定第一次，但不是會更新。 如果元件實作<xref:System.Windows.Forms.IBindableComponent>但不是支援屬性變更通知，則繫結將不會更新設定檔中的屬性變更時。  
  
 某些 Windows Form 元件，例如<xref:System.Windows.Forms.ToolStripItem>，不支援設定繫結。  
  
### <a name="settings-serialization"></a>設定序列化  
 當<xref:System.Configuration.LocalFileSettingsProvider>必須將設定儲存至磁碟，它會執行下列動作：  
  
1. 使用反映來檢查的所有屬性上定義您<xref:System.Configuration.ApplicationSettingsBase>衍生類別中，尋找與所套用<xref:System.Configuration.ApplicationScopedSettingAttribute>或<xref:System.Configuration.UserScopedSettingAttribute>。  
  
2. 將屬性序列化至磁碟。 它會先嘗試呼叫<xref:System.ComponentModel.TypeConverter.ConvertToString%2A>或是<xref:System.ComponentModel.TypeConverter.ConvertFromString%2A>上的相關聯的型別<xref:System.ComponentModel.TypeConverter>。 如果不成功，則改用 XML 序列化。  
  
3. 根據設定的屬性，判斷哪些設定在哪些檔案中。  
  
 如果您實作您自己的設定類別，您可以使用<xref:System.Configuration.SettingsSerializeAsAttribute>將設定標示為針對二進位或自訂序列化使用<xref:System.Configuration.SettingsSerializeAs>列舉型別。 如需有關如何在程式碼中建立您自己的設定類別的詳細資訊，請參閱[How to:建立應用程式設定](how-to-create-application-settings.md)。  
  
### <a name="settings-file-locations"></a>設定檔案位置  
 根據應用程式的安裝方式，`app`.exe.config 和 *user*.config 檔案的位置會有所不同。 Windows Forms 應用程式複製到本機電腦，如`app`.exe.config 所在相同的目錄，做為基底目錄的應用程式的主要可執行檔，並*使用者*.config 位於所指定的位置<xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType>屬性。 對於透過 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 安裝的應用程式，這兩個檔案都位於 %InstallRoot%\Documents and Settings\\*username*\Local Settings 下的 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 資料目錄中。  
  
 如果使用者啟用漫遊設定檔，這些檔案的儲存位置會稍微不同，這可讓使用者在使用網域內的其他電腦時，定義不同的 Windows 和應用程式設定。 在此情況下，[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式和 非 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式的 `app`.exe.config 和 *user*.config 檔案，都儲存在 %InstallRoot%\Documents and Settings\\*username*\Application Data 下。  
  
 如需應用程式設定功能如何搭配新的部署技術的詳細資訊，請參閱 [ClickOnce 和應用程式設定](/visualstudio/deployment/clickonce-and-application-settings)。 如需 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]資料目錄的詳細資訊，請參閱[在 ClickOnce 應用程式中存取本機和遠端資料](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)。  
  
## <a name="application-settings-and-security"></a>應用程式設定和安全性  
 應用程式設定設計為在部分信任情況下運作，這是裝載於網際網路或內部網路上的 Windows Forms 應用程式預設的受限制環境。 使用應用程式設定搭配預設的設定提供者時，不需要任何超過部分信任的特殊權限。  
  
 在 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式中使用應用程式設定時，`user`.config 檔案儲存在 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 資料目錄中。 應用程式的 `user`.config 檔案大小不能超過 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 設定的資料目錄配額。 如需詳細資訊，請參閱 [ClickOnce 和應用程式設定](/visualstudio/deployment/clickonce-and-application-settings)。  
  
## <a name="custom-settings-providers"></a>自訂設定提供者  
 在應用程式設定架構中，為應用程式設定之間的鬆散結合的包裝函式類別衍生自<xref:System.Configuration.ApplicationSettingsBase>，以及相關聯的設定提供者或提供者，衍生自<xref:System.Configuration.SettingsProvider>。 此關聯會定義只由<xref:System.Configuration.SettingsProviderAttribute>套用至包裝函式類別或其個別的屬性。 如果的設定，提供者未明確指定，預設的提供者， <xref:System.Configuration.LocalFileSettingsProvider>，會使用。 因此，此架構支援建立和使用自訂設定提供者。  
  
 例如，假設您想要開發及使用 `SqlSettingsProvider`，此提供者會將所有設定資料儲存在 Microsoft SQL Server 資料庫中。 您<xref:System.Configuration.SettingsProvider>-在衍生的類別會收到這項資訊在其`Initialize`方法做為參數的型別<xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>。 您會實作<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A>方法，以從資料存放區中，擷取您的設定和<xref:System.Configuration.SettingsProvider.SetPropertyValues%2A>以加以儲存。 您的提供者可以使用<xref:System.Configuration.SettingsPropertyCollection>提供給<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A>若要判斷屬性的名稱、 類型和範圍，以及任何其他設定的屬性會定義該屬性。  
  
 您的提供者必須實作一個屬性和一個方法，其實作可能不明顯。 <xref:System.Configuration.SettingsProvider.ApplicationName%2A>屬性是抽象屬性<xref:System.Configuration.SettingsProvider>; 您應設計程式，它會傳回下列：  
  
 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 您的衍生類別也必須實作 `Initialize` 方法，不接受任何引數，也不傳回任何值。 這個方法不由定義<xref:System.Configuration.SettingsProvider>。  
  
 最後，您實作<xref:System.Configuration.IApplicationSettingsProvider>上您的提供者提供支援重新整理設定，將設定還原為其預設值，並從一個應用程式的版本升級設定。  
  
 實作並編譯您的提供者之後，您必須指示設定類別使用此提供者來代替預設值。 完成這項工作<xref:System.Configuration.SettingsProviderAttribute>。 如果套用至整個設定類別，提供者用於每個類別定義的設定如果套用至個別的設定，應用程式設定架構的這些設定，請使用該提供者，並使用<xref:System.Configuration.LocalFileSettingsProvider>其餘部分。 下列程式碼範例示範如何指示設定類別來使用您的自訂提供者。  
  
 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 一個提供者可供多個執行緒同時呼叫，但永遠寫入相同的儲存位置。因此，應用程式設定架構只會具現化提供者類別的單一執行個體。  
  
> [!IMPORTANT]
>  您應該確定您的提供者是安全執行緒，而且一次只允許一個執行緒寫入組態檔。  
  
 您的提供者不需要支援所有的屬性中定義的設定<xref:System.Configuration?displayProperty=nameWithType>命名空間，但它必須在最小支援<xref:System.Configuration.ApplicationScopedSettingAttribute>並<xref:System.Configuration.UserScopedSettingAttribute>，也應該支援和<xref:System.Configuration.DefaultSettingValueAttribute>。 對於不支援的屬性，您的提供者應該失敗且不需要通知，也就是不應該擲回例外狀況。 如果設定類別使用無效的屬性組合，但是 — 例如套用<xref:System.Configuration.ApplicationScopedSettingAttribute>和<xref:System.Configuration.UserScopedSettingAttribute>相同的設定 — 您的提供者應該擲回例外狀況，並停止作業。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [應用程式設定概觀](application-settings-overview.md)
- [Application Settings for Custom Controls](application-settings-for-custom-controls.md)
- [ClickOnce 和應用程式設定](/visualstudio/deployment/clickonce-and-application-settings)
- [應用程式設定結構描述](../../configure-apps/file-schema/application-settings-schema.md)
