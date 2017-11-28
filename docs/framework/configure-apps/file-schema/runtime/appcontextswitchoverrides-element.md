---
title: "&lt;AppContextSwitchOverrides&gt;項目"
ms.custom: 
ms.date: 10/17/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ed1b11cef909af153e43d61e71a4875648bdbfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;AppContextSwitchOverrides&gt;項目
定義一或多個由 <xref:System.AppContext> 類別所使用的參數，以提供新功能的退出機制。  
  
 \<configuration>  
 \<執行階段 >  
\<AppContextSwitchOverrides >  
  
## <a name="syntax"></a>語法  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`value`|必要屬性。<br /><br /> 定義一或多個參數名稱和其相關聯的布林值。|  
  
### <a name="value-attribute"></a>屬性值  
  
|值|說明|  
|-----------|-----------------|  
|「 名稱 = 值 」|預先定義的參數名稱，以及其值 (`true`或`false`)。 多個參數名稱/值組以分號分隔 （";"）。 如需.NET Framework 所支援的預先定義的參數名稱的清單，請參閱 < 備註 > 一節。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 從.NET Framework 4.6 開始`<AppContextSwitchOverrides>`組態檔中的項目可讓呼叫端的 API，以決定其應用程式可以充分利用新功能或保留與舊版的程式庫相容性。 例如，如果應用程式開發介面的行為已變更的程式庫中，兩個版本之間`<AppContextSwitchOverrides>`項目可讓呼叫端，該 api 來支援新功能的程式庫版本的新行為來選擇退出。 在.NET Framework 中，呼叫 Api 的應用程式`<AppContextSwitchOverrides>`項目也可讓呼叫端的應用程式目標的舊版.NET Framework，以選擇加入新功能，如果包含的.NET Framework 版本上執行其應用程式這項功能。  
  
 `value`屬性`<AppContextSwitchOverrides>`元素所組成的單一字串，包含一或多個以分號分隔名稱/值組。  每個名稱識別的相容性參數，且其對應的值為布林值 (`true`或`false`)，指出是否已設定的參數。 根據預設，這個參數是`false`，和程式庫提供的新功能。 它們僅提供先前的功能，如果已設定參數 (亦即，其值是`true`)。 這可讓現有的 api 提供新的行為，同時允許取決於先前的行為，退出新功能的呼叫端程式庫。  
  
 .NET Framework 支援下列參數：  
  
