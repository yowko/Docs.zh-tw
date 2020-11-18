---
title: 解密資料
description: 瞭解如何使用對稱演算法或非對稱演算法來解密 .NET 中的資料。
ms.date: 07/16/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: cf286eeca8a9372c6532c56701e4775d5e09d786
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831100"
---
# <a name="decrypting-data"></a><span data-ttu-id="3ce5b-103">解密資料</span><span class="sxs-lookup"><span data-stu-id="3ce5b-103">Decrypting Data</span></span>

<span data-ttu-id="3ce5b-104">解密是加密的反向作業。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-104">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="3ce5b-105">針對秘密金鑰加密，您必須同時知道金鑰和用來加密資料的 IV。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-105">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="3ce5b-106">針對公開金鑰加密，您必須知道公開金鑰 (如果使用私密金鑰來加密資料) 或私密金鑰 (如果使用公開金鑰來加密資料)。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-106">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="3ce5b-107">對稱解密</span><span class="sxs-lookup"><span data-stu-id="3ce5b-107">Symmetric Decryption</span></span>

<span data-ttu-id="3ce5b-108">以對稱演算法加密的資料解密類似於用來以對稱演算法加密資料的程序。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-108">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="3ce5b-109"><xref:System.Security.Cryptography.CryptoStream>類別會搭配 .net 提供的對稱式密碼編譯類別使用，以解密從任何 managed 資料流程物件讀取的資料。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-109">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by .NET to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="3ce5b-110">下列範例說明如何為演算法建立預設實類別的新實例 <xref:System.Security.Cryptography.Aes> 。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-110">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="3ce5b-111">實例用來對物件執行解密 <xref:System.Security.Cryptography.CryptoStream> 。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-111">The instance is used to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="3ce5b-112">此範例會先建立實類別的新實例 <xref:System.Security.Cryptography.Aes> 。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-112">This example first creates a new instance of the <xref:System.Security.Cryptography.Aes> implementation class.</span></span> <span data-ttu-id="3ce5b-113">它會從 managed 資料流程變數中讀取 (IV) 值的初始化向量 `myStream` 。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-113">It reads the initialization vector (IV) value from a managed stream variable, `myStream`.</span></span> <span data-ttu-id="3ce5b-114">接下來它會具現化 <xref:System.Security.Cryptography.CryptoStream> 物件，並將它初始化為實例的值 `myStream` 。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-114">Next it instantiates a <xref:System.Security.Cryptography.CryptoStream> object and initializes it to the value of the `myStream` instance.</span></span> <span data-ttu-id="3ce5b-115"><xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType>實例中的方法 <xref:System.Security.Cryptography.Aes> 會傳遞 IV 值和用於加密的相同金鑰。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-115">The <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> method from the <xref:System.Security.Cryptography.Aes> instance is passed the IV value and the same key that was used for encryption.</span></span>

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

<span data-ttu-id="3ce5b-116">下列範例顯示建立資料流、解密資料流、從資料流讀取，然後關閉資料流的整個程序。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-116">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="3ce5b-117">建立的檔案資料流程物件會讀取名為 *TestData.txt* 的檔案。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-117">A file stream object is created that reads a file named *TestData.txt*.</span></span> <span data-ttu-id="3ce5b-118">接著會使用 **CryptoStream** 類別和 **Aes** 類別來解密檔案資料流程。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-118">The file stream is then decrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="3ce5b-119">此範例會指定用於 [加密資料](encrypting-data.md)的對稱式加密範例中所使用的金鑰值。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-119">This example specifies key value that is used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="3ce5b-120">它不會顯示加密和傳輸這些值所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-120">It does not show the code needed to encrypt and transfer these values.</span></span>

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

<span data-ttu-id="3ce5b-121">上述範例使用相同的金鑰，以及用於對稱式加密範例中的演算法來 [加密資料](encrypting-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-121">The preceding example uses the same key, and algorithm used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="3ce5b-122">它會將此範例所建立的 *TestData.txt* 檔案解密，並在主控台上顯示原始文字。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-122">It decrypts the *TestData.txt* file that is created by that example and displays the original text on the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="3ce5b-123">非對稱解密</span><span class="sxs-lookup"><span data-stu-id="3ce5b-123">Asymmetric Decryption</span></span>

<span data-ttu-id="3ce5b-124">一般而言，有一方 (A 方) 會同時產生公開和私密金鑰，並將金鑰儲存在記憶體或密碼編譯金鑰容器中。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-124">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="3ce5b-125">A 方接著會將公開金鑰傳送給另一方 (B 方)。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-125">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="3ce5b-126">使用公開金鑰時，合作物件 B 會將資料加密，並將資料傳送回第 A 方。收到資料之後，合作物件 A 會使用對應的私密金鑰將它解密。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-126">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="3ce5b-127">只有在 A 方使用的私密金鑰對應於 B 方用來加密資料的公開金鑰時，解密才會成功。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-127">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="3ce5b-128">如需如何在安全的密碼編譯金鑰容器儲存非對稱金鑰，以及稍後如何擷取非對稱金鑰的相關資訊，請參閱 [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-128">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="3ce5b-129">下列範例說明代表對稱金鑰和 IV 的兩個位元組陣列的解密。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-129">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="3ce5b-130">如需如何從 <xref:System.Security.Cryptography.RSA> 物件擷取非對稱式公開金鑰，且使用的格式可以輕鬆地傳送給第三方的相關資訊，請參閱 [Encrypting Data](encrypting-data.md)的 Managed 資料流的值。</span><span class="sxs-lookup"><span data-stu-id="3ce5b-130">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSA> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a><span data-ttu-id="3ce5b-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce5b-131">See also</span></span>

- [<span data-ttu-id="3ce5b-132">產生加密和解密金鑰</span><span class="sxs-lookup"><span data-stu-id="3ce5b-132">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="3ce5b-133">加密資料</span><span class="sxs-lookup"><span data-stu-id="3ce5b-133">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="3ce5b-134">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="3ce5b-134">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="3ce5b-135">密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="3ce5b-135">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="3ce5b-136">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="3ce5b-136">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="3ce5b-137">使用填補進行 CBC 模式對稱解密的時間弱點</span><span class="sxs-lookup"><span data-stu-id="3ce5b-137">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="3ce5b-138">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="3ce5b-138">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
