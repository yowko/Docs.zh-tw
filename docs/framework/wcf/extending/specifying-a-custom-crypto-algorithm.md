---
title: 指定自訂的加密演算法
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 5c7bddb7e6e1696ea1cb4f8359e34a51a89fce40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537682"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>指定自訂的加密演算法
WCF 可讓您指定加密資料或計算數位簽章時使用的自訂密碼編譯演算法。 其步驟如下：  
  
1.  從 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 衍生類別  
  
2.  註冊演算法  
  
3.  使用 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 衍生的類別設定繫結。  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>從 SecurityAlgorithmSuite 衍生類別  
 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 是一個抽象的基底類別，可讓您指定執行各種安全性相關作業時使用的演算法。 例如，計算數位簽章的雜湊或加密訊息。 下列程式碼示範如何從 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 衍生類別：  
  
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
  
## <a name="register-the-custom-algorithm"></a>註冊自訂演算法  
 您可以在組態檔或命令式程式碼中進行註冊。 註冊自訂演算法的方法是，在實作密碼編譯服務提供者和別名的類別之間建立對應。 接著，將別名對應到在 WCF 服務的繫結中指定演算法時使用的 URI。 下列組態程式碼片段說明如何在組態中註冊自訂演算法：  
  
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
  
 在下的一節 <`cryptoClasses`> 項目會建立 SHA256CryptoServiceProvider 和別名"SHA256CSP"之間的對應。 <`nameEntry`> 項目會建立"SHA256CSP"別名和指定的 URL 之間的對應 (http://constoso.com/CustomAlgorithms/CustomHashAlgorithm )。  
  
 若要在程式碼中註冊自訂演算法，請使用 <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> 方法。 此方法會建立兩個對應。 下列範例會示範如何呼叫這個方法：  
  
```  
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the   
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>設定繫結  
 在繫結設定中指定自訂 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 衍生的類別來設定繫結，如下列程式碼片段所示：  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 如需完整的程式碼範例，請參閱 < [WCF 安全性中的密碼編譯靈活性](../../../../docs/framework/wcf/samples/cryptographic-agility-in-wcf-security.md)範例。  
  
## <a name="see-also"></a>另請參閱
- [保護服務和用戶端的安全](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [保護服務安全](../../../../docs/framework/wcf/securing-services.md)
- [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [安全性概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)
