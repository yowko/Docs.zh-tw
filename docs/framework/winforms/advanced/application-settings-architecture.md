---
title: "應用程式設定架構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "應用程式設定 [Windows Form], 架構"
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# 應用程式設定架構
這個主題描述應用程式設定 \(Application Setting\) 架構的運作方式，並且瀏覽架構的進階功能 \(例如已群組的設定和設定索引鍵\)。  
  
 應用程式設定架構支援以應用程式範圍或使用者範圍定義強型別 \(Strongly Typed\) 的設定，並且可以在兩個應用程式工作階段 \(Session\) 之間保存 \(Persist\) 設定。  架構提供了預設的保存引擎，可以將設定儲存至本機檔案系統或從此處載入設定。  架構也定義了用來提供自訂保存引擎的介面。  
  
 提供了介面後，當您在應用程式中裝載自訂元件時，此元件便能保存其本身的設定。  藉由使用設定索引鍵，元件可以將多個執行個體的設定各自保持獨立。  
  
## 定義設定  
 應用程式設定架構可以在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 和 Windows Form 中使用，它包含一些可跨越這兩種環境共用的基底類別。  其中最重要的是 <xref:System.Configuration.SettingsBase>，它可用來存取某一集合中所有設定，而且還提供載入和儲存設定的低階方法。  每一個環境都會各自實作衍生自 <xref:System.Configuration.SettingsBase> 的類別，藉此提供該環境中的其他設定功能。  在 Windows Form 架構的應用程式中，所有應用程式設定都必須在衍生自 <xref:System.Configuration.ApplicationSettingsBase> 類別的類別上定義，此舉會將下列功能加入基底類別：  
  
-   較高層級的載入和儲存作業  
  
-   使用者範圍設定的支援  
  
-   將使用者的設定轉換為預先定義的預設值  
  
-   升級來自舊版應用程式的設定  
  
