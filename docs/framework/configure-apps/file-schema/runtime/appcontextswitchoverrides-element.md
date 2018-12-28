---
title: '&lt;Appcontextswitchoverrides>&gt;項目'
ms.custom: updateeachrelease
ms.date: 09/19/2018
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5498874661f36ee4e96e6d2d58e3076bb8abbcce
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611486"
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;Appcontextswitchoverrides>&gt;項目
定義一或多個由 <xref:System.AppContext> 類別所使用的參數，以提供新功能的退出機制。  
  
 \<configuration>  
 \<執行階段 >  
\<AppContextSwitchOverrides>  
  
## <a name="syntax"></a>語法  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`value`|必要屬性。<br /><br /> 定義一或多個參數名稱和其相關聯的布林值。|  
  
### <a name="value-attribute"></a>值屬性  
  
|值|描述|  
|-----------|-----------------|  
|"name=value"|預先定義的參數名稱和其值 (`true`或`false`)。 多個參數名稱/值組會以分號 （";"）。 如需.NET Framework 所支援的預先定義的參數名稱的清單，請參閱 < 備註 > 一節。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 從.NET Framework 4.6 開始`<AppContextSwitchOverrides>`組態檔中的項目可讓呼叫端的 API，以判斷其應用程式可以利用新功能或保留與舊版文件庫的相容性。 例如，如果程式庫的兩個版本之間已經變更 API 的行為`<AppContextSwitchOverrides>`項目可讓呼叫端，該 api 來選擇退出新行為的程式庫支援的新功能的版本上。 在.NET Framework 中，呼叫 Api 的應用程式的`<AppContextSwitchOverrides>`項目也可以允許呼叫端的應用程式為目標是舊版的.NET Framework，才能選擇加入新功能，如果包含的.NET Framework 版本上執行其應用程式功能。  
  
 `value`屬性的`<AppContextSwitchOverrides>`項目是由一或多個以分號分隔名稱/值組所組成的單一字串所組成。  每個名稱會識別相容性參數，以及其對應的值是布林值 (`true`或`false`)，指出是否已設定此參數。 根據預設，此參數是`false`，和程式庫提供的新功能。 如果此參數設定只提供先前的功能 (亦即，其值是`true`)。 這可讓程式庫，以提供現有的 API 中的新行為，同時允許呼叫端相依於先前的行為，若要退出新功能。  
  
 .NET Framework 支援下列參數：  
  
