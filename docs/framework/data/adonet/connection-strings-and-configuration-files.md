---
title: 連接字串和組態檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: a4876d3b794282852b364f58cc84b58546567d80
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="connection-strings-and-configuration-files"></a>連接字串和組態檔
在應用程式的程式碼中嵌入連接字串可能會導致安全性漏洞和維護問題。 您可以使用檢視編譯成應用程式的原始碼的未加密的連接字串[Ildasm.exe （IL 解譯器）](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md)工具。 此外，如果連接字串變更，應用程式就必須重新編譯。 基於上述理由，建議您將連接字串儲存在應用程式組態檔中。  
  
## <a name="working-with-application-configuration-files"></a>使用應用程式組態檔  
 應用程式組態檔包含特定應用程式專屬的設定。 例如，ASP.NET 應用程式可以有一或多個**web.config**檔案和 Windows 應用程式可以有選用**app.config**檔案。 組態檔會共用通用的項目，但組態檔的名稱及位置則會根據應用程式的主機而不同。  
  
### <a name="the-connectionstrings-section"></a>connectionStrings 區段  
 連接字串可以儲存為索引鍵/值組**connectionStrings**區段**組態**的應用程式組態檔項目。 子項目包括**新增**，**清除**，和**移除**。  
  
 下列組態檔片段示範儲存連接字串的結構描述和語法。 **名稱**屬性是可唯一識別連接字串，使它可以擷取在執行階段的名稱。 **ProviderName**是註冊在 machine.config 檔案中的.NET Framework 資料提供者非變異名稱。  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
  <configuration>  
    <connectionStrings>  
      <clear />  
      <add name="Name"   
       providerName="System.Data.ProviderName"   
       connectionString="Valid Connection String;" />  
    </connectionStrings>  
  </configuration>  
