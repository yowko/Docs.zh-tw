---
title: 密碼編譯簽章
ms.date: 07/14/2020
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
ms.openlocfilehash: 453e9d887012826da3f64d199e15a05fd0661191
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831126"
---
# <a name="cryptographic-signatures"></a>密碼編譯簽章

密碼編譯數位簽章會使用公開金鑰演算法來提供資料完整性。 當您使用數位簽章簽署資料時，其他人可以確認簽章，並可以證明資料是來自您，而且在您簽署它之後沒有遭到竄改。 如需有關數位簽章的詳細資訊，請參閱 [The signature is valid](cryptographic-services.md)。

本主題說明如何使用 <xref:System.Security.Cryptography> 命名空間中的類別產生及驗證數位簽章。

## <a name="generating-signatures"></a>產生簽章

數位簽章通常適用於代表較大資料的雜湊值。 下列範例會將數位簽章套用到雜湊值。 首先，會建立 <xref:System.Security.Cryptography.RSA> 類別的新執行個體，來產生公開/私密金鑰組。 接著， <xref:System.Security.Cryptography.RSA> 會傳遞至 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 類別的新執行個體。 如此會將私密金鑰轉移給 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>，它會實際執行數位簽署。 在您可以簽署雜湊碼之前，必須先指定要使用的雜湊演算法。 此範例使用 SHA1 演算法。 最後，會呼叫 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> 方法來執行簽章。

由於 SHA1 的衝突問題，我們建議使用 SHA256 或更好的方式。

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

## <a name="verifying-signatures"></a>驗證簽章

若要驗證資料是由特定合作對象簽署，您必須擁有下列資訊：

- 簽章資料之合作對象的公開金鑰。

- 數位簽章。

- 已簽署的資料。

- 簽署人使用的雜湊演算法。

若要驗證 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 類別所簽署的簽章，請使用 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 類別。 必須提供 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 類別簽署者的公開金鑰。 針對 RSA，您將需要模數和指數的值來指定公開金鑰。  (產生公開/私密金鑰組的合作物件應該提供這些值。 ) 先建立一個 <xref:System.Security.Cryptography.RSA> 物件來保存將驗證簽章的公開金鑰，然後將 <xref:System.Security.Cryptography.RSAParameters> 結構初始化為指定公開金鑰的模數和指數值。

下列程式碼顯示如何建立 <xref:System.Security.Cryptography.RSAParameters> 結構。 `Modulus` 屬性設定為 `modulusData` 位元組陣列的值，而 `Exponent` 屬性設定為 `exponentData`位元組陣列的值。

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

建立 <xref:System.Security.Cryptography.RSAParameters> 物件之後，您可以將實類別的新實例初始化 <xref:System.Security.Cryptography.RSA> 為中指定的值 <xref:System.Security.Cryptography.RSAParameters> 。 <xref:System.Security.Cryptography.RSA>實例會接著傳遞至的函式， <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 以傳輸金鑰。

下列範例將說明此程序。 在此範例中， `hashValue` 和 `signedHashValue` 是遠端合作對象所提供的位元組陣列。 遠端合作對象已使用 SHA1 演算法簽署 `hashValue` ，產生數位簽章 `signedHashValue`。 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>方法會驗證數位簽章是否有效，以及用來簽署 `hashValue` 。

由於 SHA1 的衝突問題，我們建議使用 SHA256 或更好的方式。  但是，如果使用 SHA1 來建立簽章，您必須使用 SHA1 來驗證簽章。

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

如果簽章有效，此程式碼片段會顯示 "`The signature is valid`"，否則顯示 "`The signature is not valid`"。

## <a name="see-also"></a>請參閱

- [密碼編譯服務](cryptographic-services.md)
- [密碼編譯模型](cryptography-model.md)
- [跨平臺密碼編譯](cross-platform-cryptography.md)
- [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)