-   在變更或儲存設定之前先進行驗證  
  
 設定可藉由使用一些在 <xref:System.Configuration> 命名空間內定義的屬性來描述；這些屬性在[應用程式設定屬性](../../../../docs/framework/winforms/advanced/application-settings-attributes.md)中有詳細說明。  定義設定時，您必須將設定套用 <xref:System.Configuration.ApplicationScopedSettingAttribute> 或 <xref:System.Configuration.UserScopedSettingAttribute>，藉此描述該設定是適用於整個應用程式或僅適用於目前的使用者。  
  
 下列程式碼範例以單一設定  `BackgroundColor` 來定義自訂設定。  
  
 [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## 設定的保存  
 <xref:System.Configuration.ApplicationSettingsBase> 類別本身並不會保存或載入設定，這項工作必須由設定提供者 \(即衍生自 <xref:System.Configuration.SettingsProvider> 的類別\) 完成。  如果 <xref:System.Configuration.ApplicationSettingsBase> 的衍生類別 \(Derived Class\) 尚未利用 <xref:System.Configuration.SettingsProviderAttribute> 來指定設定提供者，那麼將會使用預設提供者 <xref:System.Configuration.LocalFileSettingsProvider>。  
  
 原本與 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 發行的組態系統支援透過本機電腦的 machine.config 檔來提供靜態應用程式組態資料，或是在與應用程式一起部署的 `app.`exe.config 檔內提供該資料。  <xref:System.Configuration.LocalFileSettingsProvider> 類別可利用下列方法來擴充原生支援：  
  
-   應用程式範圍的設定可儲存於 machine.config 或 `app.`exe.config 檔案。  Machine.config 永遠是唯讀的，而 `app`.exe.config 則是基於安全性考量在大部分應用程式中都限制成唯讀狀態。  
  
-   使用者範圍的設定可儲存於 `app`.exe.config 檔案中，這裡的設定都被視為靜態預設值。  
  
-   非預設的使用者範圍設定儲存於新的 *user*.config 檔案中，其中的 *user* 就是目前正在執行應用程式之人員的使用者名稱。  您可以使用 <xref:System.Configuration.DefaultSettingValueAttribute> 來指定使用者範圍設定的預設值。  由於在應用程式執行期間使用者範圍的設定經常變更，因此 `user`.config 永遠可以讀取\/寫入。  
  
 三個組態檔全部都是以 XML 格式儲存設定。  應用程式範圍設定的最上層 XML 項目為 `<appSettings>`，而 `<userSettings>` 則是用於使用者範圍設定。  同時包含應用程式範圍設定以及使用者範圍設定預設值的 `app`.exe.config 檔案可能如以下所示：  
  
```  
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
  
 如需組態檔中應用程式設定區段內各個項目的定義，請參閱[應用程式設定結構描述](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)。  
  
### 設定的繫結  
 應用程式設定會使用 Windows Form 的資料繫結 \(Data Binding\) 架構，為設定物件與元件之間的設定更新提供雙向通訊。  如果使用 Visual Studio 建立應用程式設定並將設定指派給元件屬性，就會自動產生這些繫結。  
  
 您只能將應用程式設定繫結至支援 <xref:System.Windows.Forms.IBindableComponent> 介面的元件。  此外，元件必須針對特定的繫結屬性實作變更事件，或是透過 <xref:System.ComponentModel.INotifyPropertyChanged> 介面通知應用程式設定屬性已變更。  如果元件未實作 <xref:System.Windows.Forms.IBindableComponent>，而且您是透過 Visual Studio 進行繫結，這時將會第一次設定繫結屬性，但是不會更新。  如果元件實作 <xref:System.Windows.Forms.IBindableComponent>，但是不支援屬性變更通知，則當屬性變更時，設定檔中的繫結將不會更新。  
  
 有些 Windows Form 元件不支援設定的繫結，例如 <xref:System.Windows.Forms.ToolStripItem>。  
  
### 設定的序列化  
 當 <xref:System.Configuration.LocalFileSettingsProvider> 必須將設定儲存於磁碟時，它會執行下列動作：  
  
1.  使用反映 \(Reflection\) 檢查在 <xref:System.Configuration.ApplicationSettingsBase> 衍生類別上定義的所有屬性，以找出套用 <xref:System.Configuration.ApplicationScopedSettingAttribute> 或 <xref:System.Configuration.UserScopedSettingAttribute> 的屬性。  
  
2.  將屬性序列化至磁碟。  它會先嘗試在型別的關聯 <xref:System.ComponentModel.TypeConverter> 上呼叫 <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> 或 <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A>。  如果不成功，它將改用 XML 序列化。  
  
3.  根據設定的屬性，判斷設定是在哪個檔案中。  
  
 如果您要實作自己的設定類別，可以使用 <xref:System.Configuration.SettingsSerializeAsAttribute>，針對使用 <xref:System.Configuration.SettingsSerializeAs> 列舉型別的二進位或自訂序列化 \(Serialization\) 來標記設定。  如需在程式碼中建立自己的設定類別的詳細資訊，請參閱 [如何：建立應用程式設定](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)。  
  
### 設定檔位置  
 `app`.exe.config 和 *user*.config 檔案的位置，將會視應用程式的安裝方式而有所不同。  對於複製到本機電腦上的 Windows Form 架構的應用程式而言，`app`.exe.config 會位於做為應用程式主執行檔之基底目錄的相同目錄內，*user*.config 則會位於 <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=fullName> 屬性所指定的位置內。  對於以 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 方式安裝的應用程式，這兩個檔案都是位於 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 資料目錄中，該目錄則是在 %InstallRoot%\\Documents and Settings\\*username*\\Local Settings 底下。  
  
 如果使用者啟用了漫遊設定檔，則這些檔案的儲存位置將稍有不同。此設定檔可讓使用者即使是使用網域內的其他電腦，也能定義不同的 Windows 設定和應用程式設定。  在這種情況下，[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式和非 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式都會將它們的 `app`.exe.config 和 *user*.config 檔案儲存在 %InstallRoot%\\Documents and Settings\\*username*\\Application Data 底下。  
  
 如需應用程式設定功能如何與新部署技術搭配使用的詳細資訊，請參閱 [ClickOnce 和應用程式設定](../Topic/ClickOnce%20and%20Application%20Settings.md)。  如需 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 資料目錄的詳細資訊，請參閱[在 ClickOnce 應用程式中存取本機和遠端資料](../Topic/Accessing%20Local%20and%20Remote%20Data%20in%20ClickOnce%20Applications.md)。  
  
## 應用程式設定和安全性  
 應用程式設定是設計為在部分信任的環境中運作，此即裝載於網際網路或內部網路之 Windows Form 應用程式的預設受限環境。  除了部分信任以外，不需其他特殊權限即可利用預設的設定提供者來使用應用程式設定。  
  
 如果是在 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式中使用應用程式設定，`user`.config 檔將會儲存在 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 資料目錄中。  應用程式的 `user`.config 檔案大小不得超過 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 所設定的資料目錄配額。  如需詳細資訊，請參閱 [ClickOnce 和應用程式設定](../Topic/ClickOnce%20and%20Application%20Settings.md)。  
  
## 自訂設定提供者  
 在應用程式設定架構中，在衍生自 <xref:System.Configuration.ApplicationSettingsBase> 的應用程式設定包裝函式類別 \(Wrapper Class\) 與衍生自 <xref:System.Configuration.SettingsProvider> 的相關設定提供者之間存在著鬆散的連結。  此關聯性只能由套用至包裝函式類別或其個別屬性的 <xref:System.Configuration.SettingsProviderAttribute> 來定義。  如果沒有明確指定設定提供者，則將使用預設提供者 <xref:System.Configuration.LocalFileSettingsProvider>。  於是，這個架構支援建立和使用自訂設定提供者。  
  
 例如，假設您想要開發和使用 `SqlSettingsProvider`，而且這是將所有設定資料儲存於 Microsoft SQL Server 資料庫的提供者。  <xref:System.Configuration.SettingsProvider> 的衍生類別會在它的  `Initialize`  方法中接收此項資訊做為 <xref:System.Collections.Specialized.NameValueCollection?displayProperty=fullName> 型別的參數。  接著，您要實作 <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> 方法，從資料存放區擷取設定，然後再實作 <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> 以儲存設定。  您的提供者可以使用提供給 <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> 的 <xref:System.Configuration.SettingsPropertyCollection>，以判斷屬性 \(Property\) 的名稱、型別和範圍，以及為該屬性 \(Property\) 定義的任何其他設定屬性 \(Attribute\)。  
  
 您的提供者將需要實作一個屬性和一個方法，但是它們的實作結果可能會不太明顯。  <xref:System.Configuration.SettingsProvider.ApplicationName%2A> 屬性是 <xref:System.Configuration.SettingsProvider> 的抽象屬性，您應該對該屬性進行程式設計，傳回以下內容：  
  
 [!code-csharp[ApplicationSettings.Architecture#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 您的衍生類別也必須實作 `Initialize` 方法，這個方法不接收引數也不傳回值。  這個方法不是由 <xref:System.Configuration.SettingsProvider> 定義。  
  
 最後，您在提供者上實作 <xref:System.Configuration.IApplicationSettingsProvider> 以提供以下支援：重新整理設定、將設定轉換成設定預設值、將設定從某一應用程式版本升級為其他版本。  
  
 當您實作和編譯好提供者之後，需要再指示設定類別以使用這個提供者而非預設值。  您可透過 <xref:System.Configuration.SettingsProviderAttribute> 完成這項工作。  如果提供者是套用至整個設定類別，則它將可用於該類別所定義的每個設定；如果是套用至個別設定，應用程式設定架構只會在這些設定使用該提供者，在其餘部分則是使用 <xref:System.Configuration.LocalFileSettingsProvider>。  下列程式碼範例會示範如何指示設定類別以使用您的自訂提供者：  
  
 [!code-csharp[ApplicationSettings.Architecture#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 提供者可能是從多重執行緒同時呼叫的，但它將永遠寫入相同的儲存位置，因此，應用程式設定架構始終只會產生單一提供者類別執行個體。  
  
> [!IMPORTANT]
>  請務必確認提供者屬於安全執行緒 \(Thread\-Safe\)，而且寫入組態檔時，一次只允許一個執行緒。  
  
 您的提供者不必支援 <xref:System.Configuration?displayProperty=fullName> 命名空間中定義的所有設定屬性，但是它至少必須支援 <xref:System.Configuration.ApplicationScopedSettingAttribute> 和 <xref:System.Configuration.UserScopedSettingAttribute>，同時也應該支援 <xref:System.Configuration.DefaultSettingValueAttribute>。  對於不支援的屬性，提供者發生失敗而不會另行告知，它並不會擲回例外狀況。  但是如果設定類別使用了無效的屬性組合，例如將 <xref:System.Configuration.ApplicationScopedSettingAttribute> 和 <xref:System.Configuration.UserScopedSettingAttribute> 套用至同一個設定，則您的提供者會擲回例外狀況並且停止作業。  
  
## 請參閱  
 <xref:System.Configuration.ApplicationSettingsBase>   
 <xref:System.Configuration.SettingsProvider>   
 <xref:System.Configuration.LocalFileSettingsProvider>   
 [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [自訂控制項的應用程式設定](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)   
 [ClickOnce 和應用程式設定](../Topic/ClickOnce%20and%20Application%20Settings.md)   
 [應用程式設定結構描述](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)