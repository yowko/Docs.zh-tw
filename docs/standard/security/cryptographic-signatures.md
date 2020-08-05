---
title: 密碼編譯簽章
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET], signatures
- security [.NET], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: ce2be1d509da4e399bf87e1c8df7ba061fc2707c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557004"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="6af32-102">密碼編譯簽章</span><span class="sxs-lookup"><span data-stu-id="6af32-102">Cryptographic Signatures</span></span>

<span data-ttu-id="6af32-103">密碼編譯數位簽章會使用公開金鑰演算法來提供資料完整性。</span><span class="sxs-lookup"><span data-stu-id="6af32-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="6af32-104">當您使用數位簽章簽署資料時，其他人可以確認簽章，並可以證明資料是來自您，而且在您簽署它之後沒有遭到竄改。</span><span class="sxs-lookup"><span data-stu-id="6af32-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="6af32-105">如需有關數位簽章的詳細資訊，請參閱 [The signature is valid](cryptographic-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6af32-105">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="6af32-106">本主題說明如何使用 <xref:System.Security.Cryptography> 命名空間中的類別產生及驗證數位簽章。</span><span class="sxs-lookup"><span data-stu-id="6af32-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="6af32-107">產生簽章</span><span class="sxs-lookup"><span data-stu-id="6af32-107">Generating Signatures</span></span>

<span data-ttu-id="6af32-108">數位簽章通常適用於代表較大資料的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="6af32-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="6af32-109">下列範例會將數位簽章套用到雜湊值。</span><span class="sxs-lookup"><span data-stu-id="6af32-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="6af32-110">首先，會建立 <xref:System.Security.Cryptography.RSA> 類別的新執行個體，來產生公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="6af32-110">First, a new instance of the <xref:System.Security.Cryptography.RSA> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="6af32-111">接著， <xref:System.Security.Cryptography.RSA> 會傳遞至 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="6af32-111">Next, the <xref:System.Security.Cryptography.RSA> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="6af32-112">如此會將私密金鑰轉移給 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>，它會實際執行數位簽署。</span><span class="sxs-lookup"><span data-stu-id="6af32-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="6af32-113">在您可以簽署雜湊碼之前，必須先指定要使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="6af32-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="6af32-114">此範例使用 SHA1 演算法。</span><span class="sxs-lookup"><span data-stu-id="6af32-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="6af32-115">最後，會呼叫 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> 方法來執行簽章。</span><span class="sxs-lookup"><span data-stu-id="6af32-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="6af32-116">由於 SHA1 的衝突問題，我們建議 SHA256 或更好。</span><span class="sxs-lookup"><span data-stu-id="6af32-116">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As RSA = RSA.Create()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSA instance to transfer the private key.
        Dim rsaFormatter As New RSAPKCS1SignatureFormatter(rsa)

        'Set the hash algorithm to SHA1.
        rsaFormatter.SetHashAlgorithm("SHA1")

        'Create a signature for hashValue and assign it to
        'signedHashValue.
        signedHashValue = rsaFormatter.CreateSignature(hashValue)
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
      //The hash value to sign.
      byte[] hashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};

      //The value to hold the signed value.
      byte[] signedHashValue;

      //Generate a public/private key pair.
      RSA rsa = RSA.Create();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSA instance to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

## <a name="verifying-signatures"></a><span data-ttu-id="6af32-117">驗證簽章</span><span class="sxs-lookup"><span data-stu-id="6af32-117">Verifying Signatures</span></span>

<span data-ttu-id="6af32-118">若要驗證資料是由特定合作對象簽署，您必須擁有下列資訊：</span><span class="sxs-lookup"><span data-stu-id="6af32-118">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="6af32-119">簽章資料之合作對象的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="6af32-119">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="6af32-120">數位簽章。</span><span class="sxs-lookup"><span data-stu-id="6af32-120">The digital signature.</span></span>

- <span data-ttu-id="6af32-121">已簽署的資料。</span><span class="sxs-lookup"><span data-stu-id="6af32-121">The data that was signed.</span></span>