|交換器名稱|描述|導入|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|控制 Windows Presentation Foundation 是否使用傳統演算法的控制項配置。 如需詳細資訊，請參閱[風險降低：WPF 版面配置](~/docs/framework/migration-guide/mitigation-wpf-layout.md)。|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|控制用來簽署套件各部分的 PackageDigitalSignatureManager 的預設演算法是 SHA1 或 SHA256。|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|當設定為`false`，允許偵錯使用 Visual Studio 的 XAML 型工作流程專案時都啟用 FIPS。 否則， <xref:System.NullReferenceException> System.Activities 組件中的方法呼叫中會擲回。|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|控制偵錯工具中的工作流程執行個體的總和檢查碼是否使用 MD5 或 SHA1。 | .NET Framework 4.7|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|堆疊追蹤是取得使用可攜式 Pdb 時可以包含來源檔案和行資訊的控制項。 `false` 包含來源檔案和行資訊;否則， `true`。|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|控制項是否<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType>方法會擲回的例外狀況時<xref:System.Drawing.Icon>物件具有 PNG 畫面格。 如需詳細資訊，請參閱[風險降低：圖示物件中的 PNG 畫面格](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md)。|.NET Framework 4.6|  
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|決定是否<xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType>新增至集合時，正確地處置物件<xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>方法。 `true` 若要維護舊版的行為。`false`來進行處置的私用字型的所有物件。 |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`</br>`OptimizePrintPreview`|控制項是否的效能<xref:System.Windows.Forms.PrintPreviewDialog>最適合用於網路印表機。 如需詳細資訊，請參閱 < [PrintPreviewDialog 控制項概觀](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md)。|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|控制是否非同步作業不會流動從呼叫的執行緒內容。 如需詳細資訊，請參閱 < [CurrentCulture 和 CurrentUICulture 流程在工作上](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks)。|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|控制項是否<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType>方法會嘗試比對的宣告型別，只會使用最後一個 DNS 項目。 如需詳細資訊，請參閱[風險降低：X509CertificateClaimSet.FindClaims 方法](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)。|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|控制是否要允許 AuthorizationContext.Empty 傳回可變動的物件。|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|控制項是否路徑長度超過`MAX_PATH`（260 個字元） 會擲回<xref:System.IO.PathTooLongException>。 如需詳細資訊，請參閱 <<c0> [ 長路徑支援](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support)。|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|控制是否進行解壓縮的使用原生 OS 常式<xref:System.IO.Compression.DeflateStream>類別。 `false` 若要使用原生 Api;`true`使用<xref:System.IO.Compression.DeflateStream>實作。|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|使用反斜線 ("\\」) 而不是正斜線 （"/"） 為路徑分隔符號<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>屬性。 如需詳細資訊，請參閱[風險降低：ZipArchiveEntry.FullName 路徑分隔符號](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)。|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|控制是否運作系統建立的背景執行緒擲回的例外狀況<xref:System.IO.Ports.SerialPort>資料流結束處理序。|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|控制是否使用舊版的路徑正規化，以及所支援的 URI 路徑<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType>和<xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>方法。 如需詳細資訊，請參閱[風險降低：路徑正規化](~/docs/framework/migration-guide/mitigation-path-normalization.md)和[風險降低：路徑冒號檢查](~/docs/framework/migration-guide/mitigation-path-colon-checks.md)。|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|控制是否相等比較的測試<xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType>一個物件的屬性<xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType>第二個物件的屬性。 如需詳細資訊，請參閱 < [MemberDescriptor.Equals 的實作不正確](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals)。|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|停用憑證增強金鑰使用方法 (EKU) 物件識別碼 (OID) 驗證。 增強金鑰使用方法 (EKU) 延伸模組是表示使用金鑰之應用程式的物件識別碼 (OID) 集合。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|停用將 SCH_SEND_AUX_RECORD 停用 TLS1.0 瀏覽器利用針對 SSL/TLS (BEAST) 風險降低。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|控制項是否<xref:System.Net.ServicePointManager?displayProperty=nameWithType>和<xref:System.Net.Security.SslStream?displayProperty=nameWithType>類別可以使用 SSL 3.0 通訊協定。 如需詳細資訊，請參閱[風險降低：TLS 通訊協定](~/docs/framework/migration-guide/mitigation-tls-protocols.md)。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|停用還原回預設值是 Tls12、 Tls11、 Tls 的 SystemDefault TLS 版本。|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|停用 SslStream TLS 伺服器端的警示。|.NET Framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |控制項是否[DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer)序列化某些於 ECMAScript V6 及 V8 標準為基礎的控制字元。 如需詳細資訊，請參閱[風險降低：序列化使用 DataContractJsonSerializer 控制字元](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|控制項是否<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>支援多個調整或只有單一調整時區。 如果`true`，它會使用<xref:System.TimeZoneInfo>類型來序列化和還原序列化日期和時間資料; 否則它會使用<xref:System.TimeZone>型別，不支援多個調整規則。|.NET Framework 4.6.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|控制項是否<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType>建構函式會設定新的物件<xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType>與現有的物件參考的屬性。 如需詳細資訊，請參閱[風險降低：ClaimsIdentity 建構函式](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md)。|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|控制是否要重複使用嘗試<xref:System.Security.Cryptography.AesCryptoServiceProvider>解密程式會擲回<xref:System.Security.Cryptography.CryptographicException>。 如需詳細資訊，請參閱 < [AesCryptoServiceProvider 解密程式提供可重複使用的轉換](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform)。|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|控制項是否的值[cspparameters.parentwindowhandle 應該](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle)屬性是[IntPtr](xref:System.IntPtr)代表視窗的記憶體位置處理，或它是否視窗控制代碼 (HWND)。 如需詳細資訊，請參閱[風險降低：Cspparameters.parentwindowhandle 應該有 HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md)。 |.NET Framework 4.7|   
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|判斷某些 SignedCMS 作業的預設值是 SHA1 或 SHA256。 |.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|判斷某些 SignedXML 作業的預設值是 SHA1 或 SHA256。 |.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|決定是否`TransportWithMessageCredential`安全性模式可讓訊息與不帶正負號"to"標頭。 這是選擇性參數。 如需詳細資訊，請參閱 < [.NET Framework 4.6.1 中的執行階段變更](~/docs/framework/migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf)。|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|控制項是否<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>建構函式會擲回<xref:System.ArgumentException>如果其中一個項目是`null`。|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|決定是否在嘗試使用 X509 憑證使用 CSG 金鑰儲存提供者會擲回例外狀況。 如需詳細資訊，請參閱 < [WCF 傳輸安全性支援使用 CNG 儲存的憑證](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng)。|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|自我裝載的服務中使用 HTTP 傳輸，此值設定為`true`讓 WCF 要略過的應用程式新增`Connection: close`標頭以要求的回應標頭。 此值設定為`false`即可加入`Connection: close`標頭以回應標頭中，會導致傳送回應之後，關閉要求通訊端。|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|處理死結 （deadlock） 所產生的單一執行緒執行一次的限制可重新進入服務的執行個體。|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|連同`Switch.System.Net.DontEnableSchUseStrongCrypto`，決定 WCF 訊息安全性使用 TLS 1.1 和 TLS 1.2。|.NET Framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|值為`false`設定預設設定，以允許作業系統選擇通訊協定。 值為`true`最高的通訊協定設定預設值。 （也適用於服務的舊版 framework 的分支）|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|決定的預設訊息簽署在 WCF 中的 MSMQ 訊息的演算法是 SHA1 或 SHA256。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|控制 WCF 來產生的具名管道的隨機名稱是否使用 SHA1 或 SHA256 雜湊。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|控制是否要擲回[NullReferenceException](xref:System.NullReferenceException)當例外狀況訊息為 null。|.NET Framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|控制是否在服務啟動時擲回例外狀況會傳播到呼叫端<xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>方法。|.NET Framework 4.7.1|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|決定是否某些有時已解碼的百分比編碼字元現在一致保持編碼。 如果`true`，它們是解碼，否則`false`。|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|決定在 Uri 中的 Unicode 雙向字元的處理。 `true` 若要刪除從 Uri;`false`保留，並且百分比編碼它們。|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |決定 Windows Presentation Foundation 是否套用舊的演算法 (`true`) 或新的演算法 (`false`) 中配置空間\*-資料行。 如需詳細資訊，請參閱[風險降低：方格控制項對 star-columns 的空間配置](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md)。 |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|控制項選取器或索引標籤的永遠控制是否引發選取項目之前更新其屬性的值選取的值已變更事件。|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|判斷是否可供非裝飾項根據選取項目轉譯<xref:System.Windows.Controls.TextBox>並<xref:System.Windows.Controls.PasswordBox>控制項，以防止 occluded 文字 (`false`)，或是否只能在裝飾項圖層轉譯文字 (`true`)。|.NET Framework 4.7.2|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|判斷每個系統上是否發生 DPI 變更 (值為`false`) 或每個監視的頻率 (值為`true`)。|.NET Framework 4.6.2|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|判斷是否需要特別處理開發人員<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>控制項文字存在時的動作。 `true` 若要處理<xref:System.Windows.Forms.DomainUpDown.UpButton>動作;`false` for<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>和<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>正確保持同步的動作。|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|選擇退出程式碼，可讓自訂<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>實作，以安全地篩選訊息，而不擲回例外狀況時<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>呼叫方法。 如需詳細資訊，請參閱[風險降低：自訂 IMessageFilter.PreFilterMessage 實作](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|決定是否<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>屬性會傳回原始檔控制當使用者開啟功能表，從巢狀<xref:System.Windows.Forms.ToolStripMenuItem>控制項。 `true` 要傳回`null`，舊版的行為。`false`返回原始檔控制。|.NET Framework 4.7.2|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|決定是否選用`WM_POINTER`為基礎的觸控/手寫筆堆疊已啟用 WPF 應用程式中。 如需詳細資訊，請參閱[風險降低：指標為基礎的觸控及手寫筆支援](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|決定是否使用總和檢查碼的預設雜湊演算法是 SHA256 (`false`) 或 SHA1 (`true`)。|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|控制是否舊式[NullReferenceException](xref:System.NullReferenceException)而不是更明確地指出造成例外狀況的例外狀況擲回 (例如[DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException)或[FileNotFoundException](xref:System.IO.FileNotFoundException)。 它取決於處理的程式碼適用於[NullReferenceException](xref:System.NullReferenceException)。 | .NET Framework 4.7 |
|`Switch.UseLegacyAccessibilityFeatures`|控制項是否可從.NET Framework 4.7.1 的協助工具功能會啟用或停用。 | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|協助工具功能提供於.NET Framework 4.7.2 是否已啟用的控制項 (`false`) 或停用 (`true`)。 如果`true`，`Switch.UseLegacyAccessibilityFeatures`也必須是`true`啟用.NET Framework 4.7.1 協助工具功能。|.NET Framework 4.7.2|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|控制是否 XSD 結構描述驗證會忽略空的索引鍵序列中的複合索引鍵。 如需詳細資訊，請參閱[風險降低：XML 結構描述驗證](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md)。|.NET Framework 4.6|  
  
> [!NOTE]
>  而不是新增`AppContextSwitchOverrides`應用程式組態檔項目，您也可以設定參數以程式設計方式呼叫`static`（在 C# 中) 或`Shared`（在 Visual Basic)<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>方法。  
  
 程式庫開發人員也可以定義自訂的參數，可讓呼叫者選擇不變更其程式庫的更新版本中引進的功能。 如需詳細資訊，請參閱 <xref:System.AppContext> 類別。  
  
## <a name="switches-in-aspnet-applications"></a>在 ASP.NET 應用程式中的參數

您可以設定 ASP.NET 應用程式使用的相容性設定，加上[\<新增 >](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md)項目[ \<appSettings >](~/docs/framework/configure-apps/file-schema/appsettings/index.md) web.config 檔案區段。 

下列範例會使用`<add>`要加入至兩個設定項目`<appSettings>`web.config 檔案區段：

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>範例

 下列範例會使用`AppContextSwitchOverrides`項目來定義單一應用程式相容性參數， `Switch.System.Globalization.NoAsyncCurrentCulture`，這樣可防止文化特性中的非同步方法呼叫的執行緒之間流動。  
  
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
- <xref:System.AppContext?displayProperty=nameWithType>  
- [\<執行階段 > 項目](runtime-element.md)  
- [\<configuration> 項目](../configuration-element.md)
