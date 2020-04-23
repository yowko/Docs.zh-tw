---
title: 套用中文切換覆蓋元素
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 8d5cd73bb9393533cb669581420e24297cb5ff71
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102927"
---
# <a name="appcontextswitchoverrides-element"></a>\<套用中文切換覆寫>元素

定義一或多個由 <xref:System.AppContext> 類別所使用的參數，以提供新功能的退出機制。

[**\<設定>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<執行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<套用中文切換覆寫>**

## <a name="syntax"></a>語法

```xml
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`value`|必要屬性。<br /><br /> 定義一個或多個交換機名稱及其關聯的布爾值。|

### <a name="value-attribute"></a>值屬性

|值|描述|
|-----------|-----------------|
|"名稱=值"|預先定義的開關名稱及其值`true`(`false`或 。 多個開關名稱/值對由分號分隔(";")。 有關 .NET Framework 支援的預定義交換機名稱的清單,請參閱備註部分。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關執行階段初始化選項的資訊。|

## <a name="remarks"></a>備註
 從 .NET Framework`<AppContextSwitchOverrides>`4.6 開始,配置檔中的元素允許 API 調用方確定其應用是否可以利用新功能或保留與庫的早期版本的相容性。 例如,如果 API 的行為在庫的兩個版本之間發生更改`<AppContextSwitchOverrides>`,則 該元素允許該 API 的調用方選擇退出支援新功能的庫版本上的新行為。 對於在 .NET 框架中調用 API 的應用`<AppContextSwitchOverrides>`,如果應用在包含該功能的 .NET Framework 版本上運行,則該元素還可以允許應用以早期版本的 .NET Framework 為目標的調用方選擇加入新功能。

 `<AppContextSwitchOverrides>`元素`value`的屬性由一個字串組成,該字串由一個或多個分號分隔的名稱/值對組成。  每個名稱識別相容性開關,其相應的值是布爾(`true``false`或 ), 指示是否設置了該開關。 默認情況下,開關為`false`,庫提供新功能。 僅當設置開關(即其值為`true`)時,它們才提供以前的功能。 這允許庫為現有 API 提供新的行為,同時允許依賴於前一個行為的調用方退出宣告新功能。

.NET 框架支援以下交換機:

|切換名稱|描述|介紹|
|-----------------|-----------------|----------------|
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|控制 Windows 演示文稿基礎是否使用舊演算法進行控制項佈局。 如需詳細資訊，請參閱[風險降低：WPF 版面配置](../../../migration-guide/mitigation-wpf-layout.md)。|.NET Framework 4.6|
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|控制用於由包數位簽名管理器對包部件進行簽名的預設演演演算法是 SHA1 還是 SHA256。<br>由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|設置為`false`時 ,允許在啟用 FIPS 時使用 Visual Studio 使用基於 XAML 的工作流專案進行調試。 如果沒有它,將<xref:System.NullReferenceException>引發對 System 中方法的調用。|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|控制除錯器中工作流實例的校驗和是使用 MD5 還是 SHA1。 | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|控制工作流校驗和哈希是使用在 .NET 框架 4.7 ()`true`中作為預設值引入的 SHA1 演演算法,還是使用`false`在 .NET 框架 4.8 () 中作為預設值引入的預設 SHA256 演演演算法。<br>由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256。|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|控制使用便攜式 PDB 時獲取的堆疊跟蹤是否可以包括源檔和行資訊。 `false`包括源檔和行資訊;否則, `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|控制當<xref:System.Drawing.Icon><xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType>物件 具有 PNG 幀時,該方法是否引發異常。 如需詳細資訊，請參閱[風險降低：Icon 物件中的 PNG 畫面格](../../../migration-guide/mitigation-png-frames-in-icon-objects.md)。|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|確定<xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType><xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType>物件 在方法添加到集合時是否正確釋放。 `true`維護舊行為;`false`處置所有私有字體物件。 |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|控制 是否針對網路印<xref:System.Windows.Forms.PrintPreviewDialog>表機 優化了的性能。 有關詳細資訊,請參閱[列印預覽對話框控制元件概述](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md)。|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|控制是否對日本日曆時執行年份範圍檢查。 `true`強制執行年份範圍檢查,並`false`禁用它們(默認行為)。 有關詳細資訊,請參閱[使用行事曆](../../../../standard/datetime/working-with-calendars.md)。|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|控制在分析操作中是否僅識別「1」是日本日曆時代的第一年。 `true`只識別「1」;`false`以識別「1」或「甘寧」(預設行為)。 有關詳細資訊,請參閱[使用行事曆](../../../../standard/datetime/working-with-calendars.md)。|.NET Framework 4.6|
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|控制日本日曆時代的第一年在格式操作中是否表示為「1」或 Gannen。 `true`將那個時代的第一年格式化為「1」;`false`將其格式化為「甘寧」(預設行為)。 有關詳細資訊,請參閱[使用行事曆](../../../../standard/datetime/working-with-calendars.md)。|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|控制非同步操作是否不從調用線程的上下文流。 有關詳細資訊,請參閱[目前文化和當前 UI 文化跨任務流](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks)。|.NET Framework 4.6|
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|控制<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType>該方法是否嘗試僅將聲明類型與最後一個 DNS 條目匹配。 如需詳細資訊，請參閱[風險降低：X509CertificateClaimSet.FindClaims 方法](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)。|.NET Framework 4.6.1|
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|控制是否允許授權上下文.empty 返回可變物件。|.NET Framework 4.6|
|`Switch.System.IO.BlockLongPaths`|控制路徑是否長於`MAX_PATH`(260 個字<xref:System.IO.PathTooLongException>元) 引發 。 有關詳細資訊,請參閱[長路徑支援](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support)。|.NET Framework 4.6.2|
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|控制本機操作系統例程是否用於<xref:System.IO.Compression.DeflateStream>類的解壓縮。 `false`使用本機 API;`true`使用一<xref:System.IO.Compression.DeflateStream>個實作 。|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|使用反斜杠 ("")\\而不是前斜杠 ("/")<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>作為屬性中的 路徑分隔符。 有關詳細資訊,請參閱[緩解:ZipArchiveEntry.全名路徑分隔符](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)。|.NET Framework 4.6.1|
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|控制在使用<xref:System.IO.Ports.SerialPort>流創建的後台線程上引發的操作系統異常是否終止進程。|.NET Framework 4.7.1|
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|控制是否使用舊路徑規範化,<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType>以及<xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>和方法是否支援 URI 路徑。 有關詳細資訊,請參閱[緩解:路徑規範化](../../../migration-guide/mitigation-path-normalization.md)和[緩解:路徑冒號檢查](../../../migration-guide/mitigation-path-colon-checks.md)。|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|控制相等性測試是否將一個<xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType>物件的屬性與第二<xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType>個 對象的屬性進行比較。 有關詳細資訊,請參閱[成員描述符的不正確實現。](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals)|.NET Framework 4.6.2|
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|禁用證書增強金鑰使用 (EKU) 物件識別碼 (OID) 驗證。 增強金鑰使用方法 (EKU) 延伸模組是表示使用金鑰之應用程式的物件識別碼 (OID) 集合。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|禁用 TLS1.0 瀏覽器漏洞攻擊 SSL/TLS (BEAST) 緩解通過禁用使用SCH_SEND_AUX_RECORD。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|控制和<xref:System.Net.ServicePointManager?displayProperty=nameWithType><xref:System.Net.Security.SslStream?displayProperty=nameWithType>類是否可以使用 SSL 3.0 協定。 如需詳細資訊，請參閱[風險降低：TLS 通訊協定](../../../migration-guide/mitigation-tls-protocols.md)。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|關閉系統預設 TLS 版本,回復到預設值 Tls12、Tls11、Tls。|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|禁用 SslStream TLS 伺服器端警報。|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|控制為關閉 COM 互通事件中的 ByRef SafeArray 參數封`false`送回本機代碼 (`true`), 還是關閉封送回本機代碼 ( )|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |控制[DataContractJon 序列化器](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer)是否基於 ECMAScript V6 和 V8 標準化列化某些控制字元。 如需詳細資訊，請參閱[風險降低︰使用 DataContractJsonSerializer 控制字元的序列化](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|控制<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>是支援多個調整還是僅支援時區的單個調整。 如果`true`,它<xref:System.TimeZoneInfo>使用 類型來序列化和反序列化日期和時間數據;如果 ,則使用 類型對日期和時間數據進行序列化和非序列化。否則,它使用<xref:System.TimeZone>類型,不支援多個調整規則。|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|控制在<xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType>物件序列化和反序列化期間是否使用較大的陣列大小。 將此開關設置為`true`按類型(<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>如) 提高大型物件圖形的序列化和反序列化性能。 |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|控制<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29>建構函數是否使用現有物件引用設置新<xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType>物件的屬性。 如需詳細資訊，請參閱[風險降低︰ClaimsIdentity 建構函式](../../../migration-guide/retargeting/4.6.1-4.6.2.md)。|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|控制是否嘗試重用<xref:System.Security.Cryptography.AesCryptoServiceProvider>解密器引發<xref:System.Security.Cryptography.CryptographicException>。 有關詳細資訊,請參閱[AesCryptoService 提供程式解密器提供可重用的轉換](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform)。|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|控制[Csp 參數.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle)屬性的值是表示視窗句柄的記憶體位置的[IntPtr,](xref:System.IntPtr)還是視窗句柄(HWND)。 如需詳細資訊，請參閱[風險降低︰CspParameters.ParentWindowHandle 應該有 HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value)。 |.NET Framework 4.7|
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|控制在 FIPS 模式下使用託管加密類別是引發<xref:System.Security.Cryptography.CryptographicException>`true`( ) 還是相依`false`系統庫 ( ) 的實作 。|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|確定某些已簽名 CMS 操作的預設值是 SHA1 還是 SHA256。<br>由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|控制<xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType>該方法是否正確處理作業系統支援的所有命名曲線`false`( ) 或還原為舊行為。|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|確定某些已簽名XML操作的預設值是 SHA1 還是 SHA256。<br>由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|確定`TransportWithMessageCredential`安全模式是否允許具有未簽名"to"標頭的郵件。 這是一個選擇加入開關。 有關詳細資訊,請參閱[.NET 框架 4.6.1 中的執行時更改](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf)。|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|控制<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>建構函式是否引發,<xref:System.ArgumentException>如果其中一個元素`null`是 。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|確定嘗試將 X509 證書與 CSG 密鑰存儲提供程式一起引發異常。 有關詳細資訊,請參閱[WCF 傳輸安全支援使用 CNG 儲存的證書](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng)。|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|將 HTTP 傳輸與自託管服務一起使用時,將此值設置`true`為使 WCF`Connection: close`忽略將標頭添加到請求的回應標頭的應用程式。 將此值設定為`false`啟用`Connection: close`將標頭添加到回應標頭,從而導致在發送回應後關閉請求套接字。|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|處理將重新進入服務的實例限制為一次執行單個線程而導致的死鎖。|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|與`Switch.System.Net.DontEnableSchUseStrongCrypto`一起,確定 WCF 消息安全性是否使用 TLS 1.1 和 TLS 1.2。|.NET Framework 4.7 |
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|的值`false`設定預設配置以允許作業系統選擇協定。 的值`true`將預設值設置為可用的最高協定。 (也可在以前框架版本的服務分支上提供)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|確定 WCF 中 MSMQ 消息的預設消息簽名演演演算法是 SHA1 還是 SHA256。<br>由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|控制 WCF 是使用 SHA1 還是 SHA256 哈希來為命名管道生成隨機名稱。<br>由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|控制在例外訊息是空時是否引發[空參考異常](xref:System.NullReferenceException)。|.NET Framework 4.7|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|控制服務啟動時引發的異常是否傳播到<xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>方法的調用方。|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|控制實例<xref:System.Threading.Timer>是否利用大規模環境的性能改進。 如果`true`啟用了 性能改進;如果啟用了 性能改進。如果`false`(預設值),則禁用它們。|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|確定有時解碼的某些百分比編碼字元現在是否始終保持編碼。 如果`true`解碼,則它們被解碼;否則, `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|確定URI中單向字元的處理。 `true`將它們從URI中剝離;`false`保留它們並將其編碼百分比。|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |確定 Windows 演示文稿基礎在將空間`true`\*分配給 列時是否`false`應用舊演演演算法 ( ) 或新演演演算法 ( )。 如需詳細資訊，請參閱[風險降低︰方格控制項對 Star-columns 的空間配置](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns)。 |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|控制選擇器或製表符控制件在引發選擇更改的事件之前是否始終更新其所選值屬性的值。|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|確定非基於 Adorner 的選擇呈現是否<xref:System.Windows.Controls.TextBox>可<xref:System.Windows.Controls.PasswordBox>用於和控制項以防止被遮蔽的文本`false`(), 或者文本是否僅在 Adorner 圖層 ()`true`中呈現。|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|控制<xref:System.Windows.Data.Binding?displayProperty=nameWithType>類別使用不當的自訂 IList 索`true`引器`false`( ) 還是正確 ( ) 。|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|確定 DPI 更改是按系統(的`false`值為 ) 還是基於每個監視器`true`(值的值 ) 發生。|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|控制是否<xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType>關閉 ()`true``false`或開啟了在|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|確定開發人員是否需要在存在控制項文本時專門<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>處理操作。 `true`處理操作<xref:System.Windows.Forms.DomainUpDown.UpButton>;`false`和<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>操作要正確<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>同步。|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|退出退出允許自定義<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>實現安全地篩選消息的代碼,而不會在調<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>用 方法時引發異常。 如需詳細資訊，請參閱[風險降低：自訂 IMessageFilter.PreFilterMessage 實作](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。|.NET Framework 4.6.1|
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|確定當使用者從<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>嵌套<xref:System.Windows.Forms.ToolStripMenuItem>控制項打開功能表時,屬性是否返回原始程式碼管理。 `true`返回`null`,遺留行為;`false`返回原始程式碼管理。|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|控制工具提示呼叫支援是關閉 (`true`)`false`還是啟用 ( ) 啟用工具提示呼叫`Switch.UseLegacyAccessibilityFeatures`支援還需要由 定義的舊式`Switch.UseLegacyAccessibilityFeatures.2`輔助功能`Switch.UseLegacyAccessibilityFeatures.3`,並且 所有功能都已禁`false`用(設置為 )。|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|確定是否在`WM_POINTER`WPF 應用程式中啟用了可選的基於觸摸/手寫的堆疊。 有關詳細資訊,請參閱[緩解:基於指標的觸摸和手寫筆支援](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|確定用於校驗和的預設哈希演演演算法是 SHA256 (`false`) 還是`true`SHA1 ()。<br>由於 SHA1 的衝突問題，Microsoft 建議使用 SHA256。|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|控制是否引發舊版[NullReferenceException,](xref:System.NullReferenceException)而不是更具體地指示異常原因的異常(如[目錄未找到 Exception](xref:System.IO.DirectoryNotFoundException)或[File NotFoundexception](xref:System.IO.FileNotFoundException))。 它供依賴於處理[Nullreferenceexception](xref:System.NullReferenceException)的代碼使用。 | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|控制工作流專案生成中 XOML 檔的校驗和哈希是使用`true`MD5 演演演算法 (),還是使用在 .NET 框架 4.8 中作為預設值引入的 SHA256 演演演算法。<br>由於 MD5 的衝突問題，Microsoft 建議使用 SHA256。|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|控制 SqlTrackIngService 的驗證和哈希是使用 MD5`true`演演演算法 ( ) 進行快取的字串,還是使用作為 .NET 框架 4.8 中的預設值引入的 SHA256 演演演算法。<br>由於 MD5 的衝突問題，Microsoft 建議使用 SHA256。|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|控制工作流執行時的校驗和哈希是使用 MD5`true`演演演算法 ( ) 進行緩存的工作流定義,還是使用作為 .NET 框架 4.8 中的預設值引入的 SHA256 演演演算法。<br>由於 MD5 的衝突問題，Microsoft 建議使用 SHA256。|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|控制以 .NET 框架 4.7.1 開頭的可用輔助功能是啟用還是禁用。 | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|控制 .NET 架構 4.7.2 中`false`可用的輔助`true`功能 是開啟 ( ) 還是關閉 ( 。 `Switch.UseLegacyAccessibilityFeatures`如果`true`還必須`true`啟用 .NET 框架 4.7.1 輔助功能。|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|控制 .NET 架構 4.8`false`中引入的`true`輔助 功能是啟用 ( ) 還是關閉 ( 。 如果`true``Switch.UseLegacyAccessibilityFeatures``Switch.UseLegacyAccessibilityFeatures.2`, 也`true`必須為 。|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|控制當使用者將滑鼠游標懸停在 WPF 控件 ()`true`上時,還是顯示工具提示,或者它們是否同時顯示在鍵盤焦點上`false`,是否通過鍵盤 快捷鍵 (,默認行為) 顯示。 對於在 .NET Framework 4.8 上執行但針對 .NET Framework 的早期版本的應用程式`Switch.UseLegacyAccessibilityFeatures`,`Switch.UseLegacyAccessibilityFeatures.2`啟用`Switch.UseLegacyAccessibilityFeatures.3`鍵盤焦點`false`和捷徑 支援都需要 將與 都設定為 。|.NET Framework 4.8|
|`Switch.System.Xml.`<br />`IgnoreEmptyKeySequences`|控制 XSD 架構驗證是否忽略複合鍵中的空鍵序列。 有關詳細資訊,請參閱[緩解:XML 架構驗證](../../../migration-guide/mitigation-xml-schema-validation.md)。|.NET Framework 4.6|

> [!NOTE]
> 還可以透過調用`AppContextSwitchOverrides``static`(在 C#`Shared`中)或 (在 Visual<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>Basic 中) 方法以程式設計方式設定交換機,而不是將元素添加到應用程式設定檔中。

 庫開發人員還可以定義自定義交換機,以允許調用方退出宣告其庫的更高版本中引入的已更改功能。 如需詳細資訊，請參閱 <xref:System.AppContext> 類別。

## <a name="switches-in-aspnet-apps"></a>ASP.NET應用中的交換器

通過將[\<>](../appsettings/add-element-for-appsettings.md)元素添加到 Web.config 檔案[\<的應用設置>](../appsettings/index.md)部分,可以將 ASP.NET 應用程式配置為使用相容性設置。

下面的範例使用`<add>`元素精靈至 Web.config`<appSettings>`檔案的檔案的項目加入兩個設定:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>範例

 下面的範例使用`AppContextSwitchOverrides`元素 定義單個應用程式相容性開`Switch.System.Globalization.NoAsyncCurrentCulture`關, 以防止區域性在非同步方法調用中跨線程流動。

```xml
<configuration>
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />
   </runtime>
</configuration>
```

 下面的範例使用`AppContextSwitchOverrides`元素 定義兩個應用程式相容性開`Switch.System.Globalization.NoAsyncCurrentCulture``Switch.System.IO.BlockLongPaths`關 和 。 分號分隔兩個名稱/值對。

```xml
<configuration>
    <runtime>
       <AppContextSwitchOverrides
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />
    </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [減輕 .NET 架構 4.6 及更高版本中的新行為](../../../migration-guide/mitigations.md)
- <xref:System.AppContext?displayProperty=nameWithType>
- [\<執行時>元素](runtime-element.md)
- [\<設定>元素](../configuration-element.md)
