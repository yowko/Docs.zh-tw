---
title: 解密資料
description: 瞭解如何使用對稱演算法或非對稱演算法來解密 .NET 中的資料。
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
ms.openlocfilehash: 7e8fe5a8b7ed7c217a31a8ee91a5d111257fed45
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440981"
---
# <a name="decrypting-data"></a>解密資料

解密是加密的反向作業。 針對秘密金鑰加密，您必須同時知道金鑰和用來加密資料的 IV。 針對公開金鑰加密，您必須知道公開金鑰 (如果使用私密金鑰來加密資料) 或私密金鑰 (如果使用公開金鑰來加密資料)。

## <a name="symmetric-decryption"></a>對稱解密

以對稱演算法加密的資料解密類似於用來以對稱演算法加密資料的程序。 <xref:System.Security.Cryptography.CryptoStream>類別會搭配 .net 提供的對稱式密碼編譯類別使用，以解密從任何 managed 資料流程物件讀取的資料。

下列範例說明如何為演算法建立預設實類別的新實例 <xref:System.Security.Cryptography.Aes> 。 實例用來對物件執行解密 <xref:System.Security.Cryptography.CryptoStream> 。 此範例會先建立實類別的新實例 <xref:System.Security.Cryptography.Aes> 。 它會從 managed 資料流程變數中讀取 (IV) 值的初始化向量 `myStream` 。 接下來它會具現化 <xref:System.Security.Cryptography.CryptoStream> 物件，並將它初始化為實例的值 `myStream` 。 <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType>實例中的方法 <xref:System.Security.Cryptography.Aes> 會傳遞 IV 值和用於加密的相同金鑰。

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

下列範例顯示建立資料流、解密資料流、從資料流讀取，然後關閉資料流的整個程序。 建立的檔案資料流程物件會讀取名為 *TestData.txt* 的檔案。 接著會使用 **CryptoStream** 類別和 **Aes** 類別來解密檔案資料流程。 此範例會指定用於 [加密資料](encrypting-data.md)的對稱式加密範例中所使用的金鑰值。 它不會顯示加密和傳輸這些值所需的程式碼。

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

上述範例使用相同的金鑰，以及用於對稱式加密範例中的演算法來 [加密資料](encrypting-data.md)。 它會將此範例所建立的 *TestData.txt* 檔案解密，並在主控台上顯示原始文字。

## <a name="asymmetric-decryption"></a>非對稱解密

一般而言，有一方 (A 方) 會同時產生公開和私密金鑰，並將金鑰儲存在記憶體或密碼編譯金鑰容器中。 A 方接著會將公開金鑰傳送給另一方 (B 方)。 使用公開金鑰時，合作物件 B 會將資料加密，並將資料傳送回第 A 方。收到資料之後，合作物件 A 會使用對應的私密金鑰將它解密。 只有在 A 方使用的私密金鑰對應於 B 方用來加密資料的公開金鑰時，解密才會成功。

如需如何在安全的密碼編譯金鑰容器儲存非對稱金鑰，以及稍後如何擷取非對稱金鑰的相關資訊，請參閱 [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md)。

下列範例說明代表對稱金鑰和 IV 的兩個位元組陣列的解密。 如需如何從 <xref:System.Security.Cryptography.RSA> 物件擷取非對稱式公開金鑰，且使用的格式可以輕鬆地傳送給第三方的相關資訊，請參閱 [Encrypting Data](encrypting-data.md)的 Managed 資料流的值。

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

## <a name="see-also"></a>請參閱

- [產生加密和解密金鑰](generating-keys-for-encryption-and-decryption.md)
- [加密資料](encrypting-data.md)
- [密碼編譯服務](cryptographic-services.md)
- [密碼編譯模型](cryptography-model.md)
- [跨平臺密碼編譯](cross-platform-cryptography.md)
- [使用填補進行 CBC 模式對稱解密的時間弱點](vulnerabilities-cbc-mode.md)
- [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)
