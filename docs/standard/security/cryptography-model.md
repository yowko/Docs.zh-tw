---
title: .NET 密碼編譯模型
description: 在 .NET 中審視一般密碼編譯演算法的實作為。 瞭解物件繼承、串流設計、& 設定的可延伸加密模型。
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], model
- encryption [.NET], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: a157a9a76f87a2a56c616b76c933e6d8d6415b03
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281580"
---
# <a name="net-cryptography-model"></a>.NET 密碼編譯模型

.NET 提供許多標準密碼編譯演算法的執行，而 .NET 加密模型則是可擴充的。

## <a name="object-inheritance"></a>物件繼承

.NET 密碼編譯系統會實作為衍生類別繼承的可擴充模式。 階層如下所述：

- 演算法型別類別，例如 <xref:System.Security.Cryptography.SymmetricAlgorithm> 、  <xref:System.Security.Cryptography.AsymmetricAlgorithm> 或 <xref:System.Security.Cryptography.HashAlgorithm> 。 這個層級是抽象的。

- 繼承自演算法類型類別的演算法類別；例如，<xref:System.Security.Cryptography.Aes><xref:System.Security.Cryptography.RSA> 或 <xref:System.Security.Cryptography.ECDiffieHellman>。 這個層級是抽象的。

- 繼承自演算法類別的演算法類別實作；例如，<xref:System.Security.Cryptography.AesManaged><xref:System.Security.Cryptography.RC2CryptoServiceProvider> 或 <xref:System.Security.Cryptography.ECDiffieHellmanCng>。 這個層級已完全實作。

這種衍生類別的模式可讓您加入新的演算法，或現有演算法的新實作為。 例如，若要建立新的公開金鑰演算法，您會繼承自 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 類別。 若要建立特定演算法的新實作，您會建立該演算法的非抽象衍生類別。

## <a name="how-algorithms-are-implemented-in-net"></a>如何在 .NET 中執行演算法

做為可供演算法使用的不同實作方式範例，請考慮對稱演算法。 所有對稱演算法的基底是 <xref:System.Security.Cryptography.SymmetricAlgorithm> 由 <xref:System.Security.Cryptography.Aes> 、 <xref:System.Security.Cryptography.TripleDES> 和其他不再建議的所繼承。

<xref:System.Security.Cryptography.Aes> 繼承自 <xref:System.Security.Cryptography.AesCryptoServiceProvider> 、 <xref:System.Security.Cryptography.AesCng> 和 <xref:System.Security.Cryptography.AesManaged> 。

在 Windows 上的 .NET Framework：

* `*CryptoServiceProvider` 演算法類別（例如 <xref:System.Security.Cryptography.AesCryptoServiceProvider> ）是在 Windows 密碼編譯 API 周圍的包裝函式， (CAPI) 的演算法執行。
* `*Cng` 演算法類別（例如 <xref:System.Security.Cryptography.ECDiffieHellmanCng> ）是 Windows 新一代密碼編譯 (CNG) 實作為包裝函式。
* `*Managed` 類別（例如 <xref:System.Security.Cryptography.AesManaged> ）完全以 managed 程式碼撰寫。 `*Managed` (FIPS) 的聯邦資訊處理標準尚未認證，而且可能會比和包裝函式 `*CryptoServiceProvider` 類別更慢 `*Cng` 。

在 .NET Core 和 .NET 5 和更新版本中，所有的實類別 (`*CryptoServiceProvider` 、 `*Managed` 和 `*Cng`) 都是作業系統 (OS) 演算法的包裝函式。 如果 OS 演算法是經過 FIPS 認證，則 .NET 會使用 FIPS 認證的演算法。 如需詳細資訊，請參閱 [跨平臺密碼](cross-platform-cryptography.md)編譯。

在大多數情況下，您不需要直接參考演算法實類別，例如 `AesCryptoServiceProvider` 。 您通常需要的方法和屬性位於基底演算法類別，例如 `Aes` 。 使用基底演算法類別上的 factory 方法建立預設實類別的實例，並參考基底演算法類別。 例如，請參閱下列範例中反白顯示的程式程式碼：

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs" highlight="16":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb" highlight="12":::

## <a name="cryptographic-configuration"></a>密碼編譯組態

密碼編譯設定可讓您將演算法的特定執行解析為演算法名稱，允許 .NET 密碼編譯類別的擴充性。 您可以加入自己的演算法硬體或軟體實作，並將實作對應到您選擇的演算法名稱。 如果在組態檔中未指定演算法，會使用預設設定。

## <a name="choosing-an-algorithm"></a>選擇演算法

您選取演算法時可能有不同的原因：例如，為了資料完整性、為了資料隱私權，或是為了產生金鑰。 對稱和雜湊演算法是要用來出於完整性的原因 (防止變更) 或隱私權的原因 (防止檢視) 保護資料。 雜湊演算法主要用於資料完整性。

以下是依應用程式的建議演算法清單：

- 資料隱私權：
  - <xref:System.Security.Cryptography.Aes>
- 資料完整性：
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- 數位簽章：
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- 金鑰交換：
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- 亂數產生：
  - <xref:System.Security.Cryptography.RandomNumberGenerator.Create%2A?displayProperty=nameWithType>
- 從密碼產生金鑰：
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a>另請參閱

- [密碼編譯服務](cryptographic-services.md)
- [跨平臺密碼編譯](cross-platform-cryptography.md)
- [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)
