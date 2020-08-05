---
title: 產生加密和解密金鑰
description: 瞭解如何在 .NET 中建立和管理對稱和非對稱金鑰，以進行加密和解密。
ms.date: 07/14/2020
ms.technology: dotnet-standard
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
ms.openlocfilehash: 7ce19dc465fb1fac22545398e0724e6b76dd7098
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556939"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="bfd3c-103">產生加密和解密金鑰</span><span class="sxs-lookup"><span data-stu-id="bfd3c-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="bfd3c-104">建立和管理金鑰是密碼編譯程序中很重要的一部分。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="bfd3c-105">對稱演算法需要建立金鑰和初始化向量 (IV)。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="bfd3c-106">務必不要對不該解密您資料的任何人透露金鑰。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="bfd3c-107">IV 不需要加密，但是應該針對每個工作階段變更。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="bfd3c-108">非對稱演算法需要建立公開金鑰和私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="bfd3c-109">公開金鑰可以公開給任何人，但私密金鑰必須只有將解密以公開金鑰加密之資料的一方知道。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="bfd3c-110">本節描述如何產生及管理對稱和非對稱演算法的金鑰。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="bfd3c-111">對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="bfd3c-111">Symmetric Keys</span></span>  
 <span data-ttu-id="bfd3c-112">.NET 所提供的對稱式加密類別需要金鑰和新的初始化向量 (IV) 來加密和解密資料。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-112">The symmetric encryption classes supplied by .NET require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="bfd3c-113">每當您使用無參數方法建立其中一個 managed 對稱密碼編譯類別的新實例時 `Create()` ，就會自動建立新的金鑰和 IV。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless `Create()` method, a new key and IV are automatically created.</span></span> <span data-ttu-id="bfd3c-114">您允許解密資料的任何人都必須擁有相同的金鑰和 IV，並使用相同的演算法。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="bfd3c-115">一般而言，應該為每個工作階段建立新的金鑰和 IV，且金鑰和 IV 都不應該儲存以用於稍後的工作階段。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="bfd3c-116">若要與遠端的一方溝通對稱金鑰和 IV，通常會使用非對稱加密來加密對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="bfd3c-117">在不安全的網路中傳送未加密的金鑰並不安全，因為任何人只要攔截金鑰和 IV，就可以解密您的資料。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span>  
  
 <span data-ttu-id="bfd3c-118">下列範例會示範如何建立演算法之預設實值類別的新實例 <xref:System.Security.Cryptography.Aes> 。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-118">The following example shows the creation of a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span>  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 <span data-ttu-id="bfd3c-119">先前的程式碼執行時，會產生新的金鑰和 IV 並分別放在 **Key** 和 **IV** 屬性。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="bfd3c-120">有時候您可能需要產生多個金鑰。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="bfd3c-121">在此情況下，您可以建立實作對稱演算法之類別的新執行個體，然後呼叫 **GenerateKey** 和 **GenerateIV** 方法來建立新的金鑰和 IV。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="bfd3c-122">下列程式碼範例說明如何在建立對稱密碼編譯類別的新實例之後，建立新的金鑰和 Iv。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
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
  
 <span data-ttu-id="bfd3c-123">執行上述程式碼時，會在建立新的**Aes**實例時產生金鑰和 IV。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-123">When the preceding code is executed, a key and IV are generated when the new instance of **Aes** is made.</span></span> <span data-ttu-id="bfd3c-124">呼叫 **GenerateKey** 和 **GenerateIV** 方法時，會建立另一個金鑰和 IV。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>
  
## <a name="asymmetric-keys"></a><span data-ttu-id="bfd3c-125">非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="bfd3c-125">Asymmetric Keys</span></span>

 <span data-ttu-id="bfd3c-126">.NET 提供 <xref:System.Security.Cryptography.RSA> 非對稱式加密的類別。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-126">.NET provides the <xref:System.Security.Cryptography.RSA> class for asymmetric encryption.</span></span> <span data-ttu-id="bfd3c-127">當您使用無參數 `Create()` 方法建立新的實例時，這個類別會建立公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-127">This class creates a public/private key pair when you use the parameterless `Create()` method to create a new instance.</span></span> <span data-ttu-id="bfd3c-128">非對稱金鑰可以儲存以用於多個工作階段，或只針對一個工作階段而產生。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="bfd3c-129">雖然公開金鑰可以公開提供使用，但應該小心地看護私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="bfd3c-130">每當建立非對稱式演算法類別的新執行個體時，就會產生公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="bfd3c-131">建立類別的新實例之後，可以使用方法來解壓縮金鑰資訊，這會傳回 <xref:System.Security.Cryptography.RSA.ExportParameters%2A> <xref:System.Security.Cryptography.RSAParameters> 保存金鑰資訊的結構。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-131">After a new instance of the class is created, the key information can be extracted using the <xref:System.Security.Cryptography.RSA.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span> <span data-ttu-id="bfd3c-132">此方法會接受布林值，指出是否只傳回公開金鑰資訊，或傳回公開金鑰和私密金鑰資訊。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-132">The method accepts a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span>

<span data-ttu-id="bfd3c-133">還有其他方法可讓您解壓縮重要資訊，例如：</span><span class="sxs-lookup"><span data-stu-id="bfd3c-133">There are also other methods that let you extract key information, such as:</span></span>

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

<span data-ttu-id="bfd3c-134">您可以使用方法，將**RSA**實例初始化為**RSAParameters**結構的值 <xref:System.Security.Cryptography.RSA.ImportParameters%2A> 。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-134">An **RSA** instance can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A> method.</span></span> <span data-ttu-id="bfd3c-135">或使用方法建立新的實例 <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-135">Or create a new instance by using the <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="bfd3c-136">非對稱私密金鑰不應逐字或以純文字儲存到本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="bfd3c-137">如果您需要儲存私密金鑰，您應該使用金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="bfd3c-138">如需如何將私密金鑰儲存在金鑰容器中的詳細資訊，請參閱[如何：將非對稱金鑰儲存在金鑰容器中](how-to-store-asymmetric-keys-in-a-key-container.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-138">For more information about how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="bfd3c-139">下列程式碼範例會建立**RSA**類別的新實例、建立公開/私密金鑰組，並將公開金鑰資訊儲存至**RSAParameters**結構。</span><span class="sxs-lookup"><span data-stu-id="bfd3c-139">The following code example creates a new instance of the **RSA** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bfd3c-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfd3c-140">See also</span></span>

- [<span data-ttu-id="bfd3c-141">加密資料</span><span class="sxs-lookup"><span data-stu-id="bfd3c-141">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="bfd3c-142">解密資料</span><span class="sxs-lookup"><span data-stu-id="bfd3c-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="bfd3c-143">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="bfd3c-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="bfd3c-144">作法：將對稱金鑰儲存在金鑰容器中</span><span class="sxs-lookup"><span data-stu-id="bfd3c-144">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
- [<span data-ttu-id="bfd3c-145">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="bfd3c-145">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="bfd3c-146">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="bfd3c-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
