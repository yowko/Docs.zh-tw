---
title: 密碼編譯簽章
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET Framework], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET Framework], signatures
- security [.NET Framework], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15fd79a1289bd54b81db551abbdfcd63deef3e24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795248"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="9b4e2-102">密碼編譯簽章</span><span class="sxs-lookup"><span data-stu-id="9b4e2-102">Cryptographic Signatures</span></span>

<a name="top"></a> <span data-ttu-id="9b4e2-103">密碼編譯數位簽章會使用公開金鑰演算法來提供資料完整性。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="9b4e2-104">當您使用數位簽章簽署資料時，其他人可以確認簽章，並可以證明資料是來自您，而且在您簽署它之後沒有遭到竄改。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="9b4e2-105">如需有關數位簽章的詳細資訊，請參閱 [The signature is valid](../../../docs/standard/security/cryptographic-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>

<span data-ttu-id="9b4e2-106">本主題說明如何使用 <xref:System.Security.Cryptography?displayProperty=nameWithType> 命名空間中的類別產生及驗證數位簽章。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

- [<span data-ttu-id="9b4e2-107">產生簽章</span><span class="sxs-lookup"><span data-stu-id="9b4e2-107">Generating Signatures</span></span>](#generate)

- [<span data-ttu-id="9b4e2-108">驗證簽章</span><span class="sxs-lookup"><span data-stu-id="9b4e2-108">Verifying Signatures</span></span>](#verify)

<a name="generate"></a>

## <a name="generating-signatures"></a><span data-ttu-id="9b4e2-109">產生簽章</span><span class="sxs-lookup"><span data-stu-id="9b4e2-109">Generating Signatures</span></span>

<span data-ttu-id="9b4e2-110">數位簽章通常適用於代表較大資料的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="9b4e2-111">下列範例會將數位簽章套用到雜湊值。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="9b4e2-112">首先，會建立 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別的新執行個體，來產生公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="9b4e2-113">接著， <xref:System.Security.Cryptography.RSACryptoServiceProvider> 會傳遞至 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="9b4e2-114">如此會將私密金鑰轉移給 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>，它會實際執行數位簽署。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="9b4e2-115">在您可以簽署雜湊碼之前，必須先指定要使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="9b4e2-116">此範例使用 SHA1 演算法。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="9b4e2-117">最後，會呼叫 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> 方法來執行簽章。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

```vb
Imports System
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As New RSACryptoServiceProvider()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSACryptoServiceProvider to transfer the private key.
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
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSACryptoServiceProvider to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

### <a name="signing-xml-files"></a><span data-ttu-id="9b4e2-118">簽署 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="9b4e2-118">Signing XML Files</span></span>

<span data-ttu-id="9b4e2-119">.NET Framework 會提供 <xref:System.Security.Cryptography.Xml> 命名空間，可讓您簽署 XML。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-119">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="9b4e2-120">當您想要確認 XML 是來自特定來源時，簽署 XML 是很重要的。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-120">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="9b4e2-121">例如，如果您使用會利用 XML 的股票報價服務，如果 XML 的來源已簽署，您便可以驗證它。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-121">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="9b4e2-122">這個命名空間中的類別遵照[XML 簽章語法和處理建議](https://www.w3.org/TR/xmldsig-core/)全球資訊網協會。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-122">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

[<span data-ttu-id="9b4e2-123">回到頁首</span><span class="sxs-lookup"><span data-stu-id="9b4e2-123">Back to top</span></span>](#top)

<a name="verify"></a>

## <a name="verifying-signatures"></a><span data-ttu-id="9b4e2-124">驗證簽章</span><span class="sxs-lookup"><span data-stu-id="9b4e2-124">Verifying Signatures</span></span>

<span data-ttu-id="9b4e2-125">若要驗證資料是由特定合作對象簽署，您必須擁有下列資訊：</span><span class="sxs-lookup"><span data-stu-id="9b4e2-125">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="9b4e2-126">簽章資料之合作對象的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-126">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="9b4e2-127">數位簽章。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-127">The digital signature.</span></span>

- <span data-ttu-id="9b4e2-128">已簽署的資料。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-128">The data that was signed.</span></span>

- <span data-ttu-id="9b4e2-129">簽署人使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-129">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="9b4e2-130">若要驗證 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 類別所簽署的簽章，請使用 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 類別。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-130">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="9b4e2-131">必須提供 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 類別簽署者的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-131">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="9b4e2-132">您將需要模數和指數的值以指定公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-132">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="9b4e2-133">(產生公開/私密金鑰組的合作對象應該提供這些值。)先建立 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件來保存將會驗證簽章的公開金鑰，然後初始化 <xref:System.Security.Cryptography.RSAParameters> 結構，到指定公開金鑰的模數和指數值。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-133">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="9b4e2-134">下列程式碼顯示如何建立 <xref:System.Security.Cryptography.RSAParameters> 結構。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-134">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="9b4e2-135">`Modulus` 屬性設定為 `modulusData` 位元組陣列的值，而 `Exponent` 屬性設定為 `exponentData`位元組陣列的值。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-135">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="9b4e2-136">建立 <xref:System.Security.Cryptography.RSAParameters> 物件之後，您可以針對 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別的新執行個體，初始化至 <xref:System.Security.Cryptography.RSAParameters>中指定的值。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-136">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="9b4e2-137"><xref:System.Security.Cryptography.RSACryptoServiceProvider> 會接著傳遞給 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 的建構函式以傳送金鑰。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-137">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="9b4e2-138">下列範例將說明此程序。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-138">The following example illustrates this process.</span></span> <span data-ttu-id="9b4e2-139">在此範例中， `hashValue` 和 `signedHashValue` 是遠端合作對象所提供的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-139">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="9b4e2-140">遠端合作對象已使用 SHA1 演算法簽署 `hashValue` ，產生數位簽章 `signedHashValue`。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-140">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="9b4e2-141"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>方法會驗證數位簽章是否有效，以及用來簽署`hashValue`。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-141">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

```vb
Dim rsa As New RSACryptoServiceProvider()
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
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();
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

<span data-ttu-id="9b4e2-142">如果簽章有效，此程式碼片段會顯示 "`The signature is valid`"，否則顯示 "`The signature is not valid`"。</span><span class="sxs-lookup"><span data-stu-id="9b4e2-142">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b4e2-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b4e2-143">See also</span></span>

- [<span data-ttu-id="9b4e2-144">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="9b4e2-144">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
