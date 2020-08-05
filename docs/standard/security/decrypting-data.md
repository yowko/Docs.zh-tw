---
title: 解密資料
description: 瞭解如何在 .NET 中使用對稱演算法或非對稱演算法來解密資料。
ms.date: 07/16/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 2ba4c3ba43d688aeb66c67ec3f94f4a503d47892
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556978"
---
# <a name="decrypting-data"></a><span data-ttu-id="48253-103">解密資料</span><span class="sxs-lookup"><span data-stu-id="48253-103">Decrypting Data</span></span>

<span data-ttu-id="48253-104">解密是加密的反向作業。</span><span class="sxs-lookup"><span data-stu-id="48253-104">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="48253-105">針對秘密金鑰加密，您必須同時知道金鑰和用來加密資料的 IV。</span><span class="sxs-lookup"><span data-stu-id="48253-105">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="48253-106">針對公開金鑰加密，您必須知道公開金鑰 (如果使用私密金鑰來加密資料) 或私密金鑰 (如果使用公開金鑰來加密資料)。</span><span class="sxs-lookup"><span data-stu-id="48253-106">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="48253-107">對稱解密</span><span class="sxs-lookup"><span data-stu-id="48253-107">Symmetric Decryption</span></span>

<span data-ttu-id="48253-108">以對稱演算法加密的資料解密類似於用來以對稱演算法加密資料的程序。</span><span class="sxs-lookup"><span data-stu-id="48253-108">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="48253-109"><xref:System.Security.Cryptography.CryptoStream>類別會與 .net 所提供的對稱式密碼編譯類別搭配使用，以解密從任何 managed 資料流程物件讀取的資料。</span><span class="sxs-lookup"><span data-stu-id="48253-109">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by .NET to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="48253-110">下列範例說明如何為演算法建立預設實值類別的新實例 <xref:System.Security.Cryptography.Aes> 。</span><span class="sxs-lookup"><span data-stu-id="48253-110">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="48253-111">實例是用來在物件上執行解密 <xref:System.Security.Cryptography.CryptoStream> 。</span><span class="sxs-lookup"><span data-stu-id="48253-111">The instance is used to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="48253-112">這個範例會先建立**Aes**實作為類別的新實例。</span><span class="sxs-lookup"><span data-stu-id="48253-112">This example first creates a new instance of the **Aes** implementation class.</span></span> <span data-ttu-id="48253-113">接下來它會建立 **CryptoStream** 物件，並將它初始化為稱為 `myStream`的 Managed 資料流的值。</span><span class="sxs-lookup"><span data-stu-id="48253-113">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `myStream`.</span></span> <span data-ttu-id="48253-114">接下來，會傳遞**Aes**類別的**CreateDecryptor**方法與用於加密的相同金鑰和 IV，然後傳遞至**CryptoStream**的函式。</span><span class="sxs-lookup"><span data-stu-id="48253-114">Next, the **CreateDecryptor** method from the **Aes** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span>

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

<span data-ttu-id="48253-115">下列範例顯示建立資料流、解密資料流、從資料流讀取，然後關閉資料流的整個程序。</span><span class="sxs-lookup"><span data-stu-id="48253-115">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="48253-116">隨即建立一個檔案資料流程物件，它會讀取名為*TestData.txt*的檔案。</span><span class="sxs-lookup"><span data-stu-id="48253-116">A file stream object is created that reads a file named *TestData.txt*.</span></span> <span data-ttu-id="48253-117">接著會使用**CryptoStream**類別和**Aes**類別來解密檔案資料流程。</span><span class="sxs-lookup"><span data-stu-id="48253-117">The file stream is then decrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="48253-118">這個範例會指定用來[加密資料](encrypting-data.md)的對稱式加密範例中所使用的金鑰和 IV 值。</span><span class="sxs-lookup"><span data-stu-id="48253-118">This example specifies key and IV values that are used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="48253-119">它不會顯示加密和傳輸這些值所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="48253-119">It does not show the code needed to encrypt and transfer these values.</span></span>