|參數名稱|說明|導入|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|控制 Windows Presentation Foundation 是否使用傳統演算法的控制項配置。 如需詳細資訊，請參閱[風險降低：WPF 版面配置](~/docs/framework/migration-guide/mitigation-wpf-layout.md)。|.NET Framework 4.6|  
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|當設定為`false`，允許 FIPS 已啟用時，Visual Studio 的 XAML 型工作流程專案的偵錯。 未安裝， <xref:System.NullReferenceException> System.Activities 組件中的方法的呼叫中是否擲回。|.NET Framework 4.7|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|控制項是否<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType>方法會擲回的例外狀況時<xref:System.Drawing.Icon>物件具有 PNG 畫面格。 如需詳細資訊，請參閱[風險降低：Icon 物件中的 PNG 畫面格](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md)。|.NET Framework 4.6|  
|`Switch.System.Globalization.NoAsyncCurrentCulture`|控制是否非同步作業不會流動從呼叫的執行緒內容。 如需詳細資訊，請參閱[CurrentCulture 和 CurrentUICulture 流經工作](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks)。|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|控制項是否<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType>方法會嘗試比對的宣告類型，只能使用最後一個 DNS 項目。 如需詳細資訊，請參閱[風險降低：X509CertificateClaimSet.FindClaims 方法](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)。|.NET Framework 4.6.1|  
|`Switch.System.IO.BlockLongPaths`|控制項是否路徑長度超過`MAX_PATH`（260 個字元） 會擲回<xref:System.IO.PathTooLongException>。 如需詳細資訊，請參閱[長路徑支援](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support)。|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|使用反斜線 ("\\") 而不是正斜線 （"/"） 為路徑分隔符號<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>屬性。 如需詳細資訊，請參閱[風險降低： ZipArchiveEntry.FullName 路徑分隔符號](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)。|.NET Framework 4.6.1|  
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|控制是否使用傳統路徑正規化和所支援的 URI 路徑<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType>和<xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>方法。 如需詳細資訊，請參閱[風險降低： 路徑正規化](~/docs/framework/migration-guide/mitigation-path-normalization.md)和[風險降低： 路徑冒號會檢查](~/docs/framework/migration-guide/mitigation-path-colon-checks.md)。|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|控制是否為等號比較測試<xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType>與某個物件的屬性<xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType>第二個物件的屬性。 如需詳細資訊，請參閱[不正確實作 MemberDescriptor.Equals](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals)。|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|停用憑證增強金鑰使用方法 (EKU) 物件識別碼 (OID) 驗證。 增強金鑰使用方法 (EKU) 延伸模組是物件識別碼 (Oid)，以指出應用程式使用金鑰的集合。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|停用使用 SCH_SEND_AUX_RECORD 停用 TLS1.0 瀏覽器利用針對 SSL/TLS (BEAST) 補救。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|控制項是否<xref:System.Net.ServicePointManager?displayProperty=nameWithType>和<xref:System.Net.Security.SslStream?displayProperty=nameWithType>類別可以使用 SSL 3.0 通訊協定。 如需詳細資訊，請參閱[風險降低：TLS 通訊協定](~/docs/framework/migration-guide/mitigation-tls-protocols.md)。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|停用 SystemDefault TLS 版本還原成預設值是 Tls12、 Tls11、 Tls。|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|停用 SslStream TLS 伺服器端的警示。|.NET Framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |控制項是否[DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer)序列化某些 ECMAScript V6 和 V8 標準為基礎的控制字元。 如需詳細資訊，請參閱[風險降低︰使用 DataContractJsonSerializer 控制字元的序列化](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)| .NET Framework 4.7 |
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|控制項是否<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType>建構函式設定新的物件<xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType>與現有的物件參考的屬性。 如需詳細資訊，請參閱[風險降低︰ClaimsIdentity 建構函式](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md)。|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|控制項是否嘗試重複使用<xref:System.Security.Cryptography.AesCryptoServiceProvider>的解密程式來擲回<xref:System.Security.Cryptography.CryptographicException>。 如需詳細資訊，請參閱 AesCryptoServiceProvider 的解密程式來提供可重複使用 transform](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform)。|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|控制項是否值[CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle)屬性是[IntPtr](xref:System.IntPtr)代表視窗的記憶體位置處理，或它是否視窗控制代碼 (HWND)。 如需詳細資訊，請參閱[風險降低︰CspParameters.ParentWindowHandle 應該有 HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md)。 |.NET Framework 4.7|   
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|決定是否`TransportWithMessageCredential`安全性模式可讓訊息與不帶正負號"to"標頭。 這是選擇性參數。 如需詳細資訊，請參閱[.NET Framework 4.6.1 中的執行階段變更](https://msdn.microsoft.com/library/mt592686.aspx#WCF)。|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|決定是否嘗試使用 X509 憑證與 CSG 金鑰儲存提供者擲回例外狀況。 如需詳細資訊，請參閱[WCF 傳輸安全性支援儲存使用 CNG 憑證](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng)。|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|連同`Switch.System.Net.DontEnableSchUseStrongCrypto`，決定 WCF 訊息安全性使用 TLS 1.1 和 TLS 1.2。|.NET Framework 4.7 |    
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |決定 Windows Presentation Foundation 是否適用於舊的演算法 (`true`) 或新的演算法 (`false`) 中配置空間\*-資料行。 如需詳細資訊，請參閱[風險降低︰方格控制項對 Star-columns 的空間配置](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md)。 |.NET Framework 4.7 |
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|選擇不允許自訂程式碼<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>實作安全地篩選訊息，而不擲回例外狀況時<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>方法呼叫。 如需詳細資訊，請參閱[風險降低：自訂 IMessageFilter.PreFilterMessage 實作](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。|.NET Framework 4.6.1|  
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|決定是否選用`WM_POINTER`-根據的觸控/手寫筆的堆疊 WPF 應用程式中啟用。 如需詳細資訊，請參閱[風險降低： 指標為基礎的觸控和手寫筆支援](Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md) | 
|`Switch.System.Windows.Media.ImageSourceConverter`<br/>`OverrideExceptionWithNullReferenceException`|控制是否舊版[NullReferenceException](xref:System.NullReferenceException)而不是更具體地來說指出例外狀況原因的例外狀況擲回 (例如[DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException)或[FileNotFoundException](xref:System.IO.FileNotFoundException)。 適用於由處理所依賴的程式碼[NullReferenceException](xref:System.NullReferenceException)。 | .NET Framework 4.7 |
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|控制是否在複合的索引鍵中的空白索引鍵序列會忽略 XSD 結構描述驗證。 如需詳細資訊，請參閱[風險降低： XML 結構描述驗證](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md)。|.NET Framework 4.6|  
  
> [!NOTE]
>  而非新增`AppContextSwitchOverrides`應用程式組態檔項目，您也可以設定參數以程式設計方式透過呼叫`static`（C# 中） 或`Shared`（在 Visual Basic)<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>方法。  
  
 程式庫開發人員也可以定義自訂的參數，以允許呼叫端退出變更他們的程式庫的更新版本中引進的功能。 如需詳細資訊，請參閱 <xref:System.AppContext> 類別。  
  
## <a name="example"></a>範例  
 下列範例會使用`AppContextSwitchOverrides`項目來定義單一應用程式相容性參數， `Switch.System.Globalization.NoAsyncCurrentCulture`，可避免文化特性中的非同步方法呼叫的執行緒之間流動。  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 下列範例會使用`AppContextSwitchOverrides`項目來定義兩個應用程式相容性參數，`Switch.System.Globalization.NoAsyncCurrentCulture`和`Switch.System.IO.BlockLongPaths`。 請注意分號分隔的兩個名稱/值組。  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [AppContext](xref:System.AppContext?qualifyHint=False&autoUpgrade=True)  
 [\<runtime > 項目](runtime-element.md)  
 [\<configuration> 項目](../configuration-element.md)
