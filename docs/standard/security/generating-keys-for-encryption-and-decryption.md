---
title: 產生加密和解密金鑰
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 839a04d8a06e782582705cf0d9ad92d2e2df6af6
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45526872"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>產生加密和解密金鑰
建立和管理金鑰是密碼編譯程序中很重要的一部分。 對稱演算法需要建立金鑰和初始化向量 (IV)。 務必不要對不該解密您資料的任何人透露金鑰。 IV 不需要加密，但是應該針對每個工作階段變更。 非對稱演算法需要建立公開金鑰和私密金鑰。 公開金鑰可以公開給任何人，但私密金鑰必須只有將解密以公開金鑰加密之資料的一方知道。 本節描述如何產生及管理對稱和非對稱演算法的金鑰。  
  
## <a name="symmetric-keys"></a>對稱金鑰  
 .NET Framework 所提供的對稱加密類別需要一個金鑰和新的初始化向量 (IV) 才能加密和解密資料。 每當您使用預設建構函式建立其中一個 Managed 對稱密碼編譯類別的新執行個體時，便會自動建立新的金鑰和 IV。 您允許解密資料的任何人都必須擁有相同的金鑰和 IV，並使用相同的演算法。 一般而言，應該為每個工作階段建立新的金鑰和 IV，且金鑰和 IV 都不應該儲存以用於稍後的工作階段。  
  
 若要與遠端的一方溝通對稱金鑰和 IV，通常會使用非對稱加密來加密對稱金鑰。 在不安全的網路中傳送未加密的金鑰並不安全，因為任何人只要攔截金鑰和 IV，就可以解密您的資料。 如需使用加密交換資料的詳細資訊，請參閱 [建立密碼編譯配置](../../../docs/standard/security/creating-a-cryptographic-scheme.md)。  
  
 下列範例顯示實作 TripleDES 演算法的 <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> 類別的新執行個體建立。  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
```  
  
 先前的程式碼執行時，會產生新的金鑰和 IV 並分別放在 **Key** 和 **IV** 屬性。  
  
 有時候您可能需要產生多個金鑰。 在此情況下，您可以建立實作對稱演算法之類別的新執行個體，然後呼叫 **GenerateKey** 和 **GenerateIV** 方法來建立新的金鑰和 IV。 下列程式碼範例說明在建立非對稱密碼編譯類別的新執行個體之後，如何建立新的金鑰和 IV。  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
TDES.GenerateIV()  
TDES.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
TDES.GenerateIV();  
TDES.GenerateKey();  
```  
  
 先前的程式碼執行時，當建立 **TripleDESCryptoServiceProvider** 的新執行個體時，會產生金鑰和 IV。 呼叫 **GenerateKey** 和 **GenerateIV** 方法時，會建立另一個金鑰和 IV。  
  
## <a name="asymmetric-keys"></a>非對稱金鑰  
 .NET Framework 提供 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 和 <xref:System.Security.Cryptography.DSACryptoServiceProvider> 類別以進行非對稱式加密。 當您使用預設建構函式來建立新的執行個體時，這些類別會建立公開/私密金鑰組。 非對稱金鑰可以儲存以用於多個工作階段，或只針對一個工作階段而產生。 雖然公開金鑰可以公開提供使用，但應該小心地看護私密金鑰。  
  
 每當建立非對稱式演算法類別的新執行個體時，就會產生公開/私密金鑰組。 建立類別的新執行個體之後，可以使用兩種方法之一擷取金鑰資訊：  
  
-   <xref:System.Security.Cryptography.RSA.ToXmlString%2A> 方法，會傳回金鑰資訊的 XML 表示法。  
  
-   <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> 方法，它會傳回 <xref:System.Security.Cryptography.RSAParameters> 結構，可保存金鑰資訊。  
  
 這兩種方法都接受布林值，表示是否只傳回公用金鑰資訊，還是同時傳回公開金鑰和私密金鑰資訊。 **RSACryptoServiceProvider** 類別可以使用 **方法，初始化為** RSAParameters <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> 結構的值。  
  
 非對稱私密金鑰不應逐字或以純文字儲存到本機電腦上。 如果您需要儲存私密金鑰，您應該使用金鑰容器。 如需如何將私密金鑰儲存到金鑰容器的詳細資訊，請參閱 [操作說明：將對稱金鑰儲存在金鑰容器中](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)。  
  
 下列程式碼範例會建立 **RSACryptoServiceProvider** 類別的新執行個體、建立公開/私密金鑰組，並將公開金鑰資訊儲存到 **RSAParameters** 結構。  
  
```vb  
'Generate a public/private key pair.  
Dim RSA as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim RSAKeyInfo As RSAParameters = RSA.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters RSAKeyInfo = RSA.ExportParameters(false);  
```  
  
## <a name="see-also"></a>另請參閱

- [加密資料](../../../docs/standard/security/encrypting-data.md)  
- [解密資料](../../../docs/standard/security/decrypting-data.md)  
- [The signature is valid](../../../docs/standard/security/cryptographic-services.md)  
- [操作說明：將對稱金鑰儲存在金鑰容器中](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
