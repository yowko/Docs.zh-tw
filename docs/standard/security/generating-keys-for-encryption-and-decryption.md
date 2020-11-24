---
title: 產生加密和解密金鑰
description: 瞭解如何在 .NET 中建立及管理對稱和非對稱金鑰以進行加密和解密。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET], keys
- symmetric keys
- asymmetric keys [.NET]
- cryptography [.NET], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 2af54cef4f233b7bcae5c476f1aa49fdbf7ef2fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689715"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>產生加密和解密金鑰

建立和管理金鑰是密碼編譯程序中很重要的一部分。 對稱演算法需要建立金鑰和初始化向量 (IV)。 務必不要對不該解密您資料的任何人透露金鑰。 IV 不需要加密，但是應該針對每個工作階段變更。 非對稱演算法需要建立公開金鑰和私密金鑰。 公開金鑰可以公開給任何人，但私密金鑰必須只有將解密以公開金鑰加密之資料的一方知道。 本節描述如何產生及管理對稱和非對稱演算法的金鑰。  
  
## <a name="symmetric-keys"></a>對稱金鑰  

 .NET 所提供的對稱式加密類別需要 (IV) 的金鑰和新的初始化向量，才能加密和解密資料。 每當您使用無參數方法建立其中一個 managed 對稱式密碼編譯類別的新實例時 `Create()` ，就會自動建立新的金鑰和 IV。 您允許解密資料的任何人都必須擁有相同的金鑰和 IV，並使用相同的演算法。 一般而言，應該為每個工作階段建立新的金鑰和 IV，且金鑰和 IV 都不應該儲存以用於稍後的工作階段。  
  
 若要與遠端的一方溝通對稱金鑰和 IV，通常會使用非對稱加密來加密對稱金鑰。 在不安全的網路中傳送未加密的金鑰並不安全，因為任何人只要攔截金鑰和 IV，就可以解密您的資料。  
  
 下列範例會示範如何建立演算法的預設實類別的新實例 <xref:System.Security.Cryptography.Aes> 。  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 先前的程式碼執行時，會產生新的金鑰和 IV 並分別放在 **Key** 和 **IV** 屬性。  
  
 有時候您可能需要產生多個金鑰。 在此情況下，您可以建立實作對稱演算法之類別的新執行個體，然後呼叫 **GenerateKey** 和 **GenerateIV** 方法來建立新的金鑰和 IV。 下列程式碼範例說明如何在已建立對稱密碼編譯類別的新實例之後，建立新的金鑰和 Iv。  
  
```vb  
Dim aes As Aes = Aes.Create()  
aes.GenerateIV()  
aes.GenerateKey()  
```  
  
```csharp  
Aes aes = Aes.Create();  
aes.GenerateIV();  
aes.GenerateKey();  
```  
  
 執行上述程式碼時，會在建立新的 **Aes** 實例時產生金鑰和 IV。 呼叫 **GenerateKey** 和 **GenerateIV** 方法時，會建立另一個金鑰和 IV。
  
## <a name="asymmetric-keys"></a>非對稱金鑰

 .NET 提供 <xref:System.Security.Cryptography.RSA> 非對稱式加密的類別。 當您使用無參數 `Create()` 方法來建立新的實例時，這個類別會建立公開/私密金鑰組。 非對稱金鑰可以儲存以用於多個工作階段，或只針對一個工作階段而產生。 雖然公開金鑰可以公開提供使用，但應該小心地看護私密金鑰。  
  
 每當建立非對稱式演算法類別的新執行個體時，就會產生公開/私密金鑰組。 建立類別的新實例之後，您可以使用方法來解壓縮金鑰資訊，此方法會傳回 <xref:System.Security.Cryptography.RSA.ExportParameters%2A> <xref:System.Security.Cryptography.RSAParameters> 保存金鑰資訊的結構。 此方法會接受布林值，指出是否只傳回公開金鑰資訊，或傳回公開金鑰和私密金鑰資訊。

另外還有其他方法可讓您解壓縮重要資訊，例如：

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

您可以使用方法，將 **RSA** 實例初始化為 **RSAParameters** 結構的值 <xref:System.Security.Cryptography.RSA.ImportParameters%2A> 。 或使用方法建立新的實例 <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> 。  
  
 非對稱私密金鑰不應逐字或以純文字儲存到本機電腦上。 如果您需要儲存私密金鑰，您應該使用金鑰容器。 如需如何在金鑰容器中儲存私密金鑰的詳細資訊，請參閱作法 [：將非對稱金鑰儲存在金鑰容器中](how-to-store-asymmetric-keys-in-a-key-container.md)。  
  
 下列程式碼範例會建立 **RSA** 類別的新實例、建立公開/私密金鑰組，並將公開金鑰資訊儲存至 **RSAParameters** 結構。  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSA = RSA.Create()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSA rsa = RSA.Create();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a>另請參閱

- [加密資料](encrypting-data.md)
- [解密資料](decrypting-data.md)
- [密碼編譯服務](cryptographic-services.md)
- [作法：將對稱金鑰儲存在金鑰容器中](how-to-store-asymmetric-keys-in-a-key-container.md)
- [跨平臺密碼編譯](cross-platform-cryptography.md)
- [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)