```vb
Imports System
Imports System.IO
Imports System.Security.Cryptography

Module Module1
    Sub Main()
            'The key and IV must be the same values that were used
            'to encrypt the stream.
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Create a file stream.
            Dim myStream As FileStream = new FileStream("TestData.txt", FileMode.Open)

            'Create a new instance of the default Aes implementation class
            'and decrypt the stream.
            Dim aes As Aes = Aes.Create()

            'Create an instance of the CryptoStream class, pass it the file stream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            myStream.Close()
            'Catch any exceptions.
        Catch
            Console.WriteLine("The decryption Failed.")
            Throw
        End Try
    End Sub
End Module
```

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

class Class1
{
    static void Main(string[] args)
    {
        //The key and IV must be the same values that were used
        //to encrypt the stream.
        byte[] key = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        byte[] iv = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        try
        {
            //Create a file stream.
            FileStream myStream = new FileStream("TestData.txt", FileMode.Open);

            //Create a new instance of the default Aes implementation class
            Aes aes = Aes.Create();

            //Create a CryptoStream, pass it the file stream, and decrypt
            //it with the Aes class using the key and IV.
            CryptoStream cryptStream = new CryptoStream(
               myStream,
               aes.CreateDecryptor(key, iv),
               CryptoStreamMode.Read);

            //Read the stream.
            StreamReader sReader = new StreamReader(cryptStream);

            //Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

            //Close the streams.
            sReader.Close();
            myStream.Close();
        }
        //Catch any exceptions.
        catch
        {
            Console.WriteLine("The decryption failed.");
            throw;
        }
    }
}
```

<span data-ttu-id="48253-120">上述範例使用對稱式加密範例中使用的相同金鑰、IV 和演算法來[加密資料](encrypting-data.md)。</span><span class="sxs-lookup"><span data-stu-id="48253-120">The preceding example uses the same key, IV, and algorithm used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="48253-121">它會解密該範例所建立的*TestData.txt*檔案，並在主控台上顯示原始文字。</span><span class="sxs-lookup"><span data-stu-id="48253-121">It decrypts the *TestData.txt* file that is created by that example and displays the original text on the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="48253-122">非對稱解密</span><span class="sxs-lookup"><span data-stu-id="48253-122">Asymmetric Decryption</span></span>

<span data-ttu-id="48253-123">一般而言，有一方 (A 方) 會同時產生公開和私密金鑰，並將金鑰儲存在記憶體或密碼編譯金鑰容器中。</span><span class="sxs-lookup"><span data-stu-id="48253-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="48253-124">A 方接著會將公開金鑰傳送給另一方 (B 方)。</span><span class="sxs-lookup"><span data-stu-id="48253-124">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="48253-125">使用公開金鑰時，合作物件 B 會加密資料，並將資料傳回給合作物件 A。在收到資料之後，合作物件 A 會使用對應的私密金鑰來解密它。</span><span class="sxs-lookup"><span data-stu-id="48253-125">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="48253-126">只有在 A 方使用的私密金鑰對應於 B 方用來加密資料的公開金鑰時，解密才會成功。</span><span class="sxs-lookup"><span data-stu-id="48253-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="48253-127">如需如何在安全的密碼編譯金鑰容器儲存非對稱金鑰，以及稍後如何擷取非對稱金鑰的相關資訊，請參閱 [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md)。</span><span class="sxs-lookup"><span data-stu-id="48253-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="48253-128">下列範例說明代表對稱金鑰和 IV 的兩個位元組陣列的解密。</span><span class="sxs-lookup"><span data-stu-id="48253-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="48253-129">如需如何從 <xref:System.Security.Cryptography.RSA> 物件擷取非對稱式公開金鑰，且使用的格式可以輕鬆地傳送給第三方的相關資訊，請參閱 [Encrypting Data](encrypting-data.md)的 Managed 資料流的值。</span><span class="sxs-lookup"><span data-stu-id="48253-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSA> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="48253-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48253-130">See also</span></span>

- [<span data-ttu-id="48253-131">產生加密和解密金鑰</span><span class="sxs-lookup"><span data-stu-id="48253-131">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="48253-132">加密資料</span><span class="sxs-lookup"><span data-stu-id="48253-132">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="48253-133">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="48253-133">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="48253-134">密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="48253-134">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="48253-135">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="48253-135">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="48253-136">使用填補進行 CBC 模式對稱解密的時間弱點</span><span class="sxs-lookup"><span data-stu-id="48253-136">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="48253-137">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="48253-137">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
