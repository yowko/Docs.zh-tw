---
title: 指定自訂的加密演算法
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: c92ce463f885e9784913b07eb11941ecd7d78d09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113707"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="fe08d-102">指定自訂的加密演算法</span><span class="sxs-lookup"><span data-stu-id="fe08d-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="fe08d-103">WCF 可讓您指定加密資料或計算數位簽章時使用的自訂密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="fe08d-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="fe08d-104">其步驟如下：</span><span class="sxs-lookup"><span data-stu-id="fe08d-104">This is done by the following steps:</span></span>  
  
1.  <span data-ttu-id="fe08d-105">衍生的類別</span><span class="sxs-lookup"><span data-stu-id="fe08d-105">Derive a class from</span></span> <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2.  <span data-ttu-id="fe08d-106">註冊演算法</span><span class="sxs-lookup"><span data-stu-id="fe08d-106">Register the algorithm</span></span>  
  
3.  <span data-ttu-id="fe08d-107">使用 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 衍生的類別設定繫結。</span><span class="sxs-lookup"><span data-stu-id="fe08d-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="fe08d-108">從 SecurityAlgorithmSuite 衍生類別</span><span class="sxs-lookup"><span data-stu-id="fe08d-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="fe08d-109"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 是一個抽象的基底類別，可讓您指定執行各種安全性相關作業時使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="fe08d-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="fe08d-110">例如，計算數位簽章的雜湊或加密訊息。</span><span class="sxs-lookup"><span data-stu-id="fe08d-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="fe08d-111">下列程式碼示範如何從 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 衍生類別：</span><span class="sxs-lookup"><span data-stu-id="fe08d-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="fe08d-112">註冊自訂演算法</span><span class="sxs-lookup"><span data-stu-id="fe08d-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="fe08d-113">您可以在組態檔或命令式程式碼中進行註冊。</span><span class="sxs-lookup"><span data-stu-id="fe08d-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="fe08d-114">註冊自訂演算法的方法是，在實作密碼編譯服務提供者和別名的類別之間建立對應。</span><span class="sxs-lookup"><span data-stu-id="fe08d-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="fe08d-115">接著，將別名對應到在 WCF 服務的繫結中指定演算法時使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="fe08d-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="fe08d-116">下列組態程式碼片段說明如何在組態中註冊自訂演算法：</span><span class="sxs-lookup"><span data-stu-id="fe08d-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="fe08d-117">在下的一節 <`cryptoClasses`> 項目會建立 SHA256CryptoServiceProvider 和別名"SHA256CSP"之間的對應。</span><span class="sxs-lookup"><span data-stu-id="fe08d-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="fe08d-118"><`nameEntry`> 項目會建立"SHA256CSP"別名和指定的 URL 之間的對應 (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm )。</span><span class="sxs-lookup"><span data-stu-id="fe08d-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm ).</span></span>  
  
 <span data-ttu-id="fe08d-119">若要在程式碼中註冊自訂演算法，請使用 <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> 方法。</span><span class="sxs-lookup"><span data-stu-id="fe08d-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="fe08d-120">此方法會建立兩個對應。</span><span class="sxs-lookup"><span data-stu-id="fe08d-120">This method creates both mappings.</span></span> <span data-ttu-id="fe08d-121">下列範例會示範如何呼叫這個方法：</span><span class="sxs-lookup"><span data-stu-id="fe08d-121">The following example shows how to call this method:</span></span>  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="fe08d-122">設定繫結</span><span class="sxs-lookup"><span data-stu-id="fe08d-122">Configure the Binding</span></span>  
 <span data-ttu-id="fe08d-123">在繫結設定中指定自訂 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 衍生的類別來設定繫結，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="fe08d-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="fe08d-124">如需完整的程式碼範例，請參閱 < [WCF 安全性中的密碼編譯靈活性](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md)範例。</span><span class="sxs-lookup"><span data-stu-id="fe08d-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe08d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe08d-125">See also</span></span>

- [<span data-ttu-id="fe08d-126">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="fe08d-126">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fe08d-127">保護服務的安全</span><span class="sxs-lookup"><span data-stu-id="fe08d-127">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="fe08d-128">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="fe08d-128">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="fe08d-129">安全性概念</span><span class="sxs-lookup"><span data-stu-id="fe08d-129">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)
