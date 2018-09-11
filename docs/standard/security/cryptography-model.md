---
title: .NET Framework 密碼編譯模型
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d74ce08197ac76a601202da8e35ca6f619207076
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264710"
---
# <a name="net-framework-cryptography-model"></a>.NET Framework 密碼編譯模型
.NET Framework 提供許多標準密碼編譯演算法的實作。 這些演算法容易使用，並且具有最安全的可能預設屬性。 此外，.NET Framework 的物件繼承、資料流設計與組態的密碼編譯模型非常具可擴充性。  
  
## <a name="object-inheritance"></a>物件繼承  
 .NET Framework 安全性系統會實作衍生類別繼承的可擴充模式。 階層如下所述：  
  
-   演算法類型類別，例如 <xref:System.Security.Cryptography.SymmetricAlgorithm>、<xref:System.Security.Cryptography.AsymmetricAlgorithm> 或 <xref:System.Security.Cryptography.HashAlgorithm>。 這個層級是抽象的。  
  
-   繼承自演算法類型類別的演算法類別；例如，<xref:System.Security.Cryptography.Aes><xref:System.Security.Cryptography.RC2> 或 <xref:System.Security.Cryptography.ECDiffieHellman>。 這個層級是抽象的。  
  
-   繼承自演算法類別的演算法類別實作；例如，<xref:System.Security.Cryptography.AesManaged><xref:System.Security.Cryptography.RC2CryptoServiceProvider> 或 <xref:System.Security.Cryptography.ECDiffieHellmanCng>。 這個層級已完全實作。  
  
 使用這種衍生類別的模式，就可以輕鬆地加入新的演算法或現有演算法的新實作。 例如，若要建立新的公開金鑰演算法，您會繼承自 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 類別。 若要建立特定演算法的新實作，您會建立該演算法的非抽象衍生類別。  
  
## <a name="how-algorithms-are-implemented-in-the-net-framework"></a>.NET Framework 中的演算法實作方式  
 做為可供演算法使用的不同實作方式範例，請考慮對稱演算法。 所有對稱演算法的基礎是 <xref:System.Security.Cryptography.SymmetricAlgorithm>，它由下列演算法所繼承：  
  
1.  <xref:System.Security.Cryptography.Aes>  
  
2.  <xref:System.Security.Cryptography.DES>  
  
3.  <xref:System.Security.Cryptography.RC2>  
  
4.  <xref:System.Security.Cryptography.Rijndael>  
  
5.  <xref:System.Security.Cryptography.TripleDES>  
  
 <xref:System.Security.Cryptography.Aes> 會由兩個類別繼承：<xref:System.Security.Cryptography.AesCryptoServiceProvider> 和 <xref:System.Security.Cryptography.AesManaged>。 <xref:System.Security.Cryptography.AesCryptoServiceProvider> 類別是 Aes 的 Windows 密碼編譯 API (CAPI) 實作的包裝函式，而 <xref:System.Security.Cryptography.AesManaged> 類別完全以 managed 程式碼撰寫。 除了 Managed 和 CAPI 實作，另外還有第三種類型的實作，Cryptography Next Generation (CNG)。 CNG 演算法的範例是 <xref:System.Security.Cryptography.ECDiffieHellmanCng>。 CNG 演算法可用於 Windows Vista 和更新版本。  
  
 您可以選擇哪一個實作最適合您。  可支援 .NET Framework 的所有平台上都可使用 Managed 實作。  CAPI 實作可用於較舊的作業系統，並且不會再開發。 CNG 是最新的實作，將在這裡進行新的開發工作。 不過，Manged 實作未經美國聯邦資訊處理標準 (FIPS) 認證，而且可能比包裝函式類別慢。  
  
## <a name="stream-design"></a>資料流設計  
 Common Language Runtime 使用資料流為導向的設計來實作對稱演算法和雜湊演算法。 這項設計的核心是 <xref:System.Security.Cryptography.CryptoStream> 類別，它衍生自 <xref:System.IO.Stream> 類別。 資料流為基礎的密碼編譯物件支援單一標準介面 (`CryptoStream`)，以便處理物件的資料傳輸部分。 由於所有物件都建置在標準介面上，您可以將多個物件鏈結在一起 (例如雜湊物件其後跟著加密物件)，且您可以對資料執行多項作業，而不需要任何中繼儲存體。 資料流模型也可讓您從較小的物件建置物件。 例如，結合的加密和雜湊演算法可視為單一資料流物件，雖然這個物件可能是從一組資料流物件建置而來。  
  
## <a name="cryptographic-configuration"></a>密碼編譯組態  
 密碼編譯組態可讓您將演算法的特定實作，解析為演算法名稱，允許擴充 .NET Framework 密碼編譯類別。 您可以加入自己的演算法硬體或軟體實作，並將實作對應到您選擇的演算法名稱。 如果在組態檔中未指定演算法，會使用預設設定。 如需有關密碼編譯組態的詳細資訊，請參閱[設定密碼編譯類別](../../../docs/framework/configure-apps/configure-cryptography-classes.md)。  
  
## <a name="choosing-an-algorithm"></a>選擇演算法  
 您選取演算法時可能有不同的原因：例如，為了資料完整性、為了資料隱私權，或是為了產生金鑰。 對稱和雜湊演算法是要用來出於完整性的原因 (防止變更) 或隱私權的原因 (防止檢視) 保護資料。 雜湊演算法主要用於資料完整性。  
  
 以下是依應用程式的建議演算法清單：  
  
-   資料隱私權：  
  
    -   <xref:System.Security.Cryptography.Aes>  
  
-   資料完整性：  
  
    -   <xref:System.Security.Cryptography.HMACSHA256>  
  
    -   <xref:System.Security.Cryptography.HMACSHA512>  
  
-   數位簽章：  
  
    -   <xref:System.Security.Cryptography.ECDsa>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   金鑰交換：  
  
    -   <xref:System.Security.Cryptography.ECDiffieHellman>  
  
    -   <xref:System.Security.Cryptography.RSA>  
  
-   亂數產生：  
  
    -   <xref:System.Security.Cryptography.RNGCryptoServiceProvider>  
  
-   從密碼產生金鑰：  
  
    -   <xref:System.Security.Cryptography.Rfc2898DeriveBytes>  
  
## <a name="see-also"></a>另請參閱

- [The signature is valid](../../../docs/standard/security/cryptographic-services.md)  
