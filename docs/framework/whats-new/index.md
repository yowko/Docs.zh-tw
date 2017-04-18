---
title: ".NET Framework 的新功能 | Microsoft Docs"
ms.custom: ""
ms.date: "04/07/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新功能 [.NET Framework]"
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
caps.latest.revision: 292
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 287
---
# .NET Framework 的新功能
<a name="introduction"></a>本文摘要說明重要的新功能，也改善了下列.NET Framework 版本︰  
  
 [.NET framework 4.6.2](#v462)   
 [.NET framework 4.6.1 在](#v461)   
 [.NET 2015年與.NET Framework 4.6](#v46)   
 [.NET framework 4.5.2](#v452)   
 [.NET framework 4.5.1](#v451)   
 [.NET framework 4.5](#core)  
  
 本文並不會提供每一項新功能的完整資料且內容可能會隨時變更。 一般.NET Framework 的詳細資訊，請參閱[開始](../../../docs/framework/get-started/index.md)。 支援的平台，請參閱[系統需求](../../../docs/framework/get-started/system-requirements.md)。 下載連結和安裝指示，請參閱[安裝指南](../../../docs/framework/install/guide-for-developers.md)。  
  
> [!NOTE]
>  .NET Framework 小組也會釋出外 NuGet 擴充平台支援及引入新功能，例如不可變的集合和啟用 SIMD 的向量類型的功能。 如需詳細資訊，請參閱[其他類別程式庫和 Api](../../../ml/index.xml)和[.NET Framework 和 Out-of-band 的版本](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)。 請參閱[NuGet 封裝的完整清單](http://blogs.msdn.com/b/dotnet/p/nugetpackages.aspx)的.NET Framework 中，或訂閱[我們的摘要](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/)。  
  
<a name="v462"></a>   
## <a name="introducing-the-net-framework-462"></a>.NET Framework 4.6.2 簡介  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 建置於 .NET Framework 4.6 和 4.6.1 的基礎上，加入許多新的修正和多項新功能，同時保有產品的高穩定性。  
  
### <a name="downloading-and-installing-the-net-framework-462"></a>下載和安裝 .NET Framework 4.6.2  
 您可從下列位置下載 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]：  
  
-   [.NET framework 4.6.2 Web 安裝程式](http://go.microsoft.com/fwlink/?LinkId=780597)  
  
-   [NET Framework 4.6.2 離線安裝程式](http://go.microsoft.com/fwlink/?LinkId=780601)  
  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 可以安裝在 Windows 10、Windows 8.1、Windows 7、以及自 Windows Server 2008 R2 SP1 起的相對應伺服器平台上。 使用 Web 安裝程式或離線安裝程式都可以安裝 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]。 大部分的使用者，我們建議使用 Web 安裝程式。  
  
 您可以將目標[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]在 Visual Studio 2012 或更新版本安裝[4.6.2 的.NET Framework 開發人員套件](http://go.microsoft.com/fwlink/?LinkId=780617)。  
  
### <a name="whats-new-in-the-net-framework-462"></a>.NET Framework 4.6.2 的新功能  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 包含下列領域的新功能：  
  
-   [ASP.NET](#ASPNET462)  
  
-   [字元類別](#Strings)  
  
-   [密碼編譯](#Crypto462)  
  
-   [SqlClient](#SQLClient)  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF462)  
  
-   [Windows Workflow Foundation (WF)](#WF462)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [將 Windows Form 和 WPF 應用程式轉換成 UWP 應用程式](#UWPConvert)  
  
-   [偵錯增強功能](#Debug462)  
  
 以一份新的 Api 加入至[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]，請參閱[4.6.2 的.NET Framework API 變更](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md)GitHub 上。 為一系列的功能改良和 bug 修正的[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]，請參閱[4.6.2 的.NET Framework API 變更](http://go.microsoft.com/fwlink/?LinkId=708778)GitHub 上。  如需詳細資訊，請參閱[發表.NET Framework 4.6.2](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/) .NET 部落格中。  
  
<a name="ASPNET462"></a>   
### <a name="aspnet"></a>ASP.NET  
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，ASP.NET 會包含下列增強功能︰  
  
 **改進對資料註解，驗證程式的當地語系化的錯誤訊息的支援**  
 資料註解驗證程式可讓您藉由將一或多個屬性加入類別內容來執行驗證。 屬性的<xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName>項目定義的錯誤訊息文字，如果驗證失敗。 從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，ASP.NET 可讓您輕鬆地將錯誤訊息當地語系化。 錯誤訊息將會當地語系化，如果︰  
  
1.  <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName>所提供的驗證屬性。  
  
2.  資源檔儲存在 App_LocalResources 資料夾中。  
  
3.  當地語系化的資源檔的名稱的格式`DataAnnotation.Localization.{`*名稱*`}.resx`，其中*名稱*是格式的文化特性名稱*指定的 languageCode*`-`*國碼/地區碼*或*指定的 languageCode*。  
  
4.  資源的索引鍵名稱是指派給字串<xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName>屬性和其值是當地語系化的錯誤訊息。  
  
 例如，下列資料附註屬性定義不正確的評等的預設文化特性的錯誤訊息。  
  
```csharp  
  
public class RatingInfo  
{  
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]  
   [Display(Name = "Your Rating")]  
   public int Rating { get; set; }  
}  
  
```  
  
```vb  
  
Public Class RatingInfo  
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>  
   <Display(Name = "Your Rating")>  
   Public Property Rating As Integer = 1  
End Class  
  
```  
  
 然後，您可以建立資源檔，DataAnnotation.Localization.fr.resx 的索引鍵是錯誤訊息字串，而其值為當地語系化的錯誤訊息。 檔案必須位於`App.LocalResources`資料夾。 例如，以下是索引鍵和其值在當地語系化的法文 (fr) 語言的錯誤訊息︰  
  
|名稱|值|  
|----------|-----------|  
|等級必須是介於 1 到 10。|La 注意 doit ê 組成 entre 1 et 10。|  
  
 然後，此檔案就可以  
  
 此外，資料註解當地語系化是可延伸的。 開發人員可以藉由實作外掛他們自己的字串的當地語系化人員提供者<xref:System.Web.Globalization.IStringLocalizerProvider>當地語系化字串儲存位置以外的資源檔中的介面。  
  
 **與工作階段狀態存放區提供者的非同步支援**  
 ASP.NET 現在可允許使用工作傳回方法，搭配工作階段狀態存放區提供者，藉此可讓 ASP.NET 應用程式獲得非同步處理的延展性優勢。 若要支援非同步作業的工作階段狀態存放區提供者，ASP.NET 會包含新介面， <xref:System.Web.SessionState.ISessionStateModule?displayProperty=fullName>，繼承自<xref:System.Web.IHttpModule> ，並可讓開發人員實作自己的工作階段狀態模組和 async 工作階段存放區提供者。 介面定義如下：  
  
```csharp  
  
public interface ISessionStateModule : IHttpModule {  
    void ReleaseSessionState(HttpContext context);  
    Task ReleaseSessionStateAsync(HttpContext context);  
}  
  
```  
  
 此外， <xref:System.Web.SessionState.SessionStateUtility>類別包含兩個新方法， <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A>和<xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>，可用來支援非同步作業。  
  
 **輸出快取提供者的非同步支援**  
 從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，工作傳回方法可以用於輸出快取提供者，以提供非同步處理的延展性優勢。  實作這些方法的提供者能減少 Web 伺服器上的執行緒阻斷，並改善 ASP.NET 服務的延展性。  
  
 已新增下列 API 來支援非同步輸出快取提供者︰  
  
-   <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=fullName>類別繼承自<xref:System.Web.Caching.OutputCacheProvider?displayProperty=fullName> ，並可讓開發人員實作非同步的輸出快取提供者。  
  
-   <xref:System.Web.Caching.OutputCacheUtility>類別，可提供用於設定輸出快取的 helper 方法。  
  
-   18 中的新方法<xref:System.Web.HttpCachePolicy?displayProperty=fullName>類別。 這些包括<xref:System.Web.HttpCachePolicy.GetCacheability%2A>， <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>， <xref:System.Web.HttpCachePolicy.GetETag%2A>， <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>， <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>， <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>， <xref:System.Web.HttpCachePolicy.GetNoStore%2A>， <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>， <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>， <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>， <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>， <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>， <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>， <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>，和<xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>。  
  
-   2 的新方法<xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=fullName>類別︰ <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A>和<xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>。  
  
-   2 的新方法<xref:System.Web.HttpCacheVaryByHeaders?displayProperty=fullName>類別︰ <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A>和<xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>。  
  
-   2 的新方法<xref:System.Web.HttpCacheVaryByParams?displayProperty=fullName>類別︰ <xref:System.Web.HttpCacheVaryByParams.GetParams%2A>和<xref:System.Web.HttpCacheVaryByParams.SetParams%2A>。  
  
-   在<xref:System.Web.Caching.AggregateCacheDependency?displayProperty=fullName>類別， <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A>方法。  
  
-   在<xref:System.Web.Caching.CacheDependency>、 <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A>方法。  
  
<a name="Strings"></a>   
### <a name="character-categories"></a>字元類別  
 在字元[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]根據分類[Unicode 標準的版本 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/)。 在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 和 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，字元是根據 Unicode 6.3 字元類別分類。  
  
 支援 Unicode 8.0 限於由字元分類<xref:System.Globalization.CharUnicodeInfo>類別和型別和方法，依賴此功能。 這些包括<xref:System.Globalization.StringInfo>類別中，多載<xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>方法，而[字元類別](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)辨識的.NET Framework 規則運算式引擎。  字元和字串比較和排序不會受到這項變更的影響，並且會繼續依賴基礎作業系統，在 Windows 7 系統上則是依賴 .NET Framework 所提供的字元資料。  
  
 從 Unicode 6.0 至 Unicode 7.0 的字元類別中的變更，請參閱[Unicode 標準、 版本 7.0.0](http://www.unicode.org/versions/Unicode7.0.0/) ，Unicode 協會網站。 Unicode 8.0 Unicode 7.0 變更，請參閱[Unicode 標準、 版本 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) ，Unicode 協會網站。  
  
<a name="Crypto462"></a>   
### <a name="cryptography"></a>加密  
 **支援的 X509 憑證包含 FIPS 186 3 DSA**  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 新增了對 DSA (數位簽章演算法) X509 憑證的支援，X509 憑證的金鑰超過 FIPS 186-2 1024 位元的限制。  
  
 除了支援較大的 FIPS 186-3 金鑰大小，[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 也允許使用 SHA-2 系列雜湊演算法 (SHA256、SHA384 及 SHA512) 運算簽章。 FIPS 186 3 提供的支援新<xref:System.Security.Cryptography.DSACng?displayProperty=fullName>類別。  
  
 為了保持最新變更<xref:System.Security.Cryptography.RSA>類別在.NET Framework 4.6 和<xref:System.Security.Cryptography.ECDsa>類別在.NET Framework 4.6.1 在<xref:System.Security.Cryptography.DSA>抽象基底類別中的[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]有其他方法可以讓呼叫者使用這項功能，而不用轉型。 您可以呼叫<xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=fullName>擴充方法，以簽署資料，如下列範例所示。  
  
```csharp  
  
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPrivateKey())  
    {  
        return dsa.SignData(data, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```vb  
  
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()  
    Using DSA As DSA = cert.GetDSAPrivateKey()  
        Return DSA.SignData(data, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 然後您就可以呼叫<xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=fullName>擴充方法，以確認簽署的資料，如下列範例所示。  
  
```csharp  
  
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPublicKey())  
    {  
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```  
  
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean  
    Using dsa As DSA = cert.GetDSAPublicKey()  
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 **輸入 ECDiffieHellman 金鑰衍生常式更的清楚**  
 .NET Framework 3.5 以三個不同的金鑰衍生函式 (KDF) 常式，新增了對 Ellipic 曲線 Diffie-hellman 金鑰協定的支援。 透過屬性上設定的輸入常式，以及本身的常式<xref:System.Security.Cryptography.ECDiffieHellmanCng>物件。 但由於不是每個常式都會讀取每個輸入屬性，所以很有可能對過去的開發人員造成混淆。  
  
 若要解決這個問題在[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]，已加入下列三種方法<xref:System.Security.Cryptography.ECDiffieHellman>基底類別，以更清楚地表示這些 KDF 常式和其輸入︰  
  
|ECDiffieHellman 方法|描述|  
|----------------------------|-----------------|  
|[DeriveKeyFromHash (ECDiffieHellmanPublicKey，HashAlgorithmName，位元組\[\]，位元組\<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|使用公式衍生金鑰內容<br /><br /> HASH(secretPrepend ||*x* | | secretAppend)<br /><br /> 雜湊 (secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> 其中*x*是 EC Diffie-hellman 演算法的計算的結果。|  
|[DeriveKeyFromHmac (ECDiffieHellmanPublicKey，HashAlgorithmName，位元組\[\]，位元組\[\]，位元組\<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|使用公式衍生金鑰內容<br /><br /> HMAC (hmacKey，secretPrepend | |*x* | | secretAppend)<br /><br /> HMAC (hmacKey，secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> 其中*x*是 EC Diffie-hellman 演算法的計算的結果。|  
|[DeriveKeyTls (ECDiffieHellmanPublicKey、 位元組\[\]，位元組\<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|使用 TLS 虛擬隨機函式 (PRF) 衍生演算法衍生金鑰內容。|  
  
 **保存金鑰的對稱式加密的支援**  
 Windows 密碼編譯程式庫 (CNG) 新增了對儲存必要對稱金鑰和使用硬體儲存之對稱金鑰的支援，[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 讓開發人員可以利用這項功能。  由於金鑰名稱和金鑰提供者的概念是因實作而定，使用此功能需要使用實體實作類型的建構函式，而不是慣用的 factory 方法 (例如呼叫 `Aes.Create`)。  
  
 保存金鑰的對稱加密支援存在 aes (<xref:System.Security.Cryptography.AesCng>) 及 3DES (<xref:System.Security.Cryptography.TripleDESCng>) 演算法。 例如：  
  
```csharp  
  
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)  
{  
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))  
    {  
        aes.IV = iv;  
  
        // Using the zero-argument overload is required to make use of the persisted key  
        using (ICryptoTransform encryptor = aes.CreateEncryptor())  
        {  
            if (!encryptor.CanTransformMultipleBlocks)  
            {  
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");  
            }  
  
            return encryptor.TransformFinalBlock(data, 0, data.Length);  
        }  
    }  
}  
  
```  
  
```vb  
  
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()  
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)  
        Aes.IV = iv  
  
        ' Using the zero-argument overload Is required to make use of the persisted key  
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()  
            If Not encryptor.CanTransformMultipleBlocks Then  
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")  
            End If  
            Return encryptor.TransformFinalBlock(data, 0, data.Length)  
        End Using  
    End Using  
End Function  
  
```  
  
 **SignedXml 支援 sha-2 雜湊**  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]新增到支援<xref:System.Security.Cryptography.Xml.SignedXml> RSA SHA256、 RSA SHA384 和 RSA SHA512 PKCS&#1; 的簽章方法和 SHA256、 SHA384 及 SHA512 參照類別摘要演算法。  
  
 URI 的常數會公開在<xref:System.Security.Cryptography.Xml.SignedXml>:  
  
|SignedXml 欄位|常數|  
|---------------------|--------------|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|  
  
 任何已註冊自訂的程式<xref:System.Security.Cryptography.SignatureDescription>到處理常式<xref:System.Security.Cryptography.CryptoConfig>加入支援這些演算法將會繼續運作一樣在過去，但是因為有現在平台會依預設，<xref:System.Security.Cryptography.CryptoConfig>不再需要註冊。  
  
<a name="SQLClient"></a>   
### <a name="sqlclient"></a>SqlClient  
 SQL Server 的.NET framework 資料提供者 (<xref:System.Data.SqlClient?displayProperty=fullName>) 包含下列新功能，在[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]:  
  
 **連接共用和逾時與 Azure SQL 資料庫**  
 如果啟用連接共用且發生逾時或其他登入錯誤，則會快取例外狀況，而在接下來的 5 秒到 1 分鐘，任何後續連接嘗試都會擲回快取的例外狀況。  如需詳細資訊，請參閱[SQL Server 連接共用 (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。  
  
 連接到 Azure SQL 資料庫時，這個行為並不理想，因為連接嘗試可能會因暫時性錯誤而失敗，但暫時性錯誤通常很快就可復原。 為了進一步最佳化連接重試的經驗，在 Azure SQL 資料庫連接失敗時，已移除連接集區封鎖期間行為。  
  
 新增 `PoolBlockingPeriod` 關鍵字可讓您選取最適合您應用程式的封鎖期間。 這些價值包括：  
  
 `Auto`  
 對於連接 Azure SQL 資料庫的應用程式，已停用連接集區封鎖期間，而對於連接任何其他 SQL Server 執行個體的應用程式，已啟用連接集區封鎖期間。 此為預設值。 如果伺服器端點名稱結尾是下列任一項，則會視為 Azure SQL 資料庫︰  
  
-   .database.windows.net  
  
-   .database.chinacloudapi.cn  
  
-   .database.usgovcloudapi.net  
  
-   .database.cloudapi.de  
  
 `AlwaysBlock`  
 一律啟用連接集區的封鎖期間。  
  
 `NeverBlock`  
 一律停用連接集區的封鎖期間。  
  
 **增強功能一律加密**  
 SQLClient 導入了兩項一律加密的增強功能︰  
  
-   為了改善對加密資料庫資料行的參數化查詢效能，現在會快取查詢參數的加密中繼資料。 使用<xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=fullName>屬性設定為`true`（此為預設值），如果相同的查詢會多次呼叫，用戶端參數中繼資料從伺服器擷取一次。  
  
-   資料行加密金鑰的項目索引鍵的快取中可設定的時間間隔，使用設定之後立即收回<xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=fullName>屬性。  
  
<a name="WCF"></a>   
### <a name="windows-communication-foundation"></a>Windows Communication Foundation  
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，Windows Communication Foundation 已在下列領域增強︰  
  
 **儲存使用 CNG 憑證的 WCF 傳輸安全性支援**  
 WCF 傳輸安全性支援使用 Windows 密碼編譯程式庫 (CNG) 儲存的憑證。 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，這項支援僅限於使用具有公開金鑰的憑證，且指數長度不能超過 32 位元。 當應用程式以 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 為目標時，這項功能預設為開啟。  
  
 目標的應用程式的[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]以及舊版，但所執行的[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]，會啟用這項功能，請加入下列這一行至[ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config 或 web.config 檔案的區段。  
  
```xml  
  
<AppContextSwitchOverrides  
    value="Switch.System.ServiceModel.DisableCngCertificates=false"  
/>  
  
```  
  
 這也可以用程式設計方式，以如下的程式碼完成︰  
  
```csharp  
  
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";  
AppContext.SetSwitch(disableCngCertificates, false);  
  
```  
  
```vb  
  
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"  
AppContext.SetSwitch(disableCngCertificates, False)  
  
```  
  
 **更好的支援由 DataContractJsonSerializer 類別的多個日光節約時間調整規則**  
 客戶可以使用應用程式組態設定來判斷是否<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>類別支援多項調整規則的單一的時區。 這是一項選擇性功能。 若要啟用它，請將下列設定加入您的 app.config 檔︰  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />  
</runtime>  
  
```  
  
 啟用這項功能時， <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>物件會使用<xref:System.TimeZoneInfo>型別而非<xref:System.TimeZone>要還原序列化的日期和時間資料型別。 <xref:System.TimeZoneInfo>支援多項調整規則，可讓您能夠使用歷史時區資料;  <xref:System.TimeZone>則否。  
  
 如需有關<xref:System.TimeZoneInfo>結構和時區調整，請參閱[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)。  
  
 **支援保留 UTC 時間序列化和還原序列化使用 XMLSerializer 類別**  
 通常，當<xref:System.Xml.Serialization.XmlSerializer>類別用來序列化 UTC <xref:System.DateTime>值，它會建立保留的日期和時間，但假設時間為本機的序列化字串。  例如，如果您藉由呼叫下列程式碼，執行個體化 UTC 日期和時間︰  
  
```csharp  
DateTime utc = new DateTime(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc);  
```  
  
```vb  
Dim utc As New Date(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc)  
```  
  
 針對時間晚於 UTC 八小時的系統而言，結果是序列化時間字串 "03:00:00.0000000-08:00"。  序列化值一律會還原序列化為本機日期和時間值。  
  
 您可以使用應用程式組態設定來判斷是否<xref:System.Xml.Serialization.XmlSerializer>會保留 UTC 時區資訊，當序列化和還原序列化<xref:System.DateTime>值︰  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides   
          value="Switch.System.Runtime.Serialization.DisableSerializeUTCDateTimeToTimeAndDeserializeUTCTimeToUTCDateTime=false" />  
</runtime>  
  
```  
  
 啟用這項功能時， <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>物件會使用<xref:System.TimeZoneInfo>型別而非<xref:System.TimeZone>要還原序列化的日期和時間資料型別。 <xref:System.TimeZoneInfo>支援多項調整規則，可讓您能夠使用歷史時區資料;  <xref:System.TimeZone>則否。  
  
 如需有關<xref:System.TimeZoneInfo>結構和時區調整，請參閱[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)。  
  
 **NetNamedPipeBinding 最符合項目**  
 WCF 有新的應用程式設定，可以在用戶端應用程式上設定，以確保它們永遠連接至在最符合要求的 URI 上接聽的服務。 使用此應用程式設定設為`false`（預設值），則可能會使用用戶端<xref:System.ServiceModel.NetNamedPipeBinding>來嘗試連接到服務接聽的 URI 的要求 URI 的子字串。  
  
 例如，用戶端嘗試連接到接聽 `net.pipe://localhost/Service1` 的服務，但該電腦上以系統管理員權限執行的不同服務正在接聽 `net.pipe://localhost`。 當此應用程式設定設為 `false` 時，用戶端會嘗試連接到錯誤的服務。 將應用程式設定設為 `true` 後，用戶端一律都會連接至最符合的服務。  
  
> [!NOTE]
>  使用用戶端<xref:System.ServiceModel.NetNamedPipeBinding>尋找根據服務的基底位址 （如果存在的話） 而不是完整的端點位址的服務。 為了確保此設定一律適用，服務應該使用唯一的基底位址。  
  
 若要啟用這項變更，請先將下列應用程式設定加入用戶端應用程式的 App.config 或 Web.config 檔︰  
  
```xml  
  
<configuration>  
    <appSettings>  
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />  
    </appSettings>  
</configuration>  
  
```  
  
 **SSL 3.0 不是預設的通訊協定**  
 當使用 NetTcp 搭配傳輸安全性和憑證類型的認證時，SSL 3.0 已不再是用來交涉安全連接的預設通訊協定。 在大部分情況下，應該不會影響現有的應用程式，因為 TLS 1.0 已包含在 NetTcp 的通訊協定清單中。 所有現有的用戶端應該能夠使用至少 TLS 1.0 來交涉連接。      如果需要 SSL3，請使用下列組態機制之一，將它加入交涉通訊協定的清單。  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName>屬性  
  
-   <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName>屬性  
  
-   The [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) section of the [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) section  
  
-   The [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) section of the [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) section  
  
<a name="WPF462"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，Windows Presentation Foundation 已在下列領域增強︰  
  
 **群組排序**  
 使用的應用程式<xref:System.Windows.Data.CollectionView>來分組資料的物件現在可以明確地宣告如何排序群組。 明確排序可以解決非直覺式排序的問題，此問題發生於應用程式以動態方式新增或移除群組時，或是變更分組時所干涉的項目屬性值時。 它也可以藉由將分組屬性的比較從完整集合排序移至群組排序，改善群組建立程序的效能。  
  
 若要支援排序的群組，新<xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=fullName>和<xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=fullName>屬性會描述如何排序群組所產生的集合<xref:System.ComponentModel.GroupDescription>物件。 這相當於相同具名方法<xref:System.Windows.Data.ListCollectionView>屬性會描述如何排序資料的項目。  
  
 兩個新的靜態屬性的<xref:System.Windows.Data.PropertyGroupDescription>類別， <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A>和<xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>，可用於大部分的案例。  
  
 比方說，下列 XAML 會依年齡將資料分組、以遞增順序排序年齡群組，並依據姓氏將每個年齡群組內項目分組。  
  
```xaml  
  
<GroupDescriptions>  
     <PropertyGroupDescription   
         PropertyName=”Age”   
         CustomSort=   
              ”{x:Static PropertyGroupDescription.CompareNamesAscending}”/>  
     </PropertyGroupDescription>  
</GroupDescriptions>  
  
<SortDescriptions>  
     <SortDescription PropertyName=”LastName”/>  
</SortDescriptions>  
  
```  
  
 **螢幕小鍵盤支援**  
 螢幕小鍵盤支援可以啟用 WPF 應用程式中的焦點追蹤，方法是當可接受文字輸入的控制項觸控收到輸入時，自動叫用及關閉 Windows 10 中新的螢幕小鍵盤。  
  
 在舊版的 .NET Framework 中，WPF 應用程式必須停用 WPF 畫筆/觸控筆勢支援，才能參加焦點追蹤。  如此一來，WPF 應用程式必須選擇完整 WPF 觸控支援，或是依賴 Windows 滑鼠升級。  
  
 **每個監視器 DPI**  
 為了針對 WPF 應用程式支援最近激增的高 DPI 和混合式 DPI 環境，[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 啟用了個別監視器感知。 請參閱[範例和開發人員指南](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI)如需有關如何啟用您的 WPF 應用程式成為每個監視器 DPI 感知的 GitHub 上。  
  
 在舊版 .NET Framework 中，WPF 應用程式是系統 DPI 感知。 換句話說，應用程式的 UI 會由作業系統進行適當的縮放，視應用程式呈現所在的監視器 DPI 而定。 ,  
  
 在執行的應用程式[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]，可以加入組態陳述式，來停用 WPF 應用程式中的每個監視器 DPI 變更[ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)下列區段的應用程式組態檔︰  
  
```xml  
  
<runtime>  
   <AppContextSwitchOverrides value=”Switch.System.Windows.DoNotScaleForDpiChanges=false”/>  
</runtime>  
  
```  
  
<a name="WF462"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 中，Windows Workflow Foundation 已在下列領域增強︰  
  
 **C# 運算式和 Re-hosted WF 設計工具中的 IntelliSense 支援**  
 從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，WF 在 Visual Studio 設計工具和程式碼工作流程中都支援 C# 運算式。 Re-hosted 工作流程設計工具是 WF 的重要功能，可讓工作流程設計工具位於 Visual Studio 以外的應用程式中 (例如 WPF 中)。  Windows Workflow Foundation 提供在 Re-hosted 工作流程設計工具中支援 C# 運算式與 IntelliSense 的功能。 如需詳細資訊，請參閱[Windows Workflow Foundation 部落格](http://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409)。  
  
 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`  
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 之前的 .NET framework 版本中，當客戶從 Visual Studio 重建工作流程專案時，WF 設計工具 IntelliSense 便會中斷。 在專案建置為成功、 在設計工具中，找不到工作流程類型從 IntelliSense 為遺漏的工作流程類型的警告會出現在**錯誤清單**視窗。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 解決了這個問題，並提供 IntelliSense。  
  
 **FIPS 模式下執行的工作流程 V1 應用程式與工作流程追蹤正在播放的節目**  
 啟用 FIPS 相容性模式的電腦，現在可以順利執行工作流程 V1 樣式的應用程式，並開啟工作流程追蹤。 若要啟用這種情況，您必須在 app.config 檔案中進行下列變更︰  
  
```xml  
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />  
```  
  
 如果未啟用這種情況，執行應用程式會繼續產生例外狀況，訊息為：「此實作不屬於 Windows Platform FIPS 已驗證密碼編譯演算法的一部分。」  
  
 **使用 Visual Studio 工作流程設計工具中使用動態更新時的工作流程改進功能**  
 工作流程設計工具、 流程圖活動設計工具，以及其他工作流程活動設計工具現在已成功載入和顯示已儲存在呼叫工作流程<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=fullName>方法。 在之前的.NET Framework 的版本[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]，載入已儲存在呼叫工作流程在 Visual Studio 中的 XAML 檔案<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=fullName>可能會導致下列問題︰  
  
-   工作流程設計工具無法正確載入 XAML 檔案 (當<xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=fullName>在一行的結尾)。  
  
-   流程圖活動設計工具或其他工作流程活動設計工具可能會在預設位置顯示所有物件，而不是根據附加的屬性值。  
  
<a name="ClickOnce"></a>   
### <a name="clickonce"></a>ClickOnce  
 ClickOnce 已更新為除了已經支援的 TLS 1.0 通訊協定之外，還支援 TLS 1.1 和 TLS 1.2。 ClickOnce 會自動偵測需要哪個通訊協定。若要啟用 TLS 1.1 和 1.2 支援，並不需要在 ClickOnce 應用程式中執行額外的步驟。  
  
<a name="UWPConvert"></a>   
### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>將 Windows Form 和 WPF 應用程式轉換成 UWP 應用程式  
 Windows 現在提供將現有 Windows 桌面應用程式，包括 WPF 和 Windows Form 應用程式，帶到通用 Windows 平台 (UWP) 的功能。 這項技術可作為橋樑，讓您能逐漸將現有的程式碼基底移轉到 UWP，從而將您的應用程式帶到所有 Windows 10 裝置。  
  
 轉換後的桌面應用程式會取得類似於 UWP 應用程式的應用程式識別，如此便可存取 UWP API，以啟用例如動態磚和通知等功能。 應用程式會繼續和之前一樣運作，而且會以完全信任應用程式執行。 應用程式轉換後，應用程式容器處理序可以加入現有的完全信任處理序，以新增調適性使用者介面。 當所有的功能都移至應用程式容器處理序時，便可以移除完全信任處理序，新的 UWP 應用程式也可以供所有 Windows 10 裝置使用。  
  
<a name="Debug462"></a>   
### <a name="debugging-improvements"></a>偵錯改進  
 *Unmanaged 偵錯 API*增強過[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]執行其他分析時<xref:System.NullReferenceException> ，就可以判斷在單行程式碼中的變數就會擲回`null`。   為了支援這種情況，下列 API 已加入 Unmanaged 偵錯 API。  
  
-   [ICorDebugCode4](../../../ocs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)， [ICorDebugVariableHome](../../../ocs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)，和[ICorDebugVariableHomeEnum](../../../ocs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)公開 managed 變數原生住家的介面。 這可讓偵錯工具執行某些程式碼流程分析時<xref:System.NullReferenceException>發生用於與舊版來判斷受管理的變數對應至原生的位置`null`。  
  
-   [ICorDebugType2::GetTypeID](../Topic/ICorDebugType2::GetTypeID%20Method.md)方法提供對應至 ICorDebugType [COR_TYPEID](../../../ocs/framework/unmanaged-api/debugging/cor-typeid-structure.md)，可讓偵錯工具取得[COR_TYPEID](../../../ocs/framework/unmanaged-api/debugging/cor-typeid-structure.md)沒有 ICorDebugType 的執行個體。 上的現有 Api [COR_TYPEID](../../../ocs/framework/unmanaged-api/debugging/cor-typeid-structure.md)然後可以用來判斷型別的類別配置。  
  
<a name="v461"></a>   
## <a name="whats-new-in-the-net-framework-461"></a>.NET Framework 4.6.1 的新功能  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 包含下列領域的新功能：  
  
-   [密碼編譯](#Crypto)  
  
-   [ADO.NET](#ADO.NET461)  
  
-   [Windows Presentation Foundation (WPF)](#WPF461)  
  
-   [Windows Workflow Foundation](#WWF461)  
  
-   [程式碼剖析](#Profile461)  
  
-   [NGen](#NGEN461)  
  
 如需 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 的詳細資訊，請參閱下列主題：  
  
-   [.NET Framework 4.6.1 在清單中的變更](http://go.microsoft.com/fwlink/?LinkId=622964)  
  
-   [4.6.1 在應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)  
  
-   [.NET Framework API 差異](http://go.microsoft.com/fwlink/?LinkId=622989)（在 GitHub)  
  
<a name="Crypto"></a>   
### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>密碼編譯：支援包含 ECDSA 的 X509 憑證  
 加入 X509 憑證 RSACng 支援的 .NET Framework 4.6。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 加入了 ECDSA (橢圓曲線數位簽章演算法) X509 憑證的支援。  
  
 ECDSA 提供較佳的效能，其密碼編譯演算法比 RSA 更安全，為傳輸層安全性 (TLS) 的效能和延展性提供了絕佳的選擇。 .NET Framework 實作會將呼叫包裝在現有的 Windows 功能中。  
  
 下列範例程式碼示範使用 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 包含的 ECDSA X509 憑證新支援，產生位元組資料流的簽章是多麼的輕鬆。  
  
 [!code-csharp[whatsnew.461.crypto#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
 [!code-vb[whatsnew.461.crypto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]  
  
 這為所需的程式碼提供標記的對比，以在 .NET Framework 4.6 中產生簽章。  
  
 [!code-csharp[whatsnew.461.crypto#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
 [!code-vb[whatsnew.461.crypto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]  
  
<a name="ADO.NET461"></a>   
### <a name="adonet"></a>ADO.NET  
 下列項目已加入 ADO.NET：  
  
 硬體保護金鑰的「一律加密」支援  
 ADO.NET 現在支援在硬體安全模組 (HSM) 中原有的儲存「一律加密」資料行主要金鑰。 透過這項支援，客戶不需要撰寫自訂的資料行主要金鑰存放區提供者，也不要向應用程式註冊，即可以使用儲存在 HSM 的非對稱金鑰。  
  
 客戶必須在應用程式伺服器或用戶端電腦上安裝 HSM 廠商提供的 CSP 提供者或 CNG 金鑰存放區提供者，才能存取受到儲存在 HSM 之資料行主要金鑰保護的「一律加密」資料。  
  
 改善<xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> alwayson 連接行為  
 SqlClient 現在會自動提供更快的 AlwaysOn 可用性群組 (AG) 連線。 它會明確偵測應用程式是否連接到不同子網路上的 AlwaysOn 可用性群組 (AG)，並快速找到目前使用中的伺服器和提供伺服器連線。 在此版本之前，應用程式必須設定連接字串包含 `“MultisubnetFailover=true”`，以表示它要連接到 AlwaysOn 可用性群組。 如果不在 `true` 設定連接關鍵字，應用程式可能會在連接到 AlwaysOn 可用性群組時發生逾時狀況。 此版本中，應用程式會*不*需要設定<xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>至`true`淪陷了。 如需 SqlClient 對於 Alwayson 可用性群組支援的詳細資訊，請參閱[高可用性、 嚴重損壞修復的 SqlClient 支援](../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md)。  
  
<a name="WPF461"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 Windows Presentation Foundation 包含數項改進和變更。  
  
 提升效能  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 已修正了引發觸控事件的延遲。 此外，在輸入<xref:System.Windows.Controls.RichTextBox>控制項不會佔用呈現執行緒期間快速輸入。  
  
 改善拼字檢查  
 Windows 8.1 和更新版本已更新了 WPF 的拼字檢查程式，運用作業系統支援其他語言的拼字檢查。  Windows 8.1 之前的 Windows 版本功能沒有任何變更。  
  
 就如同舊版的.NET Framework 的語言<xref:System.Windows.Controls.TextBox>控制這個<xref:System.Windows.Controls.RichTextBox>區塊偵測到的尋找以下列順序的資訊︰  
  
-   `xml:lang` (如有)。  
  
-   目前的輸入語言。  
  
-   目前的執行緒文化特性。  
  
 如需有關在 WPF 中的語言支援的詳細資訊，請參閱[WPF 在.NET Framework 4.6.1 在功能上的部落格文章](http://go.microsoft.com/fwlink/?LinkID=691819)。  
  
 每個使用者自訂字典的額外支援  
 在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 中，WPF 能夠辨識已全域註冊的自訂字典。 這是除了依照每個控制項登錄它們之外的可用功能。  
  
 在舊版的 WPF 中，自訂的字典無法辨識 [已排除單字] 和 [自動校正] 清單。 Windows 8.1 和 Windows 10 透過可置於 `%AppData%\Microsoft\Spelling\<language tag>` 目錄之下使用的檔案支援它們。  下列規則適用於這些檔案：  
  
-   檔案應有副檔名：.dic (用於加入的字詞)、.exc (用於排除的字詞) 或 .acl (用於自動校正)。  
  
-   檔案應為以位元組順序標記 (BOM) 開始的 UTF-16 LE 純文字。  
  
-   每一行應該包含的單字 （以加入和排除的字詞清單），或以分隔號分隔的字樣的自動校正配對 ("|")（在 自動校正字清單）。  
  
-   系統視這些檔案為唯讀，而且不會加以修改。  
  
> [!NOTE]
>  WPF 拼字檢查應用程式開發介面不直接支援這些新的檔案格式，而應用程式中向 WPF 提供的自訂字典應該繼續使用 .lex 檔案。  
  
 範例  
 有許多[WPF 範例](https://msdn.microsoft.com/library/ms771633.aspx)MSDN 上。 超過 200 個最受歡迎的範例 （根據其使用方式） 將被移到[開啟來源 GitHub 儲存機制](https://github.com/Microsoft/WPF-Samples)。 協助我們改進我們的範例，請傳送提取要求或開啟[GitHub 問題](https://github.com/Microsoft/WPF-Samples/issues)。  
  
 DirectX 擴充功能  
 WPF 包含[nuget](http://go.microsoft.com/fwlink/?LinkID=691342)所提供的新實作<xref:System.Windows.Interop.D3DImage> ，方便您使用 DX10 和支援 Dx11 交互操作內容。 此程式碼已開啟此封裝取得資料來源並使用[GitHub 上](https://github.com/Microsoft/WPFDXInterop)。  
  
<a name="WWF461"></a>   
### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation：教學課程  
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=fullName>方法現在可以使用 MSDTC 以外的分散式的交易管理員來將交易升級。 您可以指定新的 GUID 交易 promoter 識別碼<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=fullName>多載。 如果這項作業成功，交易的功能上就會放置一些限制。 一旦已登錄非 MSDTC 交易 promoter，下列方法會擲回<xref:System.Transactions.TransactionPromotionException>因為這些方法需要升級至 MSDTC:  
  
-   <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=fullName>  
  
-   <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=fullName>  
  
-   <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=fullName>  
  
-   <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=fullName>  
  
 一旦登錄了非 MSDTC 的交易升級程式，即必須使用它定義的通訊協定，將它用於未來的永久性登錄。 <xref:System.Guid>可以使用來取得交易的 promoter <xref:System.Transactions.Transaction.PromoterType%2A>屬性。 當交易升級，提供交易 promoter<xref:System.Byte>陣列，表示已升級的語彙基元。 應用程式可以取得非 MSDTC 升級交易的升級語彙基元<xref:System.Transactions.Transaction.GetPromotedToken%2A>方法。  
  
 新的使用者<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=fullName>多載必須遵循特定的呼叫序列中才能順利完成升級作業。 這些規則都會記錄在於方法的文件中。  
  
<a name="Profile461"></a>   
### <a name="profiling"></a>程式碼剖析  
 Unmanaged 程式碼剖析應用程式開發介面已增強下列項目：  
  
 更有效地支援存取 Pdb 中的[ICorProfilerInfo7](../../../ocs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)介面  
 在 ASP.Net 5 中，Roslyn 把組件編譯到記憶體中變得更加普遍。 對於製作程式碼剖析工具的開發人員，這表示過去在磁碟上序列化的 PDB 可能不再存在。 程式碼分析工具通常會使用 PDB 對應回工作原始程式行的程式碼，例如程式碼涵蓋範圍或逐行效能分析。 [ICorProfilerInfo7](../../../ocs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)介面現在包含兩個新方法︰ [ICorProfilerInfo7::GetInMemorySymbolsLength](../Topic/ICorProfilerInfo7::GetInMemorySymbolsLength%20Method.md)和[ICorProfilerInfo7::ReadInMemorySymbols](../Topic/ICorProfilerInfo7::ReadInMemorySymbols.md)，提供這些程式碼剖析工具工具存取記憶體中的 PDB 資料，藉由使用新的 Api，分析工具可以取得記憶體中 PDB，做為位元組陣列的內容，然後進行處理或序列化至磁碟。  
  
 具有 ICorProfiler 介面的更佳檢測設備  
 使用 `ICorProfiler` 應用程式開發介面的 ReJit 功能進行動態檢測的程式碼分析工具，現在可以修改某些中繼資料。 這類工具過去可以隨時檢測 IL，但只能在模組載入時修改中繼資料。 因為 IL 參考中繼資料，這會限制能夠執行的檢測種類。 我們已經提昇的一些這些限制加[ICorProfilerInfo7::ApplyMetaData](../Topic/ICorProfilerInfo7::ApplyMetaData%20Method.md)方法，以支援編輯中繼資料的子集後模組載入時，特別是藉由新增新`AssemblyRef`， `TypeRef`， `TypeSpec`， `MemberRef`， `MemberSpec`，和`UserString`記錄。 這項變更讓更大範圍的即時檢測變成可能。  
  
<a name="NGEN461"></a>   
### <a name="native-image-generator-ngen-pdbs"></a>原生映像產生器 PDB  
 跨電腦的事件追蹤可讓客戶分析電腦 A 的程式，並使用電腦 B 上對應的原始程式查看程式碼剖析資料。使用舊版的 .NET Framework 時，使用者會將所有模組和原生映像從剖析的機器複製到包含 IL PDB 的分析機器，建立來源與原生的對應。 雖然這個程序能在檔案較小時運作良好，例如手機的電話應用程式；但是，桌上型系統的檔案可能非常巨大，需要大量的複製時間。  
  
 使用 Ngen PDB，NGen 可以建立包含 IL 與原生對應的 PDB，不必依賴 IL PDB。 在我們跨機器事件的追蹤案例，只需要為複製到機器 B 的電腦 A 所產生的 PDB 的原生映像，且使用[偵錯介面存取 Api](https://msdn.microsoft.com/en-us/library/ee8x173s.aspx)讀取 IL PDB 來源-IL 對應和原生映像 PDB IL-原生對應。 結合兩個對應可提供來源與原生對應。 由於原生映像 PDB 遠小於所有模組和原生映像，電腦 A 到電腦 B 的複製程序會更快。  
  
<a name="v46"></a>   
## <a name="whats-new-in-net-2015"></a>.NET 2015 的新功能  
 .NET 2015 導入了 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 和 .NET 核心。 其中一些新功能適用於兩者，另一些功能則專屬於 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 或 [!INCLUDE[net_core](../../../includes/net-core-md.md)]。  
  
-   **ASP.NET 5**  
  
     .NET 2015 包含用於建置現代化雲端架構應用程式的簡式 .NET 平台 ASP.NET 5。 這個平台已模組化，因此您可以在應用程式中僅包含所需的功能。 這個平台可裝載於 IIS 上或自行裝載於自訂處理序中，並且您可以在同一部伺服器上執行具有不同 .NET Framework 版本的應用程式。 其中所包含的新環境組態系統是專為雲端部署所設計。  
  
     MVC、Web API 和網頁已整合成單一架構，稱為 MVC 6。 您可以透過 Visual Studio 2015 的新工具來建置 ASP.NET 5 應用程式。 您現有的應用程式可在新的 .NET Framework 上運作；不過若要建置使用 MVC 6 或 SignalR 3 的應用程式，您必須使用 Visual Studio 2015 的專案系統。  
  
     如需資訊，請參閱[ASP.NET 5](http://go.microsoft.com/fwlink/?LinkId=518238)。  
  
-   **ASP.NET 的更新**  
  
    -   **工作架構非同步回應排清的 API**  
  
         ASP.NET 現在提供簡單的工作為基礎 API 非同步回應排清， <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=fullName>，可讓使用您的語言來以非同步方式排清回應`async/await`支援。  
  
    -   `Model binding supports task-returning methods`  
  
         [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的 ASP.NET 中已加入模型繫結功能，可保障 Web Form 頁面和使用者控制項中以 CRUD 為基礎之資料作業方式的可延伸性並以程式碼為重心。 模型繫結系統現在支援<xref:System.Threading.Tasks.Task>-傳回模型繫結方法。 這項功能可讓 Web Form 開發人員在使用包括 Entity Framework 的較新版 ORM 時，透過簡單的資料繫結系統獲得非同步延展性的優勢。  
  
         非同步模型繫結是由 `aspnet:EnableAsyncModelBinding` 組態設定所控制。  
  
        ```  
  
        <appSettings>  
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />  
        </appSettings>  
  
        ```  
  
         若是目標為 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 的應用程式，它會預設為 `true`。 若是在目標為舊版 .NET Framework 但在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 上執行的應用程式，則預設為 `false`。 您可將組態設定設為 `true` 以將其啟用。  
  
    -   **HTTP/2 支援 (Windows 10)**  
  
         [HTTP/2](http://www.wikipedia.org/wiki/HTTP/2)新版的 HTTP 通訊協定，提供更好的連線使用 （用戶端與伺服器之間的較少往返），導致較低的延遲網頁載入的使用者。  網頁 (與服務相反) 從 HTTP/2 獲益最明顯，因為通訊協定會針對做為單一體驗之一部分之要求的多個成品進行最佳化。 在 .NET Framework 4.6 中，HTTP/2 支援已加入 ASP.NET。 由於網路功能存在於多個層，因此 Windows、IIS 和 ASP.NET中需要新功能以啟用 HTTP/2。 您必須在 Windows 10 上執行才能搭配 ASP.NET 使用 HTTP/2。  
  
         HTTP/2 也支援上的預設和適用於 Windows 10 的通用 Windows 平台 (UWP) 應用程式使用<xref:System.Net.Http.HttpClient?displayProperty=fullName> API。  
  
         若要提供一個方式來使用[PUSH_PROMISE](http://http2.github.io/http2-spec/#PUSH_PROMISE)功能 ASP.NET 應用程式，新的方法有兩個多載， <xref:System.Web.HttpResponse.PushPromise%28System.String%29>和<xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>，已加入至<xref:System.Web.HttpResponse>類別。  
  
        > [!NOTE]
        >  雖然 ASP.NET 5 支援 HTTP/2，但尚未加入 PUSH PROMISE 功能的支援。  
  
         瀏覽器和網頁伺服器 (Windows 上的 IIS) 會執行所有工作。 您不需要為使用者進行任何繁重工作。  
  
         大部分的[主要瀏覽器都支援 HTTP/2](http://www.wikipedia.org/wiki/HTTP/2)，因此可能您的使用者會因為 HTTP/2 支援，如果您的伺服器支援它。  
  
    -   **語彙基元繫結通訊協定的支援**  
  
         Microsoft 與 Google 合作的新驗證方法，稱為[語彙基元繫結通訊協定](https://github.com/TokenBinding/Internet-Drafts)。 前提是可以竊取驗證權杖 （在您的瀏覽器快取），並使用罪犯存取安全資源 （例如您的銀行帳戶），而不需要您的密碼或其他特殊權限的知識。 新的通訊協定旨在減輕這個問題。  
  
         語彙基元繫結通訊協定會在 Windows 10 中實作為瀏覽器功能。 ASP.NET 應用程式將會參與通訊協定，以便驗證權杖能驗證為合法。 用戶端和伺服器實作會建立通訊協定所指定的端對端保護。  
  
    -   **隨機的字串的雜湊演算法**  
  
         .NET Framework 4.5 引入[隨機的字串雜湊演算法](https://msdn.microsoft.com/library/jj152924.aspx)。 不過，由於部分 ASP.NET 功能相依於穩定的雜湊程式碼，因此 ASP.NET 並不支援此演算法。 在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中，現已支援隨機字串雜湊演算法。 若要啟用這項功能，請使用 `aspnet:UseRandomizedStringHashAlgorithm` 組態設定。  
  
        ```  
  
        <appSettings>  
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />  
        </appSettings>  
  
        ```  
  
-   **ADO.NET**  
  
     ADO.NET 現在支援 SQL Server 2016 Community Technology Preview 2 (CTP2) 提供的「一律加密」功能。 使用「一律加密」，SQL Server 可以對加密資料執行作業，而且最好的是加密金鑰是與應用程式一起位於客戶的受信任環境內，而不是伺服器上。 「一律加密」會保護客戶資料安全，因此，DBA 無法存取純文字資料。 資料的加密和解密透明地在驅動程式層級進行，以將變更現有應用程式的需求降到最少。 如需詳細資訊，請參閱[一律加密 (Database Engine)](https://msdn.microsoft.com/library/mt163865\(v=sql.130\).aspx)和[一律加密 （用戶端開發）](https://msdn.microsoft.com/library/mt147923\(v=sql.130\).aspx)。  
  
-   **managed 程式碼的&64; 位元 JIT 編譯器**  
  
     .NET Framework 4.6 提供 64 位元 JIT 編譯器的新版本 (原本的程式碼名為 RyuJIT)。 全新的 64 位元編譯器比舊版 64 位元 JIT 編譯器更大幅提升效能。 在 .NET Framework 4.6 之上執行的 64 位元處理序即會啟用全新的 64 位元編譯器。 若您的應用程式是編譯為 64 位元或 AnyCPU 並在 64 位元作業系統上執行的話，則會以 64 位元處理序執行。 雖然我們已盡量讓新編譯器的轉換透明化，但仍可能會有行為上的變更。 如果您在使用新的 JIT 編譯器遇到任何問題，歡迎您直接向我們反應。 請連絡我們透過[Microsoft Connect](http://connect.microsoft.com/)如果您遇到可能與新的 64 位元 JIT 編譯器相關的問題。  
  
     新的 64 位元 JIT 編譯器也會包含硬體 SIMD 加速功能一起使用啟用 SIMD 的類型中<xref:System.Numerics>命名空間，可產生良好的效能改進。  
  
-   **組件載入器增強功能**  
  
     現在，組件載入器會於載入對應的 NGEN 影像之後即卸載 IL 組件，因此可以更有效率地使用記憶體。 這項變更會減少虛擬記憶體，這對大型的 32 位元應用程式 (例如 Visual Studio) 特別有幫助，也可節省實體記憶體。  
  
-   **基底類別程式庫變更**  
  
     為了能夠在主要情況下使用，[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 已新增許多 API。 其中包括下列變更和新功能：  
  
    -   **IReadOnlyCollection<> \</> \>實作**  
  
         其他集合，以實作<xref:System.Collections.Generic.IReadOnlyCollection%601>例如<xref:System.Collections.Generic.Queue%601>和<xref:System.Collections.Generic.Stack%601>。  
  
    -   **CultureInfo.CurrentCulture 和 CultureInfo.CurrentUICulture**  
  
         <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>和<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>屬性現在是讀寫，而非唯讀狀態。 如果您指派新<xref:System.Globalization.CultureInfo>給這些屬性時，所定義的目前執行緒文化特性物件`Thread.CurrentThread.CurrentCulture`屬性和目前的 UI 執行緒所定義的文化特性`Thread.CurrentThread.CurrentUICulture`屬性也會變更。  
  
    -   **記憶體回收 (GC) 的增強功能**  
  
         <xref:System.GC>類別現在包含<xref:System.GC.TryStartNoGCRegion%2A>和<xref:System.GC.EndNoGCRegion%2A>方法可讓您不允許記憶體回收期間於執行關鍵路徑。  
  
         新的多載<xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=fullName>方法可讓您控制是否清理和壓縮或只要小型物件堆積和大型物件堆積。  
  
    -   **啟用 SIMD 的類型**  
  
         <xref:System.Numerics>命名空間現在包含數種啟用 SIMD 的類型，例如<xref:System.Numerics.Matrix3x2>， <xref:System.Numerics.Matrix4x4>，<xref:System.Numerics.Plane>，<xref:System.Numerics.Quaternion>， <xref:System.Numerics.Vector2>， <xref:System.Numerics.Vector3>，和<xref:System.Numerics.Vector4>。  
  
         因為新的 64 位元 JIT 編譯器也包含硬體 SIMD 加速功能，所以在搭配支援 SIMD 的類型與新的 64 位元 JIT 編譯器時有特別顯著的效能改進。  
  
    -   **密碼編譯更新**  
  
         <xref:System.Security.Cryptography?displayProperty=fullName> API 更新為支援[Windows CNG 密碼編譯 Api](https://msdn.microsoft.com/library/windows/desktop/aa376214.aspx)。 舊版的.NET Framework 有在完全依賴[舊版的 Windows 密碼編譯 Api](https://msdn.microsoft.com/library/windows/desktop/aa380255.aspx)做為基礎<xref:System.Security.Cryptography?displayProperty=fullName>實作。 我們已經要求支援 CNG API，因為它支援[現代的密碼編譯演算法](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx#suite_b_support)，這些對特定應用程式分類很重要。  
  
         .NET Framework 4.6 包含下列新的增強功能，可支援 Windows CNG 加密 API：  
  
        -   一組適用於 `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` 和 `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` x509 憑證的擴充方法，其會在可能時傳回以 CNG 為基礎的實作，而不是以 CAPI 為基礎的實作。 (有些智慧卡仍需要 CAPI，因此 API 可處理這類後援。)  
  
        -   <xref:System.Security.Cryptography.RSACng?displayProperty=fullName>類別，可提供 RSA 演算法的 CNG 實作。  
  
        -   RSA API 的增強功能，可讓一般動作不再需要轉型。 例如，加密資料使用<xref:System.Security.Cryptography.X509Certificates.X509Certificate2>物件需要如下所示，在舊版的.NET Framework 程式碼。  
  
             [!code-csharp[WhatsNew.Casting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
             [!code-vb[WhatsNew.Casting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]  
  
             您可將使用 .NET Framework 4.6 中新加密 API 的程式碼改寫如下，以避免轉型。  
  
             [!code-csharp[WhatsNew.Casting#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
             [!code-vb[WhatsNew.Casting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]  
  
    -   **進行轉換的日期和時間，或從 Unix 時間支援**  
  
         已加入下列的新方法<xref:System.DateTimeOffset>結構來支援轉換的日期和時間值，或從 Unix 時間︰  
  
        -   <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=fullName>  
  
        -   <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=fullName>  
  
        -   <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=fullName>  
  
        -   <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=fullName>  
  
    -   **相容性參數**  
  
         新<xref:System.AppContext>類別加入了新的相容性功能，可讓程式庫作者為使用者提供新功能的統一退出機制。 它會建立元件之間的鬆散結合合約，以便溝通退出要求。 變更現有的功能時，這項功能通常會特別重要。 相反地，已經有新功能的隱含選擇加入。  
  
         使用<xref:System.AppContext>、 程式庫會定義並公開相容性參數，而依賴它們的程式碼可以設定這些參數來影響程式庫行為。 根據預設，程式庫可提供新的功能，且它們只會在已設定此參數時變更它 (亦即，它們提供先前的功能)。  
  
         應用程式 （或程式庫） 可以宣告參數的值 (一律為<xref:System.Boolean>值) 的相依程式庫定義。 參數一律隱含為 `false`。 將參數設定為 `true` 可啟用它。 明確地將參數設定為 `false` 提供了新的行為。  
  
        ```csharp  
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);  
        ```  
  
         程式庫必須檢查取用者是否已宣告參數的值，然後適當地處理它。  
  
        ```  
  
        if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))   
        {  
           // This is the case where the switch value was not set by the application.   
           // The library can choose to get the value of shouldThrow by other means.   
           // If no overrides nor default values are specified, the value should be 'false'.   
           // A false value implies the latest behavior.  
        }  
  
           // The library can use the value of shouldThrow to throw exceptions or not.  
           if (shouldThrow)   
           {  
              // old code  
           }  
           else {  
              // new code  
           }  
        }  
  
        ```  
  
         使用一致的參數格式很有幫助，因為它們是程式庫公開的正式合約。 以下是兩種明顯的格式。  
  
        -   *Switch*.*命名空間*。*參數名稱*  
  
        -   *Switch*.*library*.*參數名稱*  
  
    -   **以工作為基礎的非同步模式 (TAP) 的變更**  
  
         目標應用程式的[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]，<xref:System.Threading.Tasks.Task>和<xref:System.Threading.Tasks.Task%601>物件會繼承文化特性和 UI 文化特性的呼叫執行緒。 以舊版 .NET Framework 為目標或未以特定 .NET Framework 版本為目標的應用程式行為則不會受到影響。 如需詳細資訊，請參閱 」 文化特性和工作為基礎的非同步作業 > 一節<xref:System.Globalization.CultureInfo>類別主題。  
  
         <xref:System.Threading.AsyncLocal%601?displayProperty=fullName>類別可讓您用來代表環境資料的本機指定的非同步控制流程中，例如`async`方法。 它可以用來跨執行緒保存資料。 您也可以定義每次因為環境的資料變更可能會收到通知的回呼方法<xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=fullName>明確變更屬性，或因為執行緒發生內容切換。  
  
         三個便利的方法， <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=fullName>， <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=fullName>，和<xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=fullName>，已加入至工作架構非同步模式 (TAP) 以傳回處於特定狀態的已完成的工作。  
  
         <xref:System.IO.Pipes.NamedPipeClientStream>類別現在支援其新的非同步通訊<xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>。 方法。  
  
    -   **EventSource 現在支援寫入至事件記錄檔**  
  
         您現在可以使用<xref:System.Diagnostics.Tracing.EventSource>類別來管理或操作的記錄檔訊息至事件日誌中，另外在電腦上建立任何現有 ETW 工作階段。 以往，您必須使用 Microsoft.Diagnostics.Tracing.EventSource NuGet 套件，才能使用這項功能。 .NET Framework 4.6 現已內建這項功能。  
  
         NuGet 套件和 .NET Framework 4.6 已更新下列功能：  
  
        -   **動態事件**  
  
             可「動態」定義事件，而不需建立事件方法。  
  
        -   **豐富的裝載**  
  
             允許專用類別和陣列，以及基本類型做為裝載傳遞  
  
        -   **活動追蹤**  
  
             可讓開始與結束事件使用識別碼來標記它們之間的事件，以代表目前作用中的所有活動。  
  
         若要支援這些功能，多載<xref:System.Diagnostics.Tracing.EventSource.Write%2A>方法加入至<xref:System.Diagnostics.Tracing.EventSource>類別。  
  
-   **Windows Presentation Foundation (WPF)**  
  
    -   **HDPI 增強功能**  
  
         現在，WPF 提供比 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 更好的 HDPI 支援。 已變更版面配置進位，以減少含邊界之控制項中的裁剪執行個體。 根據預設，此功能只有當您<xref:System.Runtime.Versioning.TargetFrameworkAttribute>設為.NET 4.6。  應用程式以舊版的 framework 為目標但在執行[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]也可以選擇新的行為加入至下列這一行[ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config 檔的區段︰  
  
        ```  
  
        <AppContextSwitchOverrides  
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"  
        />  
  
        ```  
  
         含不同 DPI 設定 (多 DPI 設定) 且跨多個監視器的 WPF 視窗，現可完全顯示，而不會有被遮蔽的區域。 您可將下列這一行加入 app.config 檔的 `<appSettings>` 區段，以選擇停用這項新的行為：  
  
        ```  
  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
  
        ```  
  
         支援自動載入右 DPI 設定為基礎的資料指標已加入至<xref:System.Windows.Input.Cursor?displayProperty=fullName>。  
  
    -   **觸控是更好**  
  
         客戶會報告[連線](https://connect.microsoft.com/VisualStudio/feedback/details/903760/)的修改會產生無法預期的行為中已經解決[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]。 Windows 市集應用程式和 WPF 應用程式的點兩下臨界值現與 Windows 8.1 和更新版本相同。  
  
    -   **透明的子視窗支援**  
  
         [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中的 WPF 支援 Windows 8.1 和更新版本的透明子視窗功能。 這可讓您在最上層視窗中建立非矩形和透明的子視窗。 您可以啟用此功能，藉由設定<xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=fullName>屬性`true`。  
  
-   **Windows Communication Foundation (WCF)**  
  
    -   **SSL 支援**  
  
         搭配使用 NetTcp 與傳輸安全性和用戶端驗證時，除了 SSL 3.0 和 TLS 1.0 之外，WCF 現在還支援 TLS 1.1 和 TLS 1.2 的 SSL 版。 現在，您可以選取要使用哪一種通訊協定，或停用較不安全的舊版通訊協定。 這可以藉由設定<xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A>屬性或加入下列組態檔。  
  
        ```  
        <netTcpBinding>  
           <binding>  
              <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                 <transport clientCredentialType="None|Windows|Certificate"  
                            protectionLevel="None|Sign|EncryptAndSign"  
                            sslProtocols="Ssl3|Tls1|Tls11|Tls12">  
                    </transport>  
              </security>  
           </binding>  
        </netTcpBinding>  
  
        ```  
  
    -   **使用不同的 HTTP 連線傳送訊息**  
  
         現在，WCF 可讓使用者使用不同的基礎 HTTP 連線以確保成功傳送特定訊息。 執行這項作業的方法有兩種：  
  
        -   **使用連接群組名稱前置詞**  
  
             使用者可以指定字串，讓 WCF 做為可達到連接群組名稱的前置詞。 系統會使用不同的基礎 HTTP 連線來傳送含有不同前置詞的兩個訊息。 您可以將前置詞將索引鍵/值組加入至訊息的<xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=fullName>屬性。 索引鍵是"HttpTransportConnectionGroupNamePrefix";此值為所需的前置詞。  
  
        -   **使用不同的通道處理站**  
  
             使用者也可以啟用功能，針對使用不同通道處理器建立之通道所傳送的訊息，使用不同的基礎 HTTP 連線。 若要啟用此功能，使用者必須將下列 `appSetting` 設為 `true`：  
  
            ```  
  
            <appSettings>  
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />  
            </appSettings>  
  
            ```  
  
-   **Windows Workflow Foundation (WWF)**  
  
     現在，若有未處理的「非通訊協定」書籤時，您可以指定工作流程服務在不按照順序的作業要求逾時之前會保存該要求的秒數。 「非通訊協定」書籤是指與未處理的 Receive 活動無關的書籤。 有些活動會在其實作中建立非通訊協定書籤，因此可能不容易察覺到非通訊協定書籤的存在。 這些活動包括 State 和 Pick。 因此如果您有使用狀態機器或包含 Pick 活動的工作流程服務實作，就很可能會有非通訊協定書籤。 您可將類似下列一行加入 app.config 檔的 `appSettings` 區段，以指定間隔：  
  
    ```  
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>  
    ```  
  
     預設值為 60 秒。 如果 `value` 設為 0，系統會立即拒絕不按照順序的要求，並顯示類似如下的錯誤文字：  
  
    ```Output  
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.   
    ```  
  
     如果收到不按照順序的作業訊息，但沒有非通訊協定書籤時，也會收到相同的訊息。  
  
     如果 `FilterResumeTimeoutInSeconds` 項目的值是非零，並有非通訊協定的書籤，而逾時間隔也已過期，則作業會失敗並顯示逾時訊息。  
  
-   **交易**  
  
     您現在可以包含的分散式的交易識別碼，交易，發生例外狀況衍生自<xref:System.Transactions.TransactionException>擲回。 您可以在 app.config 檔的`appSettings` 區段中加入下列索引鍵，以完成這項作業：  
  
    ```  
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>   
    ```  
  
     預設值是 `false`。  
  
-   **網路功能**  
  
    -   **通訊端重複使用**  
  
         Windows 10 包含新的高延展性網路演算法，其可重複使用對外 TCP 連線的本機連接埠，以更妥善運用電腦資源。 .NET Framework 4.6 支援新的演算法，可讓 .NET 應用程式利用這項新的行為。 在舊版的 Windows 中，並沒有人為的並行連線限制 (通常為動態連接埠範圍的預設大小 16,384)，因此當負載下的連接埠耗盡時，可能會限制服務的延展性。  
  
         為了讓連接埠可以重複使用，在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中加入了兩個新的 API，其可有效地移除並行連線的 64K 限制：  
  
        -   <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName>列舉值。  
  
        -   <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName>屬性。  
  
         根據預設， <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName>屬性是`false`除非`HWRPortReuseOnSocketBind`值`HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319`登錄機碼設定為 0x1。 若要啟用 HTTP 連線的本機連接埠重複使用， <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName>屬性`true`。 這會導致從所有連出 TCP 通訊端連線<xref:System.Net.Http.HttpClient>和<xref:System.Net.HttpWebRequest>使用新的 Windows 10 通訊端選項， [SO_REUSE_UNICASTPORT](https://msdn.microsoft.com/library/windows/desktop/ms740532.aspx)，使本機連接埠重複使用。  
  
         撰寫僅限通訊端的應用程式的開發人員可以指定<xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName>選項，例如呼叫方法時<xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=fullName>以便繫結期間輸出的通訊端重複使用的本機連接埠。  
  
    -   **支援國際網域名稱和 PunyCode**  
  
         新的屬性， <xref:System.Uri.IdnHost%2A>，已加入至<xref:System.Uri>類別，以進一步支援國際網域名稱和 PunyCode。  
  
-   **調整 Windows Form 控制項的大小。**  
  
     這項功能已展開於[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]包含<xref:System.Windows.Forms.DomainUpDown>， <xref:System.Windows.Forms.NumericUpDown>， <xref:System.Windows.Forms.DataGridViewComboBoxColumn>， <xref:System.Windows.Forms.DataGridViewColumn>和<xref:System.Windows.Forms.ToolStripSplitButton>類型和所指定的矩形<xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A>屬性，可繪製<xref:System.Drawing.Design.UITypeEditor>。  
  
     這是一項選擇性功能。 若要啟用這項功能，請將應用程式組態檔 (app.config) 中的 `EnableWindowsFormsHighDpiAutoResizing` 項目設為 `true`：  
  
    ```  
  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
  
    ```  
  
-   **支援的字碼頁編碼方式**  
  
     [!INCLUDE[net_core](../../../includes/net-core-md.md)] 主要支援 Unicode 編碼方式，並且預設會提供字碼頁編碼方式的有限支援。 您可以新增支援，但不受.NET Framework 中可用的字碼頁編碼方式[!INCLUDE[net_core](../../../includes/net-core-md.md)]註冊字碼頁編碼方式<xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=fullName>方法。 如需詳細資訊，請參閱[System.Text.CodePagesEncodingProvider](https://msdn.microsoft.com/en-us/library/system.text.codepagesencodingprovider.aspx)。  
  
-   **.NET 原生**  
  
     以 [!INCLUDE[net_core](../../../includes/net-core-md.md)] 為目標並以 C# 或 Visual Basic 撰寫的 Windows 10 應用程式，現在可以利用將應用程式編譯成機器碼的新技術，而不是使用 IL。 所產生之應用程式的特色是啟動和執行都更快。 如需詳細資訊，請參閱[用於.NET 原生編譯的應用程式](../../../docs/framework/net-native/index.md)。 .NET Native 概觀，以及與 JIT 編譯和 NGEN 差異，這代表什麼意思，會檢查方法，讓您的程式碼，請參閱[.NET 原生和編譯](../../../docs/framework/net-native/net-native-and-compilation.md)。  
  
     當您使用 Visual Studio 2015 編譯您的應用程式時，它們預設會編譯成機器碼。 如需詳細資訊，請參閱[開始使用.NET 原生](../../../docs/framework/net-native/getting-started-with-net-native.md)。  
  
     為了支援對 .NET Native 應用程式進行偵錯，Unmanaged 偵錯 API 已新增許多介面和列舉。 如需詳細資訊，請參閱[偵錯 （Unmanaged API 參考）](../../../ml/index.xml)主題。  
  
-   **開放原始碼.NET Framework 套件**  
  
     [!INCLUDE[net_core](../../../includes/net-core-md.md)]不可變的集合，例如封裝[SIMD Api](http://go.microsoft.com/fwlink/?LinkID=518639)，例如網路 Api 中找到<xref:System.Net.Http>命名空間現在會提供為開放原始碼套件[GitHub](https://github.com/)。 若要存取程式碼，請參閱[GitHub 上的 NetFx](http://go.microsoft.com/fwlink/?LinkID=518634)。 如需詳細資訊，以及如何對這些套件，請參閱[.NET Core 和開放原始碼](../../../docs/framework/get-started/net-core-and-open-source.md)， [GitHub 上的.NET 首頁](http://go.microsoft.com/fwlink/?LinkID=518635)。  
  
 [回到頁首](#introduction)  
  
<a name="v452"></a>   
## <a name="whats-new-in-the-net-framework-452"></a>.NET Framework 4.5.2 的新功能  
  
-   **ASP.NET 應用程式的新 Api。** 新<xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=fullName>和<xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=fullName>方法可讓您檢查及修改回應標頭和狀態碼回應清除至用戶端應用程式。 請考慮使用這些方法，而不是<xref:System.Web.HttpApplication.PreSendRequestHeaders>和<xref:System.Web.HttpApplication.PreSendRequestContent>事件; 它們是更有效率且可靠。  
  
     <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=fullName>方法可讓您排程小型背景工作項目。 完成所有背景工作項目之前，ASP.NET 會追蹤這些項目，並防止 IIS 突然終止背景工作處理序。 此方法只能在 ASP.NET Managed 應用程式網域內呼叫。  
  
     新<xref:System.Web.HttpResponse.HeadersWritten?displayProperty=fullName>和<xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=fullName>屬性會傳回布林值，指出是否已寫入回應標頭。 您可以使用這些屬性來確定這類 Api 呼叫<xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=fullName> （如果擲回例外狀況已寫入標頭） 將會成功。  
  
-   **調整 Windows Form 控制項的大小。** 這項功能已擴充。 您現在可以使用系統 DPI 設定來調整下列其他控制項的元件大小 (例如下拉式方塊中的下拉箭號)：  
  
     <xref:System.Windows.Forms.ComboBox>   
     <xref:System.Windows.Forms.ToolStripComboBox>   
     <xref:System.Windows.Forms.ToolStripMenuItem>   
     <xref:System.Windows.Forms.Cursor>   
     <xref:System.Windows.Forms.DataGridView>   
     <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
     這是一項選擇性功能。 若要啟用這項功能，請將應用程式組態檔 (app.config) 中的 `EnableWindowsFormsHighDpiAutoResizing` 項目設為 `true`：  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
-   **新的工作流程功能。** 使用資源管理員<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>方法 (進而實作<xref:System.Transactions.IPromotableSinglePhaseNotification>介面) 可以使用新<xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=fullName>來要求下列方法︰  
  
    -   將交易提升至 Microsoft 分散式交易協調器 (MSDTC) 交易。  
  
    -   取代<xref:System.Transactions.IPromotableSinglePhaseNotification>與<xref:System.Transactions.ISinglePhaseNotification>，也就是支援單一階段認可的永久性登記。  
  
     您可以在相同的應用程式網域中完成這些作業，而不需要任何額外的 Unmanaged 程式碼來與 MSDTC 互動以進行提升。 從呼叫未完成時，就可以呼叫此新方法<xref:System.Transactions?displayProperty=fullName>至<xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote`可提升登記未實作的方法。  
  
-   **程式碼分析增強功能。** 下列新的 Unmanaged 程式碼分析 API 提供更強大的程式碼分析功能：  
  
     [COR_PRF_ASSEMBLY_REFERENCE_INFO 結構](../../../ocs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)   
     [COR_PRF_HIGH_MONITOR 列舉](../../../ocs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)   
     [GetAssemblyReferences 方法](../Topic/ICorProfilerCallback6::GetAssemblyReferences%20Method.md)   
     [GetEventMask2 方法](../Topic/ICorProfilerInfo5::GetEventMask2%20Method.md)   
     [SetEventMask2 方法](../Topic/ICorProfilerInfo5::SetEventMask2%20Method.md)   
     [AddAssemblyReference 方法](../Topic/ICorProfilerAssemblyReferenceProvider::AddAssemblyReference%20Method.md)  
  
     之前的 `ICorProfiler` 實作支援相依組件的延遲載入。 新程式碼分析 API 要求可立即載入分析工具插入的相依組件，而不是在完全初始化應用程式之後才載入。 這項變更不會影響現有 `ICorProfiler` API 的使用者。  
  
-   **偵錯改進。** 下列新的 Unmanaged 偵錯 API 提供與分析工具更佳的整合。 您現在可以存取分析工具插入的中繼資料，並存取偵錯傾印時編譯器 ReJIT 要求所產生的本機變數和程式碼。  
  
     [SetWriteableMetadataUpdateMode 方法](../Topic/ICorDebugProcess7::SetWriteableMetadataUpdateMode%20Method.md)   
     [EnumerateLocalVariablesEx 方法](../Topic/ICorDebugILFrame4::EnumerateLocalVariablesEx%20Method.md)   
     [GetLocalVariableEx 方法](../Topic/ICorDebugILFrame4::GetLocalVariableEx%20Method.md)   
     [GetCodeEx 方法](../Topic/ICorDebugILFrame4::GetCodeEx%20Method.md)   
     [GetActiveReJitRequestILCode 方法](../Topic/ICorDebugFunction3::GetActiveReJitRequestILCode%20Method.md)   
     [GetInstrumentedILMap 方法](../Topic/ICorDebugILCode2::GetInstrumentedILMap%20Method.md)  
  
-   **事件追蹤變更。** .NET Framework 4.5.2 可對更大的表面區域進行 Windows 事件追蹤 (ETW) 的跨處理序活動追蹤。 此功能可讓進階電源管理 (APM) 廠商提供輕量型工具，以正確追蹤跨執行緒之個別要求和活動的成本。  僅當 ETW 控制器啟用這些事件時，才會引發事件；因此，這些變更不會影響之前寫入的 ETW 程式碼或停用 ETW 時所執行的程式碼。  
  
-   **將交易升級，並將它轉換為永久性登記**  
  
     <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=fullName>新 API 加入至.NET Framework 4.5.2 與 4.6:  
  
    ```  
  
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,  
                                              IPromotableSinglePhaseNotification promotableNotification,  
                                              ISinglePhaseNotification enlistmentNotification,  
                                              EnlistmentOptions enlistmentOptions)  
  
    ```  
  
     先前所建立的登錄可能會使用的方法<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=fullName>回應<xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=fullName>方法。 它會要求 `System.Transactions` 將交易升級為 MSDTC 交易，並將可升級登記「轉換」為永久性登記。 這個方法成功完成之後， <xref:System.Transactions.IPromotableSinglePhaseNotification>介面不再被參考的`System.Transactions`，以及任何未來的通知將送達上提供<xref:System.Transactions.ISinglePhaseNotification>介面。 登記必須做為永久性登記，才可支援交易記錄和復原。 請參閱<xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=fullName>如需詳細資訊。 此外，必須支援登記<xref:System.Transactions.ISinglePhaseNotification>。  這個方法可以*只*時處理呼叫<xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=fullName>呼叫。 如果不是這樣， <xref:System.Transactions.TransactionException>擲回例外狀況。  
  
 [回到頁首](#introduction)  
  
<a name="v451"></a>   
## <a name="whats-new-in-the-net-framework-451"></a>.NET Framework 4.5.1 的新功能  
 **2014 年 4 月更新**:  
  
-   [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658)包含可攜式類別庫範本，以支援這些案例的更新︰  
  
    -   您可以使用以 Windows 8.1、Windows Phone 8.1 和 Windows Phone Silverlight 8.1 為目標之可攜式類別庫中的 Windows 執行階段 API。  
  
    -   當您以 Windows 8.1 或 Windows Phone 8.1. 為目標時，可將 XAML (Windows.UI.XAML 類別) 加入至可攜式類別庫中。 支援下列 XAML 範本：「空白網頁」、「資源字典」、「樣板化控制項」和「使用者控制項」。  
  
    -   您可以建立可攜式 Windows 執行階段元件 (.winmd 檔案)，以便用於以 Windows 8.1 和 Windows Phone 8.1 為目標的市集應用程式。  
  
    -   您可以像是可攜式類別庫一樣，重定 Windows 市集或 Windows Phone 市集類別庫的目標。  
  
     如需有關這些變更的詳細資訊，請參閱[可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)。  
  
-   .NET Framework 內容集現在包含 [!INCLUDE[net_native](../../../includes/net-native-md.md)] (用於建置及部署 Windows 應用程式的先行編譯技術) 的文件。 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 會將您的應用程式直接編譯為機器碼 (而不是中繼語言 (IL)) 以提升效能。 如需詳細資訊，請參閱[用於.NET 原生編譯的應用程式](../../../docs/framework/net-native/index.md)。  
  
-   [.NET Framework 參考來源](http://referencesource.microsoft.com/)提供新的瀏覽體驗和增強的功能。 您現在可以瀏覽.NET Framework 原始程式碼，[下載參考](http://referencesource.microsoft.com/download.html)為離線檢視，並逐步執行偵錯期間 （包含修補程式和更新） 的來源。 如需詳細資訊，請參閱部落格文章[.NET 參考來源的新外觀](http://blogs.msdn.com/b/dotnet/archive/2014/02/24/a-new-look-for-net-reference-source.aspx)。  
  
 .NET Framework 4.5.1 的核心新功能和增強功能包括：  
  
-   組件的自動繫結重新導向。 從 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 開始，當您編譯鎖定 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 的應用程式時，如果您的應用程式或其元件參考相同組件的多個版本，就可能會將繫結重新導向加入至應用程式組態檔。 您也可以對鎖定舊版 .NET Framework 的專案啟用這項功能。 如需詳細資訊，請參閱[How to︰ 啟用和停用自動繫結重新導向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)。  
  
-   可收集診斷資訊，協助開發人員改進伺服器和雲端應用程式效能的功能。 如需詳細資訊，請參閱<xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A>和<xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A>方法<xref:System.Diagnostics.Tracing.EventSource>類別。  
  
-   可在記憶體回收期間明確壓縮大型物件堆積 (LOH) 的功能。 如需詳細資訊，請參閱<xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName>屬性。  
  
-   其他效能改進功能包括 ASP.NET 應用程式暫止、多核心 JIT 改進功能，以及 .NET Framework 更新後應用程式更快速啟動。 如需詳細資訊，請參閱[.NET Framework 4.5.1 公告](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)和[ASP.NET 應用程式暫停](http://blogs.msdn.com/b/dotnet/archive/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting.aspx)部落格文章。  
  
 Windows Form 的增強功能包括：  
  
-   調整 Windows Form 控制項的大小。 您可以透過在應用程式的應用程式組態檔中選擇加入一個項目，使用系統 DPI 設定來調整控制項的元件大小 (例如屬性方格中出現的圖示)。 目前支援這項功能的 Windows Form 控制項如下：  
  
     <xref:System.Windows.Forms.PropertyGrid>   
     <xref:System.Windows.Forms.TreeView>   
     某些層面<xref:System.Windows.Forms.DataGridView> (請參閱[4.5.2 的新功能](#v452)的其他支援的控制項)  
  
     若要啟用這項功能，加入新<>\>至組態檔 (app.config)，並將項目`EnableWindowsFormsHighDpiAutoResizing`項目`true`:  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
 在 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 中對您的 .NET Framework 應用程式進行偵錯時的改進功能包括：  
  
-   在 Visual Studio Debugger 中傳回值。 當您在 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]中對 Managed 應用程式進行偵錯時，[自動變數] 視窗會顯示方法的傳回類型和值。 這項資訊適用於桌面、Windows 市集和 Windows Phone 應用程式。 如需詳細資訊，請參閱[檢查方法呼叫的傳回值](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f\(v=vs.120\).aspx)MSDN Library 中。  
  
-   64 位元應用程式的 [編輯後繼續] 功能。 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 對桌面、Windows 市集和 Windows Phone 的 64 位元 Managed 應用程式支援 [編輯後繼續] 功能。 現有限制仍然有效的 32 位元和 64 位元應用程式 (請參閱上一節的[支援的程式碼變更 (C#)](http://msdn.microsoft.com/library/ms164927\(v=vs.120\).aspx)文章)。  
  
-   非同步感知偵錯。 為了在 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 中更為容易對非同步應用程式進行偵錯，呼叫堆疊會隱藏編譯器提供的基礎結構程式碼來支援非同步程式設計，以及提供邏輯父框架中的鍊結，讓您可以更清楚地了解邏輯程式執行的方式。 [工作] 視窗會取代 [平行工作] 視窗，並顯示與特定中斷點相關的工作，同時也會顯示應用程式中目前為作用中或已排程的任何其他工作。 這項功能的 「 非同步感知偵錯 」 區段中，您可以參閱[.NET Framework 4.5.1 公告](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)。  
  
-   對 Windows 執行階段元件提供更佳的例外狀況支援。 在 [!INCLUDE[win81](../../../includes/win81-md.md)] 中，Windows 市集應用程式所引發的例外狀況會保留造成例外狀況之錯誤的資訊，甚至跨語言界限。 「 Windows 市集應用程式開發 > 一節中的這項功能，您可以參閱[.NET Framework 4.5.1 公告](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)。  
  
 從開始[!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]，您可以使用[Managed 特性指引最佳化工具 (Mpgo.exe)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)最佳化[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式，以及桌面應用程式。  
  
 如需 ASP.NET 4.5.1 的新功能，請參閱[ASP.NET 4.5.1 和 Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) ASP.NET 網站上。  
  
 [回到頁首](#introduction)  
  
<a name="core"></a>   
## <a name="whats-new-in-the-net-framework-45"></a>.NET Framework 4.5 的新功能  
  
### <a name="core-new-features-and-improvements"></a>核心新功能和增強功能  
  
-   可透過在部署期間偵測及關閉 .NET Framework 4 應用程式的方式，減少系統重新啟動次數的功能。 請參閱[在.NET Framework 4.5 安裝期間減少系統重新啟動](../../../docs/framework/deployment/reducing-system-restarts.md)。  
  
-   在 64 位元平台上支援大於 2 GB 的陣列。 這項功能可以在應用程式組態檔中啟用。 請參閱[ <> \>元素](../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)，其中也會列出對於物件大小和陣列大小的其他限制。  
  
-   透過伺服器的背景記憶體回收改善效能。 當您在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中使用伺服器記憶體回收時，背景記憶體回收會自動啟用。 請參閱 < 背景伺服器記憶體回收區段[回收的基本概念](../../../docs/standard/garbage-collection/fundamentals.md)主題。  
  
-   背景 Just-in-Time (JIT) 編譯，它可在多核心處理器上選擇性提供，以改善應用程式效能。 請參閱<xref:System.Runtime.ProfileOptimization>。  
  
-   可限制規則運算式引擎在逾時之前，嘗試解析規則運算式之時間長度的功能。 請參閱<xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=fullName>屬性。  
  
-   可定義應用程式定義域之預設文化特性的功能。 請參閱<xref:System.Globalization.CultureInfo>類別。  
  
-   對 Unicode (UTF-16) 編碼的主控台支援。 請參閱<xref:System.Console>類別。  
  
-   支援文化特性字串順序和比較資料的版本控制。 請參閱<xref:System.Globalization.SortVersion>類別。  
  
-   改善擷取資源時的效能。 請參閱[封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)。  
  
-   改善 Zip 壓縮，縮減壓縮檔的大小。 請參閱<xref:System.IO.Compression?displayProperty=fullName>命名空間。  
  
-   能夠自訂反映內容以覆寫預設反映行為透過<xref:System.Reflection.Context.CustomReflectionContext>類別。  
  
-   支援 2008年版的國際化網域名稱中的應用程式 (IDNA) 標準時<xref:System.Globalization.IdnMapping?displayProperty=fullName>類別用於[!INCLUDE[win8](../../../includes/win8-md.md)]。  
  
-   對作業系統委派字串比較，該字串比較會在 [!INCLUDE[win8](../../../includes/win8-md.md)] 上使用 .NET Framework 時實作 Unicode 6.0。 在其他平台上執行時，.NET Framework 會包含自己的字串比較資料 (該資料會實作 Unicode 5.x)。 請參閱<xref:System.String>類別和 \< 備註 > 一節<xref:System.Globalization.SortVersion>類別。  
  
-   可用每個應用程式定義域做為基準，計算字串之雜湊碼的功能。 See [<>\> Element](../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).  
  
-   類型反映支援之間分割<xref:System.Type>和<xref:System.Reflection.TypeInfo>類別。 請參閱[Windows 市集應用程式的.NET Framework 中反映](../../../docs/framework/reflection-and-codedom/reflection-for-windows-store-apps.md)。  
  
### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)  
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，Managed Extensibility Framework (MEF) 提供下列新功能：  
  
-   支援泛型類型。  
  
-   以慣例為基礎的程式撰寫模型，可讓您依命名慣例而非屬性建立組件。  
  
-   多個範圍。  
  
-   可以在建立 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式時使用的 MEF 子集。 這個子集可做為[可下載的套件](http://go.microsoft.com/fwlink/?LinkId=256238)NuGet gallery。 若要安裝封裝，在 Visual Studio 中開啟您的專案中，選擇**管理 NuGet 封裝**從**專案** 功能表上，然後在搜尋線上`Microsoft.Composition`封裝。  
  
 如需詳細資訊，請參閱[Managed Extensibility Framework (MEF)](../../../docs/framework/mef/index.md)。  
  
### <a name="asynchronous-file-operations"></a>非同步檔案作業  
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，C# 和 Visual Basic 語言已加入新的非同步功能。 這些功能會加入執行非同步作業的工作模型。 若要使用這個全新的模型，請在 I/O 類別中使用非同步方法。 請參閱[非同步檔案 I/O](../../../docs/standard/io/非同步檔案-i-o.md)。  
  
<a name="tools"></a>   
### <a name="tools"></a>工具  
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，資源檔產生器 (Resgen.exe) 可讓您從 .NET Framework 組件內嵌的 .resources 檔建立 .resw 檔，以供 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式使用。 如需詳細資訊，請參閱[Resgen.exe （資源檔產生器）](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)。  
  
 Managed 特性指引最佳化 (Mpgo.exe) 可讓您藉由最佳化原生映像組件，改善應用程式啟動時間、記憶體使用量 (工作集大小) 和輸送量。 命令列工具會產生原生映像應用程式組件的設定檔資料。 請參閱[Mpgo.exe （Managed 的特性指引最佳化工具）](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)。 從 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 開始，您可以使用 Mpgo.exe 最佳化 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式及桌面應用程式。  
  
<a name="parallel"></a>   
### <a name="parallel-computing"></a>平行運算  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 針對平行計算提供了許多新功能和改進功能。 這些功能包括提升效能、增強控制、改善非同步程式設計的支援、全新的資料流程程式庫，以及改善平行偵錯與效能分析的支援。 請參閱文章[.NET 4.5 平行處理原則的新](http://go.microsoft.com/fwlink/?LinkId=235061)中平行程式設計與.NET 部落格。  
  
<a name="web"></a>   
### <a name="web"></a>Web  
 ASP.NET 4.5 和 4.5.1 加入了 Web Form、WebSocket 支援、非同步處理常式、效能增強功能及許多其他功能的模型繫結。 如需詳細資訊，請參閱下列資源：  
  
-   [ASP.NET 4.5 和 Visual Studio 2012](../Topic/ASP.NET%20Core%20and%20Visual%20Studio%202015.md) MSDN Library 中。  
  
-   [ASP.NET 4.5.1 和 Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) ASP.NET 網站上。  
  
<a name="networking"></a>   
### <a name="networking"></a>網路功能  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為 HTTP 應用程式提供了新的程式設計介面。 如需詳細資訊，請參閱新<xref:System.Net.Http?displayProperty=fullName>和<xref:System.Net.Http.Headers?displayProperty=fullName>命名空間。  
  
 支援也會併入新的程式設計介面，用於接受並進行互動使用現有的 WebSocket 連線<xref:System.Net.HttpListener>和相關類別。 如需詳細資訊，請參閱新<xref:System.Net.WebSockets>命名空間和<xref:System.Net.HttpListener>類別。  
  
 此外，[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 還包括下列網路改進功能：  
  
-   符合 RFC 標準的 URI 支援。 如需詳細資訊，請參閱<xref:System.Uri>和相關類別。  
  
-   支援國際化網域名稱 (IDN) 剖析。 如需詳細資訊，請參閱<xref:System.Uri>和相關類別。  
  
-   支援電子郵件地址國際化 (EAI)。 如需詳細資訊，請參閱<xref:System.Net.Mail>命名空間。  
  
-   改進的 IPv6 支援。 如需詳細資訊，請參閱<xref:System.Net.NetworkInformation>命名空間。  
  
-   雙重模式通訊端支援。 如需詳細資訊，請參閱<xref:System.Net.Sockets.Socket>和<xref:System.Net.Sockets.TcpListener>類別。  
  
<a name="client"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，Windows Presentation Foundation (WPF) 包含以下層面的變更與改進功能：  
  
-   新<xref:System.Windows.Controls.Ribbon.Ribbon>控制項，可讓您實作裝載了 快速存取工具列、 應用程式功能表和索引標籤功能區使用者介面。  
  
-   新<xref:System.ComponentModel.INotifyDataErrorInfo>介面支援同步和非同步資料驗證。  
  
-   新功能<xref:System.Windows.Controls.VirtualizingPanel>和<xref:System.Windows.Threading.Dispatcher>類別。  
  
-   改善顯示大型群組資料集合時的效能，以及透過在非 UI 執行緒上存取集合提升效能。  
  
-   資料繫結至靜態屬性，資料繫結至自訂型別都會實作<xref:System.Reflection.ICustomTypeProvider>介面和擷取資料繫結資訊從繫結運算式。  
  
-   隨著值變更重新調整資料的位置 (即時繪圖)。  
  
-   可查看項目容器的資料內容是否已中斷連接的功能。  
  
-   可設定屬性變更與資料來源更新之間應該經過之時間長度的功能。  
  
-   改進對實作弱式事件模式的支援。 此外，事件現在可以接受標記延伸。  
  
<a name="windows_communication_foundation"></a>   
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中已加入下列功能，這些功能可讓寫入和維護 Windows Communication Foundation (WCF) 應用程式更容易：  
  
-   簡化產生的組態檔。  
  
-   支援合約優先開發。  
  
-   可更輕鬆地設定 ASP.NET 相容性模式的功能。  
  
-   預設傳輸屬性值中所做的變更，可降低必須設定這些屬性的可能性。  
  
-   若要更新<xref:System.Xml.XmlDictionaryReaderQuotas>類別，以減少您必須手動設定 XML 字典讀取器配額的可能性。  
  
-   Visual Studio 會在建置流程中驗證 WCF 組態檔，如此您就可以在執行應用程式之前偵測組態錯誤。  
  
-   新增非同步資料流支援。  
  
-   新增 HTTPS 通訊協定對應，如此就能更容易使用 Internet Information Services (IIS) 透過 HTTPS 公開端點。  
  
-   可藉由將 `?singleWSDL` 附加至服務 URL 的方式，在單一 WSDL 文件中產生中繼資料的功能。  
  
-   Websocket 支援，可透過與 TCP 傳輸類似的效能特性在連接埠 80 與 443 之間進行真正的雙向通訊。  
  
-   支援在程式碼中設定服務。  
  
-   XML 編輯器工具提示。  
  
-   <xref:System.ServiceModel.ChannelFactory>快取支援。  
  
-   支援二進位編碼器壓縮。  
  
-   支援 UDP 傳輸，可讓開發人員撰寫使用「射後不理」(Fire and Forget) 訊息的服務。 用戶端傳送訊息給服務，而不期待服務發出任何回應。  
  
-   可在使用 HTTP 傳輸和傳輸安全性時，於單一 WCF 端點上支援多種驗證模式的功能。  
  
-   支援使用國際化網域名稱 (IDN) 的 WCF 服務。  
  
 如需詳細資訊，請參閱[的新功能 Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=228173)。  
  
<a name="windows_workflow_foundation"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，Windows Workflow Foundation (WF) 已加入數項新功能，包括：  
  
-   狀態機器工作流程，首次引進.NET Framework 4.0.1 的一部分 ([.NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092))。 這項更新包括數個可讓開發人員建立狀態機器工作流程的新類別和活動。 這些類別和活動已針對 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 進行更新，並加入下列功能：  
  
    -   可設定狀態中斷點的功能。  
  
    -   可在工作流程設計工具中複製和貼上轉換的功能。  
  
    -   設計工具支援建立共用的觸發程序轉換。  
  
    -   活動建立狀態機器工作流程，包括︰ <xref:System.Activities.Statements.StateMachine>，<xref:System.Activities.Statements.State>，和<xref:System.Activities.Statements.Transition>。  
  
-   增強的「工作流程設計工具」功能，如下所示：  
  
    -   增強的工作流程搜尋功能在 Visual Studio 中，包括**快速尋找**和**檔案中尋找**。  
  
    -   可在第二個子活動加入至容器活動時自動建立序列活動，以及同時將這兩個活動包含在序列活動中的功能。  
  
    -   平移支援，不需使用捲軸就能變更工作流程的可見部分。  
  
    -   新**文件大綱**檢視，以樹狀樣式大綱檢視中顯示工作流程的元件，並可讓您選取的元件中**文件大綱**檢視。  
  
    -   可將註釋加入至活動的功能。  
  
    -   可使用工作流程設計工具定義並取用活動委派的功能。  
  
    -   在狀態機器及流程圖工作流程中自動連接和自動插入活動和轉換。  
  
-   將工作流程的檢視狀態資訊儲存在 XAML 檔案的單一項目中，如此您就可以輕鬆尋找和編輯檢視狀態資訊。  
  
-   NoPersistScope 容器活動，可防止保存子活動。  
  
-   支援 C# 運算式：  
  
    -   使用 Visual Basic 的工作流程專案會使用 Visual Basic 運算式，而 C# 工作流程專案則會使用 C# 運算式。  
  
    -   在 Visual Studio 2010 中建立且具有 Visual Basic 運算式的 C# 工作流程專案，能夠與使用 C# 運算式的 C# 工作流程專案相容。  
  
-   版本控制增強功能：  
  
    -   新<xref:System.Activities.WorkflowIdentity>類別，可提供持續性工作流程執行個體和它的工作流程定義之間的對應。  
  
    -   並存執行多個工作流程版本在相同的主應用程式，包括<xref:System.ServiceModel.Activities.WorkflowServiceHost>。  
  
    -   在動態更新中，修改所保存工作流程執行個體定義的功能。  
  
-   開發合約優先 (Contract-first) 工作流程服務，可提供自動配合現有服務合約產生活動的支援。  
  
 如需詳細資訊，請參閱[的新功能 Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=228176)。  
  
<a name="tailored"></a>   
### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]  
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式是專為特定尺寸所設計，並且會利用 Windows 作業系統的強大功能。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或 4.5.1 的子集可於使用 C# 或 Visual Basic 建置適用於 Windows 的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式時提供。 這個子集稱為[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]，會在討論[概觀](http://go.microsoft.com/fwlink/?LinkId=228491)Windows 開發人員中心。  
  
<a name="portable"></a>   
### <a name="portable-class-libraries"></a>可攜式類別庫  
 在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] (含) 以後版本中的可攜式類別庫專案可讓您撰寫及建置可在多個 .NET Framework 平台上執行的 Managed 組件。 使用可攜式類別庫專案時，可選擇做為目標的平台 (例如 Windows Phone 和 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)])。 專案中可用的類型和成員會自動限制為這些平台上的通用類型和成員。 如需詳細資訊，請參閱[可攜式類別庫](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)。  
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 和 Out-of-band 的版本](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)   
 [什麼是 Visual Studio 2013 的新功能](http://msdn.microsoft.com/library/bb386063\(v=vs.120\).aspx)   
 [ASP.NET 4.5.1 及 Web Tools for Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094)   
 [ASP.NET 和 Visual Studio for Web](../Topic/ASP.NET%20and%20Visual%20Studio%20for%20Web.md)   
 [什麼是 Windows Communication Foundation 的新功能](http://go.microsoft.com/fwlink/?LinkId=228173)   
 [什麼是 Windows Workflow Foundation 的新功能](http://go.microsoft.com/fwlink/?LinkId=228176)   
 [什麼是 Visual c + + 的新功能](http://msdn.microsoft.com/library/hh409293\(v=vs.120\).aspx)