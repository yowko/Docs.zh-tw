---
title: 使用 CBC 模式的對稱式解密使用邊框間距的計時弱點
description: 了解如何偵測及降低計時弱點與 Cipher Block Chaining (CBC) 模式對稱式解密使用的填補。
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 0f5f7d2032981d28445abe27f87a678ce2c74600
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066167"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>使用 CBC 模式的對稱式解密使用邊框間距的計時弱點

Microsoft 認為它是無法再解密資料加密使用對稱式加密 Cipher Block Chaining (CBC) 模式，而不先確保完整性的密碼文字，除了已套用可驗證的填補時的安全非常特定情況。 此判斷是以目前已知的密碼編譯研究為基礎。 

## <a name="introduction"></a>簡介

填補 oracle 攻擊是一種攻擊可讓攻擊者來解密資料，而不需要知道金鑰的加密資料。

Oracle 指的是 「 告訴 」 讓它們執行的動作是否為正確的攻擊者資訊。 想像一下播放面板或卡片具有子系的遊戲。 當她臉部會點亮並以巨量的笑臉替因為她認為她是即將進行的良好移動，是一種 oracle。 為對手，可以使用此 oracle 適當地規劃下一步的移動。

填補為特定的密碼編譯期間。 某些編碼器，也就是用來加密資料的演算法，適用於其中每個區塊的大小是固定的資料區塊。 如果您想要加密的資料不正確的大小以填滿的區塊，直到它會填補資料。 許多形式的邊框距離要求一律必須存在，即使已正確大小的原始輸入該邊框距離。 這可讓一律可以安全地移除時解密的填補。

將兩個項目放在一起，與邊框距離 oracle 軟體實作，顯示解密的資料是否具有有效的填補。 傳回值，指出 「 無效的邊框距離 」 簡單或更複雜，例如處理而不是無效的區塊是有效區塊的具體不同時間，可能是 oracle。

區塊編碼器會有另一個屬性，稱為模式，用來決定第一個區塊的第二個區塊中的資料中的資料關聯性，等等。 其中一個最常使用的模式是 CBC。 CBC 引進初始的隨機區塊，已知為初始化向量 (IV)，並結合的靜態加密，以方便，使用相同的金鑰加密相同的訊息不一定會產生相同加密的輸出結果中的前一個區塊。

攻擊者可以使用填補 oracle，搭配 CBC 資料結構的方式，將稍有變更的訊息傳送至 oracle，公開 （expose） 的程式碼，並持續傳送資料，直到 oracle 告訴他們的資料正確。 從這個回應，攻擊者可以解密逐位元組的訊息。

現代電腦網路都屬於這類高品質攻擊者可以偵測很小 （小於 0.1 毫秒） 在遠端系統上執行的差異時間。 假設資料未曾遭到竄改時，可以只會發生成功解密的應用程式可能容易遭受攻擊的工具，專為觀察在成功和失敗的解密的差異。 雖然這項時間差異可能是在某些語言或程式庫比其他更重要的現在認為這是實際服務威脅中的所有語言和程式庫，當失敗的應用程式的回應會納入考量。

這種攻擊會依賴變更加密的資料和測試結果與 oracle 的能力。 完全緩和攻擊的唯一方法是偵測加密資料的變更，並拒絕在其上執行任何動作。 若要這樣做的標準方式是建立資料的簽章，並執行任何作業之前，請驗證該簽章。 簽章必須可供驗證，攻擊者無法加以建立，否則它們就可以變更加密的資料，然後計算新的簽章已變更的資料為基礎。 一個常見的適當簽章的類型稱為金鑰式雜湊訊息驗證碼 (HMAC)。 HMAC 與總和檢查碼不同，在於它會使用祕密金鑰，已知只產生 HMAC 的人員，並確認它的人員。 而不需要擁有金鑰，您無法產生正確的 HMAC。 當您收到您的資料時，您會需要加密的資料，獨立計算 HMAC 使用祕密金鑰，您寄件者共用，然後它們傳送給其中一個您 HMAC 計算的比較。 這項比較必須是固定的時間，否則您已新增另一個偵測到 oracle，可讓不同類型的攻擊。