- <span data-ttu-id="6af32-122">簽署人使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="6af32-122">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="6af32-123">若要驗證 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 類別所簽署的簽章，請使用 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 類別。</span><span class="sxs-lookup"><span data-stu-id="6af32-123">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="6af32-124">必須提供 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 類別簽署者的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="6af32-124">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="6af32-125">針對 RSA，您將需要模數的值和指數來指定公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="6af32-125">For RSA, you will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="6af32-126"> (產生公開/私密金鑰組的合作物件應該提供這些值。 ) 先建立一個用 <xref:System.Security.Cryptography.RSA> 來保存公開金鑰的物件，以驗證簽章，然後將 <xref:System.Security.Cryptography.RSAParameters> 結構初始化為指定公開金鑰的模數和指數值。</span><span class="sxs-lookup"><span data-stu-id="6af32-126">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSA> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="6af32-127">下列程式碼顯示如何建立 <xref:System.Security.Cryptography.RSAParameters> 結構。</span><span class="sxs-lookup"><span data-stu-id="6af32-127">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="6af32-128">`Modulus` 屬性設定為 `modulusData` 位元組陣列的值，而 `Exponent` 屬性設定為 `exponentData`位元組陣列的值。</span><span class="sxs-lookup"><span data-stu-id="6af32-128">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

```vb
Dim rsaKeyInfo As RSAParameters
rsaKeyInfo.Modulus = modulusData
rsaKeyInfo.Exponent = exponentData
```

```csharp
RSAParameters rsaKeyInfo;
rsaKeyInfo.Modulus = modulusData;
rsaKeyInfo.Exponent = exponentData;
```

<span data-ttu-id="6af32-129">建立 <xref:System.Security.Cryptography.RSAParameters> 物件之後，您可以將實類別的新實例初始化 <xref:System.Security.Cryptography.RSA> 為中指定的值 <xref:System.Security.Cryptography.RSAParameters> 。</span><span class="sxs-lookup"><span data-stu-id="6af32-129">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSA> implementation class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="6af32-130"><xref:System.Security.Cryptography.RSA>接著，實例會傳遞至的函式， <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 以傳輸金鑰。</span><span class="sxs-lookup"><span data-stu-id="6af32-130">The <xref:System.Security.Cryptography.RSA> instance is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="6af32-131">下列範例將說明此程序。</span><span class="sxs-lookup"><span data-stu-id="6af32-131">The following example illustrates this process.</span></span> <span data-ttu-id="6af32-132">在此範例中， `hashValue` 和 `signedHashValue` 是遠端合作對象所提供的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="6af32-132">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="6af32-133">遠端合作對象已使用 SHA1 演算法簽署 `hashValue` ，產生數位簽章 `signedHashValue`。</span><span class="sxs-lookup"><span data-stu-id="6af32-133">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="6af32-134"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>方法會驗證數位簽章是否有效，並已用來簽署 `hashValue` 。</span><span class="sxs-lookup"><span data-stu-id="6af32-134">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

<span data-ttu-id="6af32-135">由於 SHA1 的衝突問題，我們建議 SHA256 或更好。</span><span class="sxs-lookup"><span data-stu-id="6af32-135">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>  <span data-ttu-id="6af32-136">不過，如果使用 SHA1 來建立簽章，您就必須使用 SHA1 來驗證簽章。</span><span class="sxs-lookup"><span data-stu-id="6af32-136">However, if SHA1 was used to create the signature, you have to use SHA1 to verify the signature.</span></span>

```vb
Dim rsa As RSA = RSA.Create()
rsa.ImportParameters(rsaKeyInfo)
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)
rsaDeformatter.SetHashAlgorithm("SHA1")
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then
   Console.WriteLine("The signature is valid.")
Else
   Console.WriteLine("The signature is not valid.")
End If
```

```csharp
RSA rsa = RSA.Create();
rsa.ImportParameters(rsaKeyInfo);
RSAPKCS1SignatureDeformatter rsaDeformatter = new RSAPKCS1SignatureDeformatter(rsa);
rsaDeformatter.SetHashAlgorithm("SHA1");
if(rsaDeformatter.VerifySignature(hashValue, signedHashValue))
{
   Console.WriteLine("The signature is valid.");
}
else
{
   Console.WriteLine("The signature is not valid.");
}
```

<span data-ttu-id="6af32-137">如果簽章有效，此程式碼片段會顯示 "`The signature is valid`"，否則顯示 "`The signature is not valid`"。</span><span class="sxs-lookup"><span data-stu-id="6af32-137">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="6af32-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6af32-138">See also</span></span>

- [<span data-ttu-id="6af32-139">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="6af32-139">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="6af32-140">密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="6af32-140">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="6af32-141">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="6af32-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="6af32-142">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="6af32-142">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
