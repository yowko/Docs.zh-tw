---
title: 加密資料
description: 瞭解如何使用對稱演算法或非對稱演算法來加密 .NET 中的資料。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], symmetric
- symmetric encryption
- cryptography [.NET], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 574ef3f829406d661e19f004e9a7d150954fd9e5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830593"
---
# <a name="encrypting-data"></a><span data-ttu-id="0e765-103">加密資料</span><span class="sxs-lookup"><span data-stu-id="0e765-103">Encrypting Data</span></span>

<span data-ttu-id="0e765-104">對稱式加密和非對稱式加密是使用不同的程序執行。</span><span class="sxs-lookup"><span data-stu-id="0e765-104">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="0e765-105">對稱式加密在資料流上執行，因此適用於加密大量資料。</span><span class="sxs-lookup"><span data-stu-id="0e765-105">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="0e765-106">非對稱式加密在少數的位元組上執行，因此只適用於小量的資料。</span><span class="sxs-lookup"><span data-stu-id="0e765-106">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="0e765-107">對稱加密</span><span class="sxs-lookup"><span data-stu-id="0e765-107">Symmetric Encryption</span></span>  

<span data-ttu-id="0e765-108">Managed 對稱式密碼編譯類別可搭配特殊的資料流類別，稱為 <xref:System.Security.Cryptography.CryptoStream> ，它會加密讀入資料流的資料。</span><span class="sxs-lookup"><span data-stu-id="0e765-108">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="0e765-109">**CryptoStream** 類別是以 managed 資料流程類別初始化，而此類別會執行 <xref:System.Security.Cryptography.ICryptoTransform> 介面 (從實) 中執行密碼編譯演算法的類別建立），以及 <xref:System.Security.Cryptography.CryptoStreamMode> 描述允許 **CryptoStream** 的存取類型的列舉。</span><span class="sxs-lookup"><span data-stu-id="0e765-109">The **CryptoStream** class is initialized with a managed stream class, a class that implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="0e765-110">**CryptoStream** 類別可以使用衍生自類別的任何類別初始化 <xref:System.IO.Stream> ，包括 <xref:System.IO.FileStream> 、 <xref:System.IO.MemoryStream> 和 <xref:System.Net.Sockets.NetworkStream> 。</span><span class="sxs-lookup"><span data-stu-id="0e765-110">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="0e765-111">使用這些類別，您可以在各種不同的資料流物件上執行對稱式加密。</span><span class="sxs-lookup"><span data-stu-id="0e765-111">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
<span data-ttu-id="0e765-112">下列範例說明如何為演算法建立預設實類別的新實例 <xref:System.Security.Cryptography.Aes> 。</span><span class="sxs-lookup"><span data-stu-id="0e765-112">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="0e765-113">實例用來對 **CryptoStream** 類別執行加密。</span><span class="sxs-lookup"><span data-stu-id="0e765-113">The instance is used to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="0e765-114">在此範例中， **CryptoStream** 以稱為 `myStream` 的資料流物件初始化，它是任何類型的 Managed 資料流。</span><span class="sxs-lookup"><span data-stu-id="0e765-114">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="0e765-115">**Aes** 類別的 **CreateEncryptor** 方法會傳遞加密所使用的金鑰和 IV。</span><span class="sxs-lookup"><span data-stu-id="0e765-115">The **CreateEncryptor** method from the **Aes** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="0e765-116">在此情況下，會使用從 `aes` 產生的預設金鑰和 IV。</span><span class="sxs-lookup"><span data-stu-id="0e765-116">In this case, the default key and IV generated from `aes` are used.</span></span>
  
```vb  
Dim aes As Aes = Aes.Create()  
Dim cryptStream As New CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
```  
  
```csharp  
Aes aes = Aes.Create();  
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write);  
```  
  
<span data-ttu-id="0e765-117">執行此程式碼之後，寫入 **CryptoStream** 物件的任何資料都會使用 AES 演算法進行加密。</span><span class="sxs-lookup"><span data-stu-id="0e765-117">After this code is executed, any data written to the **CryptoStream** object is encrypted using the AES algorithm.</span></span>  
  
<span data-ttu-id="0e765-118">下列範例顯示建立資料流、加密資料流、寫入資料流，然後關閉資料流的整個程序。</span><span class="sxs-lookup"><span data-stu-id="0e765-118">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="0e765-119">這個範例會建立使用 **CryptoStream** 類別和 **Aes** 類別加密的檔案資料流程。</span><span class="sxs-lookup"><span data-stu-id="0e765-119">This example creates a file stream that is encrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="0e765-120">產生的 IV 會寫入至的開頭 <xref:System.IO.FileStream> ，因此可供讀取和用於解密。</span><span class="sxs-lookup"><span data-stu-id="0e765-120">Generated IV is written to beginning of <xref:System.IO.FileStream>, so it can be read and used for decryption.</span></span> <span data-ttu-id="0e765-121">然後會使用類別，將訊息寫入至加密的資料流程 <xref:System.IO.StreamWriter> 。</span><span class="sxs-lookup"><span data-stu-id="0e765-121">Then a message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="0e765-122">雖然可以多次使用相同的金鑰來加密和解密資料，但建議您每次都產生新的隨機 IV。</span><span class="sxs-lookup"><span data-stu-id="0e765-122">While the same key can be used multiple times to encrypt and decrypt data, it is recommended to generate a new random IV each time.</span></span> <span data-ttu-id="0e765-123">如此一來，加密資料一律會不同，即使純文字相同也一樣。</span><span class="sxs-lookup"><span data-stu-id="0e765-123">This way the encrypted data is always different, even when plain text is the same.</span></span>
  
:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

<span data-ttu-id="0e765-124">程式碼會使用 AES 對稱演算法來加密資料流，並寫入 IV 然後加密 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="0e765-124">The code encrypts the stream using the AES symmetric algorithm, and writes IV and then encrypted "Hello World!"</span></span> <span data-ttu-id="0e765-125">寫入此資料流。</span><span class="sxs-lookup"><span data-stu-id="0e765-125">to the stream.</span></span> <span data-ttu-id="0e765-126">如果程式碼成功，它會建立名為 *TestData.txt* 的加密檔案，並在主控台中顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="0e765-126">If the code is successful, it creates an encrypted file named *TestData.txt* and displays the following text to the console:</span></span>
  
```console  
The text was encrypted.
```  

<span data-ttu-id="0e765-127">您可以使用對稱解密範例解密 [資料](decrypting-data.md)來解密檔案。</span><span class="sxs-lookup"><span data-stu-id="0e765-127">You can decrypt the file by using the symmetric decryption example in [Decrypting Data](decrypting-data.md).</span></span> <span data-ttu-id="0e765-128">該範例和這個範例會指定相同的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0e765-128">That example and this example specify the same key.</span></span>

<span data-ttu-id="0e765-129">但是，如果引發例外狀況，程式碼會在主控台中顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="0e765-129">However, if an exception is raised, the code displays the following text to the console:</span></span>
  
```console  
The encryption failed.
```

## <a name="asymmetric-encryption"></a><span data-ttu-id="0e765-130">非對稱加密</span><span class="sxs-lookup"><span data-stu-id="0e765-130">Asymmetric Encryption</span></span>

<span data-ttu-id="0e765-131">非對稱演算法通常用來加密少量的資料，例如對稱金鑰和 IV 的加密。</span><span class="sxs-lookup"><span data-stu-id="0e765-131">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="0e765-132">一般來說，個別的執行中非對稱式加密會使用另一個合作對象所產生的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="0e765-132">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="0e765-133"><xref:System.Security.Cryptography.RSA>此類別是由 .net 針對此目的提供。</span><span class="sxs-lookup"><span data-stu-id="0e765-133">The <xref:System.Security.Cryptography.RSA> class is provided by .NET for this purpose.</span></span>  
  
<span data-ttu-id="0e765-134">下列範例會使用公開金鑰資訊來加密對稱金鑰和 IV。</span><span class="sxs-lookup"><span data-stu-id="0e765-134">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="0e765-135">會初始化兩個代表第三方的公開金鑰的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="0e765-135">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="0e765-136"><xref:System.Security.Cryptography.RSAParameters> 物件會初始化為這些值。</span><span class="sxs-lookup"><span data-stu-id="0e765-136">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="0e765-137">接下來， **RSAParameters** 物件 (，以及它所代表的公開金鑰，) 會使用方法匯入到 **RSA** 實例中 <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0e765-137">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSA** instance using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0e765-138">最後，由類別建立的私密金鑰和 IV <xref:System.Security.Cryptography.Aes> 都會加密。</span><span class="sxs-lookup"><span data-stu-id="0e765-138">Finally, the private key and IV created by an <xref:System.Security.Cryptography.Aes> class are encrypted.</span></span> <span data-ttu-id="0e765-139">此範例會要求系統安裝 128 位元加密。</span><span class="sxs-lookup"><span data-stu-id="0e765-139">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System
Imports System.Security.Cryptography

Module Module1

    Sub Main()
        'Initialize the byte arrays to the public key information.  
        Dim modulus As Byte() = {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19, 202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}

        Dim exponent As Byte() = {1, 0, 1}

        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte
        Dim encryptedSymmetricIV() As Byte

        'Create a new instance of the default RSA implementation class.
        Dim rsa As RSA = RSA.Create()

        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()

        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus
        rsaKeyInfo.Exponent = exponent

        'Import key parameters into rsa
        rsa.ImportParameters(rsaKeyInfo)

        'Create a new instance of the default Aes implementation class.  
        Dim aes As Aes = Aes.Create()

        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1)
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1)
    End Sub

End Module
```  
  
```csharp  
using System;
using System.Security.Cryptography;

class Class1
{
    static void Main()
    {
        //Initialize the byte arrays to the public key information.  
        byte[] modulus = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};

        byte[] exponent = { 1, 0, 1 };

        //Create values to store encrypted symmetric keys.  
        byte[] encryptedSymmetricKey;
        byte[] encryptedSymmetricIV;

        //Create a new instance of the RSA class.  
        RSA rsa = RSA.Create();

        //Create a new instance of the RSAParameters structure.  
        RSAParameters rsaKeyInfo = new RSAParameters();

        //Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus;
        rsaKeyInfo.Exponent = exponent;

        //Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo);

        //Create a new instance of the default Aes implementation class.  
        Aes aes = Aes.Create();

        //Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1);
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="0e765-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e765-140">See also</span></span>

- [<span data-ttu-id="0e765-141">產生加密和解密金鑰</span><span class="sxs-lookup"><span data-stu-id="0e765-141">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="0e765-142">解密資料</span><span class="sxs-lookup"><span data-stu-id="0e765-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="0e765-143">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="0e765-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="0e765-144">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="0e765-144">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="0e765-145">使用填補進行 CBC 模式對稱解密的時間弱點</span><span class="sxs-lookup"><span data-stu-id="0e765-145">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="0e765-146">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="0e765-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