```  
  
> [!NOTE]
>  您可將部分連接字串儲存在組態檔中，然後在執行階段使用 <xref:System.Data.Common.DbConnectionStringBuilder> 類別 (Class) 加以完成。 在您無法預先知道連接字串的項目，或者不想將機密資訊儲存在組態檔中時，這種方法很有用。 如需詳細資訊，請參閱[連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)。  
  
### <a name="using-external-configuration-files"></a>使用外部組態檔  
 外部組態檔是包含組態檔片段 (由單一區段組成) 的個別檔案。 外部組態檔接著會由主組態檔來參考。 儲存**connectionStrings**實際分開的檔案中區段是在應用程式部署之後，編輯連接字串可能位置的情況下很有用。 例如，標準的 ASP.NET 行為是在組態檔修改時重新啟動應用程式網域，而這可能導致狀態資訊遺失。 然而，修改外部組態檔並不會造成應用程式重新啟動。 外部組態檔並不僅限於 ASP.NET 才有，Windows 應用程式也可加以利用； 此外，也可以透過檔案存取安全性和權限，限制對外部組態檔的存取權。 執行階段的外部組態檔使用是透明的，而且不需要任何特殊的程式碼。  
  
 若要將連接字串儲存在外部組態檔中，建立個別的檔案只包含**connectionStrings** > 一節。 請勿包含任何額外的項目、區段或屬性。 此範例說明外部組態檔的語法。  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 在主應用程式組態檔中，您會使用**configSource**屬性來指定完整的名稱和外部檔案的位置。 此範例會參考名為 `connections.config` 的外部組態檔。  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>在執行階段擷取連接字串  
 .NET Framework 2.0 在 <xref:System.Configuration> 命名空間 (Namespace) 中導入了新的類別，可簡化在執行階段從組態檔中擷取連接字串的作業。 您可以透過程式設計的方式，依名稱或提供者名稱擷取連接字串。  
  
> [!NOTE]
>  **Machine.config**檔案也包含**connectionStrings**區段，其中包含使用 Visual Studio 的連接字串。 從提供者名稱擷取連接字串時**app.config** Windows 應用程式中的連接字串中的檔案**machine.config**取得已載入，然後再將項目從**app.config**。加入**清除**之後立即**connectionStrings**項目移除所有繼承的參考資料結構，在記憶體中，以便只連接字串會定義本機**app.config**視為檔案。  
  
### <a name="working-with-the-configuration-classes"></a>使用組態類別  
 從 .NET Framework 2.0 開始，在本機電腦上使用組態檔時，就會使用 <xref:System.Configuration.ConfigurationManager> 來取代已被取代的 <xref:System.Configuration.ConfigurationSettings>。 <xref:System.Web.Configuration.WebConfigurationManager> 則會用於搭配 ASP.NET 組態檔。 它設計來搭配 網頁伺服器上的組態檔，並允許以程式設計方式存取組態檔區段，例如**system.web**。  
  
> [!NOTE]
>  您必須為呼叫端授與權限，才能在執行階段存取組態檔；所需的權限則根據應用程式類型、組態檔以及位置而有所不同。 如需詳細資訊，請參閱[使用組態類別](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)和<xref:System.Web.Configuration.WebConfigurationManager>ASP.NET 應用程式，以及<xref:System.Configuration.ConfigurationManager>Windows 應用程式。  
  
 您可以利用 <xref:System.Configuration.ConnectionStringSettingsCollection> 從應用程式組態檔擷取連接字串。 它包含的集合<xref:System.Configuration.ConnectionStringSettings>物件，其中每一個都代表單一項目中**connectionStrings** > 一節。 其屬性會對應至連接字串屬性，讓您可以藉由指定名稱或提供者名稱而擷取連接字串。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|連接字串的名稱。 對應至**名稱**屬性。|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|完整的提供者名稱。 對應至**providerName**屬性。|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|連接字串。 對應至**connectionString**屬性。|  
  
### <a name="example-listing-all-connection-strings"></a>範例：列出所有連接字串  
 此範例逐一查看 `ConnectionStringSettings` 集合，並在主控台 (Console) 視窗中顯示 <xref:System.Configuration.ConnectionStringSettings.Name%2A>、<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> 和 <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A> 屬性。  
  
> [!NOTE]
>  System.Configuration.dll 並未包含在所有專案類型中，您可能需要設定其參考，才能使用該組態類別。 特定應用程式組態檔的名稱和位置會根據應用程式類型及裝載處理序而不同。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>範例：依名稱擷取連接字串  
 此範例示範如何藉由指定連接字串的名稱，從組態檔擷取連接字串。 程式碼會建立 <xref:System.Configuration.ConnectionStringSettings> 物件，並將提供的輸入參數與 <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> 名稱進行比對。 如果沒有找到符合的名稱，函式就會傳回 `null` (在 Visual Basic 中則為 `Nothing`)。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>範例：依提供者名稱擷取連接字串  
 這個範例示範如何藉由指定的格式提供者非變異名稱擷取連接字串*System.Data.ProviderName*。 程式碼會逐一查看 <xref:System.Configuration.ConnectionStringSettingsCollection>，並針對第一個找到的 <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> 傳回連接字串。 如果找不到提供者名稱，函式就會傳回 `null` (在 Visual Basic 中則為 `Nothing`)。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>使用受保護的組態來加密組態檔區段  
 ASP.NET 2.0 導入了新功能，稱為*受保護的組態*，，可讓您加密組態檔中的機密資訊。 雖然主要是針對 ASP.NET 所設計，但這項功能仍可用來加密 Windows 應用程式中的組態檔區段。 受保護的組態功能的詳細說明，請參閱[加密組態資訊使用受保護的組態](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)。  
  
 下列組態檔片段示範**connectionStrings**區段之後已加密。 **ConfigProtectionProvider**指定用來加密和解密連接字串的受保護的組態提供者。 **EncryptedData**區段包含加密文字。  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 .NET Framework 執行階段擷取加密的連接字串時，使用指定的提供者來解密**CipherValue** ，並提供您的應用程式。 您不需要撰寫任何額外的程式碼來管理解密程序。  
  
### <a name="protected-configuration-providers"></a>受保護的組態提供者  
 受保護的組態提供者會登錄在**c**區段**machine.config**所示，在下列的片段中，會顯示兩個檔案的本機電腦上，.NET Framework 所提供的受保護的組態提供者。 為了便於讀取，這裡顯示的值已經過刪減。  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"   
      type="System.Configuration.RsaProtectedConfigurationProvider, ... />  
    <add name="DataProtectionConfigurationProvider"   
      type="System.Configuration.DpapiProtectedConfigurationProvider, ... />  
  </providers>  
</configProtectedData>  
```  
  
 您可以設定其他受保護的組態提供者藉由加入**machine.config**檔案。 也可以從 <xref:System.Configuration.ProtectedConfigurationProvider> 抽象基底類別 (Base Class) 繼承而建立自己的受保護組態提供者。 下表說明 .NET Framework 所隨附的兩個組態檔。  
  