總而言之，使用填補 CBC 區塊加密方式安全地，您必須將它們合併 HMAC （或其他資料完整性檢查） 進行驗證再試一次使用固定時間的比較，來解密資料。 由於所有變更的訊息需要產生回應的相同時間量，防止攻擊。

## <a name="who-is-vulnerable"></a>易受攻擊是誰

這項弱點適用於 managed 和原生應用程式會執行自己的加密和解密。 這包括，例如：

- 應用程式來加密伺服器上的更新版本解密 cookie。
- 提供可讓使用者將資料插入資料表的資料行的資料庫應用程式會稍後會進行解密。
- 使用共用的金鑰來保護傳輸中的資料加密所依賴的應用程式的資料傳輸。
- 應用程式來加密及解密 「 內部 」 TLS 通道的訊息。

請注意，使用 TLS 本身可能不保護您在這些情況下。

易受攻擊的應用程式：

- 使用 CBC 加密模式，可驗證的填補模式，例如 PKCS #7 或 ANSI X.923 解密資料。
- 執行解密，而不需要執行資料完整性檢查 （透過在 MAC 或非對稱的數位簽章）。

這也適用於應用程式之上，請在下列基本類型，例如密碼編譯訊息語法 (PKCS #7/CMS) EnvelopedData 結構為基礎的抽象概念。

## <a name="related-areas-of-concern"></a>相關的關切的區域

參考資料造成 Microsoft 進一步考量到會填補填補訊息時的已知或可預測的頁尾結構的 ISO 10126-對等的 CBC 訊息。 例如，內容已備妥的 W3C XML 加密語法和處理建議 (xmlenc EncryptedXml) 的規則。 雖然 W3C 指導方針，以簽署訊息，然後加密已被視為適當時，Microsoft 現在會建議一律進行加密再簽署。

因為沒有任何固有之間的信任關係的非對稱金鑰和任意的訊息，應用程式開發人員應該一律是留意驗證的非對稱簽章金鑰的適用性。

## <a name="details"></a>詳細資料

在過去，已經很重要，來加密和驗證使用 HMAC 或 RSA 簽章等方式的重要資料的共識。 不過，已減少清楚的指引，來選擇要排序的加密和驗證作業。 本文章中的弱點，因為 Microsoft 的指引是現在一律使用 「 加密然後-簽署 」 典範。 也就是第一次使用對稱金鑰，加密資料，則計算加密文字 （加密的資料） 的 MAC 或非對稱簽章。 當解密資料，請執行反向。 首先，確認 MAC 或簽章的加密文字，然後將它解密。

稱為 「 填補 oracle 攻擊 」 存在超過 10 年已知的弱點類別。 這些弱點會允許攻擊者使用來解密資料加密的對稱區塊的演算法，例如 AES 和 3DES，超過 4096 個嘗試每個資料區塊。 進行這些弱點可驗證的邊框距離結尾的資料最常使用的區塊編碼器的事實使用。 它找不到攻擊者可以修改加密文字，並了解是否遭到竄改而造成錯誤的結尾填補格式，是否攻擊者可以解密資料。

一開始，會傳回不同的錯誤代碼是否有效，例如 ASP.NET 的弱點可能會填補為基礎的服務以實際的攻擊[MS10 070](/security-updates/SecurityBulletins/2010/ms10-070)。 不過，Microsoft 現在認為它是實際進行類似的攻擊使用只在處理有效和無效的邊框距離之間的時間差異。

而不發出任何資訊，提供的加密配置採用簽章和簽章驗證會使用固定的執行階段指定長度的資料 （不論內容中） 執行的可以驗證資料完整性攻擊者透過[側邊通道](https://en.wikipedia.org/wiki/Side-channel_attack)。 因為完整性檢查會拒絕遭竄改的任何訊息，以降低填補 oracle 威脅。

## <a name="guidance"></a>指引

首先，Microsoft 建議透過傳輸層安全性 (TLS)，以安全通訊端層 (SSL) 的後續版本需要傳送任何具有機密性的資料。

接下來，分析您的應用程式：

- 了解精確地將您要執行何種加密，並由平台和您使用的 Api 提供何種加密。
- 可確定每個使用方式，在每一層的對稱[區塊加密演算法](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)，例如 AES 和 3DES，CBC 模式的合併使用的密碼為索引鍵的資料完整性檢查 (非對稱簽章的 HMAC，或若要變更加密模式[驗證加密](https://en.wikipedia.org/wiki/Authenticated_encryption)(AE) 模式，例如 GCM 或 CCM)。

以目前研究為基礎，因此一般認為，非 AE 模式，加密的獨立執行的驗證和加密步驟時，驗證加密文字 （加密-然後-簽署） 時，最佳的一般選項。 不過，沒有一體適用的正確解答，密碼編譯，而且這個一般化不專業的解碼員從不如導向的建議。

無法變更其訊息的格式，但執行未經驗證的 CBC 解密的應用程式，建議嘗試將緩和措施，例如：

- 不允許的解密程式來驗證或移除填補解密：
  - 已套用任何填補字元仍必須移除，或略過，您要移動到您的應用程式的負擔。
  - 優點是，填補驗證及移除，可以合併到其他應用程式資料的驗證邏輯。 如果填補驗證及資料驗證可以以常數時間來完成，則會降低潛在威脅。
  - 因為填補的解譯變更察覺到的訊息長度，仍可能從這種方法發出的計時資訊。
- 變更 ISO10126 解密的填補模式：
  - ISO10126 解密填補是與 PKCS7 加密填補和 ANSIX923 加密填補相容。
  - 將模式變更成 1 個位元組，而不是整個區塊減少填補 oracle 知識。 不過，如果內容有已知的頁尾中，例如結尾 XML 項目相關的攻擊可以繼續攻擊其餘的訊息。
  - 這也不會阻止在其中，攻擊者可以強制轉型會以不同的訊息位移加密多次相同的純文字的情況下的純文字復原。
- 閘道評估的解密呼叫水輥計時訊號：
  - 等候時間的計算必須解密作業會針對包含填補的任何資料 」 區段所需的時間的最大數量超過最小值。
  - 時間計算應該根據中的指導方針[取得高解析度的時間戳記](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx)，不是使用<xref:System.Environment.TickCount?displayProperty=nameWithType>（受限於向前復原移轉/溢位） 上或減去兩個系統的時間戳記，（受限於 NTP 調整錯誤）。
  - 時間計算必須包括在所有可能的例外狀況解密作業包含管理或 c + + 應用程式，不只是加在尾端填補。
  - 如果已尚未決定成功或失敗，計時閘道需要它過期時傳回失敗。
- 監視機制來偵測已通過的 「 無效 」 訊息時，應該執行未經驗證的解密的服務。
  - 請記住此訊號會誤肯定 （合法的損毀的資料） 和誤否定 （經過一段夠長的時間來規避偵測攻擊散佈）。

## <a name="finding-vulnerable-code---native-applications"></a>尋找易受攻擊的程式碼-原生應用程式

建置 Windows 密碼編譯的程式：下一步 的新一代 (CNG) 程式庫：

- 解密呼叫是對[BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt)，並指定`BCRYPT_BLOCK_PADDING`旗標。
- 藉由呼叫已經初始化的金鑰控制代碼[BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty)具有[BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE)設定為`BCRYPT_CHAIN_MODE_CBC`。
  - 由於`BCRYPT_CHAIN_MODE_CBC`是預設設定，受影響的程式碼可能未指派任何值`BCRYPT_CHAINING_MODE`。

針對較舊的 Windows 密碼編譯 API 建置的程式：

- 解密呼叫是對[CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt)使用`Final=TRUE`。
- 藉由呼叫已經初始化的金鑰控制代碼[CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam)具有[KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam)設定為`CRYPT_MODE_CBC`。
  - 由於`CRYPT_MODE_CBC`是預設設定，受影響的程式碼可能未指派任何值`KP_MODE`。

## <a name="finding-vulnerable-code---managed-applications"></a>尋找受到程式碼-受管理的應用程式

- 解密呼叫是對<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor>或是<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])>上的方法<xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>。
  - 這包括在.NET 中，下列的衍生型別，但也可能包含協力廠商類型：
    - <xref:System.Security.Cryptography.Aes>
    - <xref:System.Security.Cryptography.AesCng>
    - <xref:System.Security.Cryptography.AesCryptoServiceProvider>
    - <xref:System.Security.Cryptography.AesManaged>
    - <xref:System.Security.Cryptography.DES>
    - <xref:System.Security.Cryptography.DESCryptoServiceProvider>
    - <xref:System.Security.Cryptography.RC2>
    - <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
    - <xref:System.Security.Cryptography.Rijndael>
    - <xref:System.Security.Cryptography.RijndaelManaged>
    - <xref:System.Security.Cryptography.TripleDES>
    - <xref:System.Security.Cryptography.TripleDESCng>
    - <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>屬性設定為<xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>， <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>，或<xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>。
  - 由於<xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>是預設設定，受影響的程式碼可能永遠不會指派<xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>屬性。
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>屬性設定為 <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - 由於<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>是預設設定，受影響的程式碼可能永遠不會指派<xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>屬性。

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>尋找易受攻擊的程式碼-密碼編譯訊息語法

未驗證的 CMS EnvelopedData 訊息，其加密的內容會使用 CBC 模式的 AES （2.16.840.1.101.3.4.1.2、 2.16.840.1.101.3.4.1.22 2.16.840.1.101.3.4.1.42）、 DES (1.3.14.3.2.7)、 3DES (1.2.840.113549.3.7) 或 RC2 (1.2.840.113549.3.2) 是易受攻擊，以及做為訊息使用 CBC 模式的任何其他的區塊加密演算法。

雖然資料流加密不容易受到這項特定弱點，Microsoft 建議一律透過檢查 ContentEncryptionAlgorithm 值進行驗證的資料。

對於受管理的應用程式，blob 可以是 CMS EnvelopedData 偵測到任何值，會傳遞至<xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>。

原生應用程式，CMS EnvelopedData blob 可以偵測到的 CMS 控點，透過提供任何值[CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate)其產生[CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam)是`CMSG_ENVELOPED`和/或 CMS 控制代碼稍後傳送`CMSG_CTRL_DECRYPT`透過指令[CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol)。

## <a name="vulnerable-code-example---managed"></a>易受攻擊的程式碼範例-管理

這個方法會讀取 cookie，然後將它解密且可以看見任何資料完整性檢查。 因此，使用者已收到，或任何攻擊者取得加密的 cookie 值，這個方法會讀取 cookie 的內容可能會遭受攻擊。

```csharp
private byte[] DecryptCookie(string cookieName)
{
    HttpCookie cookie = Request.Cookies[cookieName];

    if (cookie == null)
    {
        return null;
    }

    using (ICryptoTransform decryptor = _aes.CreateDecryptor())
    using (MemoryStream memoryStream = new MemoryStream())
    using (CryptoStream cryptoStream =
        new CryptoStream(memoryStream, decryptor, CryptoStreamMode.Write))
    {
        byte[] readCookie = Convert.FromBase64String(cookie.Value);
        cryptoStream.Write(readCookie, 0, readCookie.Length);
        cryptoStream.FlushFinalBlock();
        return memoryStream.ToArray();
    }
}
```

## <a name="example-code-following-recommended-practices---managed"></a>下列範例程式碼建議的作法-管理

下列範例程式碼會使用非標準的訊息格式

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

何處`cipher_algorithm_id`和`hmac_algorithm_id`演算法識別項是這些演算法的應用程式的本機 （非標準） 的表示法。 這些識別碼合理的其他部分，而不是您現有的傳訊通訊協定為裸機串連位元組資料流。

此範例也會使用單一的主要金鑰來加密金鑰和 HMAC 金鑰衍生。 這被提供兩者都是為了方便起見，開啟單一索引應用程式到雙重為索引鍵的應用程式，並鼓勵保留兩個索引鍵為不同的值。 它進一步保證的 HMAC 金鑰和加密金鑰無法取得未執行同步處理。

此範例不會接受<xref:System.IO.Stream>加密或解密。 目前的資料格式進行一段式加密不容易因為`hmac_tag`值之前加密文字。 不過，因為它在最開頭一直到簡單的剖析器會將所有固定大小的項目，已選擇這種格式。 此資料格式時，一段式解密是可行的但實作者 cautioned 呼叫 GetHashAndReset 並呼叫 TransformFinalBlock 之前驗證結果。 如果資料流加密很重要的不同的 AE 模式可能需要。

```csharp
// ==++==
//
//   Copyright (c) Microsoft Corporation.  All rights reserved.
//
//   Shared under the terms of the Microsoft Public License,
//   https://opensource.org/licenses/MS-PL
//
// ==--==

using System;
using System.Diagnostics;
using System.IO;
using System.Runtime.CompilerServices;
using System.Security.Cryptography;

namespace Microsoft.Examples.Cryptography
{
    public enum AeCipher : byte
    {
        Unknown,
        Aes256CbcPkcs7,
    }

    public enum AeMac : byte
    {
        Unknown,
        HMACSHA256,
        HMACSHA384,
    }

    /// <summary>
    /// Provides extension methods to make HashAlgorithm look like .NET Core's
    /// IncrementalHash
    /// </summary>
    internal static class IncrementalHashExtensions
    {
        public static void AppendData(this HashAlgorithm hash, byte[] data)
        {
            hash.TransformBlock(data, 0, data.Length, null, 0);
        }

        public static void AppendData(
            this HashAlgorithm hash,
            byte[] data,
            int offset,
            int length)
        {
            hash.TransformBlock(data, offset, length, null, 0);
        }

        public static byte[] GetHashAndReset(this HashAlgorithm hash)
        {
            hash.TransformFinalBlock(Array.Empty<byte>(), 0, 0);
            return hash.Hash;
        }
    }

    public static partial class AuthenticatedEncryption
    {
        /// <summary>
        /// Use <paramref name="masterKey"/> to derive two keys (one cipher, one HMAC)
        /// to provide authenticated encryption for <paramref name="message"/>.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="message">The message to encrypt</param>
        /// <returns>
        /// A concatenation of
        /// [cipher algorithm+chainmode+padding][mac algorithm][authtag][IV][ciphertext],
        /// suitable to be passed to <see cref="Decrypt"/>.
        /// </returns>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or bigger) value generated
        /// by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>.
        /// This implementation chooses to block deficient inputs by length, but does not
        /// make any attempt at discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase)
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Encrypt(byte[] masterKey, byte[] message)
        {
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (message == null)
                throw new ArgumentNullException(nameof(message));

            // First, choose an encryption scheme.
            AeCipher aeCipher = AeCipher.Aes256CbcPkcs7;

            // Second, choose an authentication (message integrity) scheme.
            //
            // In this example we use the master key length to change from HMACSHA256 to
            // HMACSHA384, but that is completely arbitrary. This mostly represents a
            // "cryptographic needs change over time" scenario.
            AeMac aeMac = masterKey.Length < 48 ? AeMac.HMACSHA256 : AeMac.HMACSHA384;

            // It's good to be able to identify what choices were made when a message was
            // encrypted, so that the message can later be decrypted. This allows for
            // future versions to add support for new encryption schemes, but still be
            // able to read old data. A practice known as "cryptographic agility".
            //
            // This is similar in practice to PKCS#7 messaging, but this uses a
            // private-scoped byte rather than a public-scoped Object IDentifier (OID).
            // Please note that the scheme in this example adheres to no particular
            // standard, and is unlikely to survive to a more complete implementation in
            // the .NET Framework.
            //
            // You may be well-served by prepending a version number byte to this
            // message, but may want to avoid the value 0x30 (the leading byte value for
            // DER-encoded structures such as X.509 certificates and PKCS#7 messages).
            byte[] algorithmChoices = { (byte)aeCipher, (byte)aeMac };
            byte[] iv;
            byte[] cipherText;
            byte[] tag;

            // Using our algorithm choices, open an HMAC (as an authentication tag
            // generator) and a SymmetricAlgorithm which use different keys each derived
            // from the same master key.
            //
            // A custom implementation may very well have distinctly managed secret keys
            // for the MAC and cipher, this example merely demonstrates the master to
            // derived key methodology to encourage key separation from the MAC and
            // cipher keys.
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
                using (ICryptoTransform encryptor = cipher.CreateEncryptor())
                {
                    // Since no IV was provided, a random one has been generated
                    // during the call to CreateEncryptor.
                    //
                    // But note that it only does the auto-generation once. If the cipher
                    // object were used again, a call to GenerateIV would have been
                    // required.
                    iv = cipher.IV;

                    cipherText = Transform(encryptor, message, 0, message.Length);
                }

                // The IV and ciphertest both need to be included in the MAC to prevent
                // tampering.
                //
                // By including the algorithm identifiers, we have technically moved from
                // simple Authenticated Encryption (AE) to Authenticated Encryption with
                // Additional Data (AEAD). By including the algorithm identifiers in the
                // MAC, it becomes harder for an attacker to change them as an attempt to
                // perform a downgrade attack.
                //
                // If you've added a data format version field, it can also be included
                // in the MAC to further inhibit an attacker's options for confusing the
                // data processor into believing the tampered message is valid.
                tagGenerator.AppendData(algorithmChoices);
                tagGenerator.AppendData(iv);
                tagGenerator.AppendData(cipherText);
                tag = tagGenerator.GetHashAndReset();
            }

            // Build the final result as the concatenation of everything except the keys.
            int totalLength =
                algorithmChoices.Length +
                tag.Length +
                iv.Length +
                cipherText.Length;

            byte[] output = new byte[totalLength];
            int outputOffset = 0;

            Append(algorithmChoices, output, ref outputOffset);
            Append(tag, output, ref outputOffset);
            Append(iv, output, ref outputOffset);
            Append(cipherText, output, ref outputOffset);

            Debug.Assert(outputOffset == output.Length);
            return output;
        }

        /// <summary>
        /// Reads a message produced by <see cref="Encrypt"/> after verifying it hasn't
        /// been tampered with.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="cipherText">
        /// The output of <see cref="Encrypt"/>: a concatenation of a cipher ID, mac ID,
        /// authTag, IV, and cipherText.
        /// </param>
        /// <returns>The decrypted content.</returns>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="masterKey"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="cipherText"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="CryptographicException">
        /// <paramref name="cipherText"/> identifies unknown algorithms, is not long
        /// enough, fails a data integrity check, or fails to decrypt.
        /// </exception>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or larger) value
        /// generated by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>. This implementation chooses to
        /// block deficient inputs by length, but doesn't make any attempt at
        /// discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase),
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Decrypt(byte[] masterKey, byte[] cipherText)
        {
            // This example continues the .NET practice of throwing exceptions for
            // failures. If you consider message tampering to be normal (and thus
            // "not exceptional") behavior, you may like the signature
            // bool Decrypt(byte[] messageKey, byte[] cipherText, out byte[] message)
            // better.
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (cipherText == null)
                throw new ArgumentNullException(nameof(cipherText));

            // The format of this message is assumed to be public, so there's no harm in
            // saying ahead of time that the message makes no sense.
            if (cipherText.Length < 2)
            {
                throw new CryptographicException();
            }

            // Use the message algorithm headers to determine what cipher algorithm and
            // MAC algorithm are going to be used. Since the same Key Derivation
            // Functions (KDFs) are being used in Decrypt as Encrypt, the keys are also
            // the same.
            AeCipher aeCipher = (AeCipher)cipherText[0];
            AeMac aeMac = (AeMac)cipherText[1];

            using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                int blockSizeInBytes = cipher.BlockSize / 8;
                int tagSizeInBytes = tagGenerator.HashSize / 8;
                int headerSizeInBytes = 2;
                int tagOffset = headerSizeInBytes;
                int ivOffset = tagOffset + tagSizeInBytes;
                int cipherTextOffset = ivOffset + blockSizeInBytes;
                int cipherTextLength = cipherText.Length - cipherTextOffset;
                int minLen = cipherTextOffset + blockSizeInBytes;

                // Again, the minimum length is still assumed to be public knowledge,
                // nothing has leaked out yet. The minimum length couldn't just be calculated
                // without reading the header.
                if (cipherText.Length < minLen)
                {
                    throw new CryptographicException();
                }

                // It's very important that the MAC be calculated and verified before
                // proceeding to decrypt the ciphertext, as this prevents any sort of
                // information leaking out to an attacker.
                //
                // Don't include the tag in the calculation, though.

                // First, everything before the tag (the cipher and MAC algorithm ids)
                tagGenerator.AppendData(cipherText, 0, tagOffset);

                // Skip the data before the tag and the tag, then read everything that
                // remains.
                tagGenerator.AppendData(
                    cipherText,
                    tagOffset + tagSizeInBytes,
                    cipherText.Length - tagSizeInBytes - tagOffset);

                byte[] generatedTag = tagGenerator.GetHashAndReset();

                // The time it took to get to this point has so far been a function only
                // of the length of the data, or of non-encrypted values (e.g. it could
                // take longer to prepare the *key* for the HMACSHA384 MAC than the
                // HMACSHA256 MAC, but the algorithm choice wasn't a secret).
                //
                // If the verification of the authentication tag aborts as soon as a
                // difference is found in the byte arrays then your program may be
                // acting as a timing oracle which helps an attacker to brute-force the
                // right answer for the MAC. So, it's very important that every possible
                // "no" (2^256-1 of them for HMACSHA256) be evaluated in as close to the
                // same amount of time as possible. For this, we call CryptographicEquals
                if (!CryptographicEquals(
                    generatedTag,
                    0,
                    cipherText,
                    tagOffset,
                    tagSizeInBytes))
                {
                    // Assuming every tampered message (of the same length) took the same
                    // amount of time to process, we can now safely say
                    // "this data makes no sense" without giving anything away.
                    throw new CryptographicException();
                }

                // Restore the IV into the symmetricAlgorithm instance.
                byte[] iv = new byte[blockSizeInBytes];
                Buffer.BlockCopy(cipherText, ivOffset, iv, 0, iv.Length);
                cipher.IV = iv;

                using (ICryptoTransform decryptor = cipher.CreateDecryptor())
                {
                    return Transform(
                        decryptor,
                        cipherText,
                        cipherTextOffset,
                        cipherTextLength);
                }
            }
        }

        private static byte[] Transform(
            ICryptoTransform transform,
            byte[] input,
            int inputOffset,
            int inputLength)
        {
            // Many of the implementations of ICryptoTransform report true for
            // CanTransformMultipleBlocks, and when the entire message is available in
            // one shot this saves on the allocation of the CryptoStream and the
            // intermediate structures it needs to properly chunk the message into blocks
            // (since the underlying stream won't always return the number of bytes
            // needed).
            if (transform.CanTransformMultipleBlocks)
            {
                return transform.TransformFinalBlock(input, inputOffset, inputLength);
            }

            // If our transform couldn't do multiple blocks at once, let CryptoStream
            // handle the chunking.
            using (MemoryStream messageStream = new MemoryStream())
            using (CryptoStream cryptoStream =
                new CryptoStream(messageStream, transform, CryptoStreamMode.Write))
            {
                cryptoStream.Write(input, inputOffset, inputLength);
                cryptoStream.FlushFinalBlock();
                return messageStream.ToArray();
            }
        }

        /// <summary>
        /// Open a properly configured <see cref="SymmetricAlgorithm"/> conforming to the
        /// scheme identified by <paramref name="aeCipher"/>.
        /// </summary>
        /// <param name="aeCipher">The cipher mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// A SymmetricAlgorithm object with the right key, cipher mode, and padding
        /// mode; or <c>null</c> on unknown algorithms.
        /// </returns>
        private static SymmetricAlgorithm GetCipher(AeCipher aeCipher, byte[] masterKey)
        {
            SymmetricAlgorithm symmetricAlgorithm;

            switch (aeCipher)
            {
                case AeCipher.Aes256CbcPkcs7:
                    symmetricAlgorithm = Aes.Create();
                    // While 256-bit, CBC, and PKCS7 are all the default values for these
                    // properties, being explicit helps comprehension more than it hurts
                    // performance.
                    symmetricAlgorithm.KeySize = 256;
                    symmetricAlgorithm.Mode = CipherMode.CBC;
                    symmetricAlgorithm.Padding = PaddingMode.PKCS7;
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            //
            // Since none of the symmetric encryption algorithms currently in .NET
            // support key sizes greater than 256-bit, we can use HMACSHA256 with
            // NIST SP 800-108 5.1 (Counter Mode KDF) to derive a value that is
            // no smaller than the key size, then Array.Resize to trim it down as
            // needed.

            using (HMAC hmac = new HMACSHA256(masterKey))
            {
                // i=1, Label=ASCII(cipher)
                byte[] cipherKey = hmac.ComputeHash(
                    new byte[] { 1, 99, 105, 112, 104, 101, 114 });

                // Resize the array to the desired keysize. KeySize is in bits,
                // and Array.Resize wants the length in bytes.
                Array.Resize(ref cipherKey, symmetricAlgorithm.KeySize / 8);

                symmetricAlgorithm.Key = cipherKey;
            }

            return symmetricAlgorithm;
        }

        /// <summary>
        /// Open a properly configured <see cref="HMAC"/> conforming to the scheme
        /// identified by <paramref name="aeMac"/>.
        /// </summary>
        /// <param name="aeMac">The message authentication mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// An HMAC object with the proper key, or <c>null</c> on unknown algorithms.
        /// </returns>
        private static HMAC GetMac(AeMac aeMac, byte[] masterKey)
        {
            HMAC hmac;

            switch (aeMac)
            {
                case AeMac.HMACSHA256:
                    hmac = new HMACSHA256();
                    break;
                case AeMac.HMACSHA384:
                    hmac = new HMACSHA384();
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            // Since the output size of the HMAC is the same as the ideal key size for
            // the HMAC, we can use the master key over a fixed input once to perform
            // NIST SP 800-108 5.1 (Counter Mode KDF):
            hmac.Key = masterKey;

            // i=1, Context=ASCII(MAC)
            byte[] newKey = hmac.ComputeHash(new byte[] { 1, 77, 65, 67 });

            hmac.Key = newKey;
            return hmac;
        }

        // A simple helper method to ensure that the offset (writePos) always moves
        // forward with new data.
        private static void Append(byte[] newData, byte[] combinedData, ref int writePos)
        {
            Buffer.BlockCopy(newData, 0, combinedData, writePos, newData.Length);
            writePos += newData.Length;
        }

        /// <summary>
        /// Compare the contents of two arrays in an amount of time which is only
        /// dependent on <paramref name="length"/>.
        /// </summary>
        /// <param name="a">An array to compare to <paramref name="b"/>.</param>
        /// <param name="aOffset">
        /// The starting position within <paramref name="a"/> for comparison.
        /// </param>
        /// <param name="b">An array to compare to <paramref name="a"/>.</param>
        /// <param name="bOffset">
        /// The starting position within <paramref name="b"/> for comparison.
        /// </param>
        /// <param name="length">
        /// The number of bytes to compare between <paramref name="a"/> and
        /// <paramref name="b"/>.</param>
        /// <returns>
        /// <c>true</c> if both <paramref name="a"/> and <paramref name="b"/> have
        /// sufficient length for the comparison and all of the applicable values are the
        /// same in both arrays; <c>false</c> otherwise.
        /// </returns>
        /// <remarks>
        /// An "insufficient data" <c>false</c> response can happen early, but otherwise
        /// a <c>true</c> or <c>false</c> response take the same amount of time.
        /// </remarks>
        [MethodImpl(MethodImplOptions.NoInlining | MethodImplOptions.NoOptimization)]
        private static bool CryptographicEquals(
            byte[] a,
            int aOffset,
            byte[] b,
            int bOffset,
            int length)
        {
            Debug.Assert(a != null);
            Debug.Assert(b != null);
            Debug.Assert(length >= 0);

            int result = 0;

            if (a.Length - aOffset < length || b.Length - bOffset < length)
            {
                return false;
            }

            unchecked
            {
                for (int i = 0; i < length; i++)
                {
                    // Bitwise-OR of subtraction has been found to have the most
                    // stable execution time.
                    //
                    // This cannot overflow because bytes are 1 byte in length, and
                    // result is 4 bytes.
                    // The OR propagates all set bytes, so the differences are only
                    // present in the lowest byte.
                    result = result | (a[i + aOffset] - b[i + bOffset]);
                }
            }

            return result == 0;
        }
    }
}
```