|提供者|描述|  
|--------------|-----------------|  
|<!--zz<xref:System.Configuration.RSAProtectedConfigurationProvider>-->`System.Configuration.RSAProtectedConfigurationProvider`|使用 RSA 加密演算法來加密及解密資料。 RSA 演算法可用於公開金鑰 (Public Key) 加密及數位簽章。 這種演算法也稱為「公開金鑰」或非對稱加密，因為它會使用兩種不同的金鑰。 您可以使用[ASP.NET IIS 註冊工具 (Aspnet_regiis.exe)](http://msdn.microsoft.com/library/6491c41e-e2b0-481f-9863-db3614d5f96b)加密 Web.config 檔案中的區段和管理加密金鑰。 ASP.NET 會在處理檔案時對組態檔進行解密。 ASP.NET 應用程式的識別必須可以讀取用於對區段進行加密及解密的加密金鑰。|  
|<!--zz<xref:System.Configuration.DPAPIProtectedConfigurationProvider>-->`System.Configuration.DPAPIProtectedConfigurationProvider`|使用 Windows Data Protection API (DPAPI) 來加密組態區段。 DPAPI 使用 Windows 內建的密碼編譯服務，可以針對電腦特定或使用者帳戶特定的保護進行設定。 電腦特定的保護特別適用於相同伺服器上需要共用資訊的多個應用程式。 使用者特定的保護則可用於使用特定使用者識別執行的服務，例如共用的裝載環境。 每個應用程式都會在不同的識別之下執行，如此可限制對檔案和資料庫等資源的存取。|  
  
 這兩種提供者都提供高度加密的資料。 不過，如果您打算在多個伺服器 (例如 Web 伺服陣列) 上使用相同的加密組態檔，則只有使用 `RsaProtectedConfigurationProvider` 才能匯出用於加密資料的加密金鑰並將其匯入另一個伺服器。 如需詳細資訊，請參閱[匯入及匯出受保護組態的 RSA 金鑰容器](http://msdn.microsoft.com/library/f3022b39-f17f-48c1-b067-025eab0ce8bc)。  
  
### <a name="using-the-configuration-classes"></a>使用組態類別  
 <xref:System.Configuration> 命名空間 (Namespace) 提供類別 (Class)，以透過程式設計的方式使用組態設定。 <xref:System.Configuration.ConfigurationManager> 類別可用於存取電腦、應用程式及使用者組態檔。 如果您要建立 ASP.NET 應用程式，您可以使用<xref:System.Web.Configuration.WebConfigurationManager>類別，可提供相同的功能，還可讓您存取 ASP.NET 應用程式，例如所特有的設定中找到時 **\<system.web >**。  
  
> [!NOTE]
>  <xref:System.Security.Cryptography> 命名空間包含可為資料加密及解密提供額外選項的類別。 如果需要無法使用受保護組態而提供的密碼編譯服務，請使用這些類別。 這其中某些類別是 Unmanaged Microsoft CryptoAPI 的包裝函式，某些則純粹是 Managed 實作 (Implementation)。 如需詳細資訊，請參閱[密碼編譯服務](http://msdn.microsoft.com/library/68a1e844-c63c-44af-9247-f6716eb23781)。  
  
### <a name="appconfig-example"></a>App.config 範例  
 此範例示範如何切換加密**connectionStrings**一節中**app.config** Windows 應用程式檔案。 在此範例中，程序會採用應用程式的名稱做為引數，例如 "MyApplication.exe"。 **App.config**檔案接著會加密，並複製到在"MyApplication.exe.config"的名稱下可執行檔所在的資料夾。  
  
> [!NOTE]
>  連接字串只能在當初進行加密的電腦上進行解密。  
  
 程式碼會使用<xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A>方法來開啟**app.config**檔案進行編輯，而<xref:System.Configuration.ConfigurationManager.GetSection%2A>方法會傳回**connectionStrings** > 一節。 接著程式碼會檢查 <xref:System.Configuration.SectionInformation.IsProtected%2A> 屬性，並呼叫 <xref:System.Configuration.SectionInformation.ProtectSection%2A> 來加密區段 (如果尚未加密)， 然後再叫用 <xref:System.Configuration.SectionInformation.UnprotectSection%2A> 方法來對區段進行解密。 <xref:System.Configuration.Configuration.Save%2A> 方法則會完成作業並儲存變更。  
  
> [!NOTE]
>  您必須在專案中設定 `System.Configuration.dll` 的參考，程式碼才能執行。  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Web.config 範例  
 此範例使用 <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> 的 `WebConfigurationManager` 方法。 請注意，在此情況下您可以提供的相對路徑**Web.config**使用波狀符號檔案。 程式碼需要 `System.Web.Configuration` 類別的參考。  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 保護 ASP.NET 應用程式的詳細資訊，請參閱[NIB: ASP.NET 安全性](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d)和[ASP.NET 2.0 安全性作法一眼](http://go.microsoft.com/fwlink/?LinkId=59997)ASP.NET 開發人員中心。  
  
## <a name="see-also"></a>另請參閱  
 [連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [使用組態類別](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [設定應用程式](../../../../docs/framework/configure-apps/index.md)  
 [ASP.NET 網站管理](http://msdn.microsoft.com/library/1298034b-5f7d-464d-abd1-ad9e6b3eeb7e)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
