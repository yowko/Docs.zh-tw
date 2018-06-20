---
title: CBC 模式的對稱式解密使用邊框距離與計時弱點
description: 了解如何偵測和解決時間的弱點可能會使用加密區塊鏈結 (CBC) 模式對稱解密使用的填補。
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 26f4d19f591ac02d792bebbd648e90b07d84de56
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208682"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>CBC 模式的對稱式解密使用邊框距離與計時弱點

Microsoft 認為有，就無法再解密資料時不含第一個確保完整性的加密文字，除了已套用可驗證的填補加密使用對稱式加密的加密區塊鏈結 (CBC) 模式的安全非常特定情況。 此 judgement 根據目前已知的密碼編譯研究。 

## <a name="introduction"></a>簡介

填補 oracle 攻擊是一種攻擊，可讓攻擊者能夠解密資料的內容，而不需要知道的金鑰加密資料。

Oracle 指的是 「 告訴 」，讓它們執行的動作是否為正確的攻擊者資訊。 想像一下棋盤或遊戲卡片具有子系。 當她朝亮起大笑臉與她認為她是因為即將進行的良好移動，是一種 oracle。 為對手，可用於此 oracle 適當地計劃下移動。

填補為特定的密碼編譯詞彙。 某些加密方式，也就是用來加密資料的演算法，適用於其中每個區塊都是固定的大小資料區塊。 如果您想要加密的資料不正確的大小以填滿的區塊，直到它會填補資料。 許多形式的填補都需要該填補一律必須存在，即使是正確的大小是原始的輸入。 這可讓永遠可以安全地移除在解密時的填補。

將放在一起的兩個項目，與邊框距離 oracle 軟體實作會顯示已解密的資料是否有有效的填補。 Oracle 可能是簡單的為傳回值，指出 「 無效的填補 」 或類似適當地不同的時間，來處理無效的區塊，而不是無效的區塊更複雜的項目。

區塊為基礎的加密方式會有另一個屬性稱為模式，用來決定第一個區塊的第二個區塊中的資料中的資料關聯性，並以此類推。 CBC 其中一個最常使用的模式。 CBC 引進初始的隨機區塊，已知為初始化向量 (IV)，並以靜態加密以容易使用相同的金鑰加密相同的訊息不一定會產生相同的加密的輸出的結果結合在前一個區塊。

攻擊者可以使用填補 oracle，搭配 CBC 資料結構的方式，將稍有變更的訊息傳送至 oracle 公開 （expose） 的程式碼，並保留傳送資料，直到 oracle 告訴他們的資料正確。 從這個回應中，攻擊者可以解密位元組的訊息。

現代電腦的網路是這類高品質的攻擊者可以偵測很小 （少於 0.1 毫秒） 的執行差異時間在遠端系統上。 假設，成功解密只會發生在資料未遭竄改的應用程式可能容易受到攻擊工具，設計來觀察成功與不成功解密的差異。 雖然這項時間差異可能有某些語言或程式庫中比其他更重要，現在相信這是實際服務威脅中的所有語言和程式庫，當應用程式的回應失敗列入考量。

這種攻擊會依賴變更加密的資料和測試結果與 oracle 的能力。 以完全降低攻擊的唯一方法是偵測到加密資料的變更，並拒絕在其上執行任何動作。 若要這樣做的標準方式是建立資料的簽章及執行任何作業之前驗證該簽章。 簽章必須經過驗證，攻擊者無法加以建立，否則它們就可以變更加密的資料，然後計算新的簽章已變更的資料為基礎。 一個常見的適當簽章類型稱為做為索引鍵雜湊訊息驗證碼 (HMAC)。 HMAC 與總和檢查碼的所需的秘密金鑰，已知只產生 HMAC 的人員，並確認它的人員。 未使用擁有金鑰，您不會產生正確的 HMAC。 當您收到您的資料時，請接受加密的資料，您和寄件者共用，然後比較的 HMAC 它們傳送給其中一個針對您計算獨立計算使用之祕密金鑰的 HMAC。 這項比較必須是固定的時間，否則您新增另一個偵測到 oracle，允許不同類型的攻擊。

在 [摘要] 使用填補 CBC 區塊加密安全地，您必須將它們結合 HMAC （或其他資料完整性檢查） 進行驗證再試一次使用常數時間比較，來解密資料。 因為所有已變更的訊息採取相同的時間，以產生回應，防止攻擊。

## <a name="who-is-vulnerable"></a>易受攻擊是誰

這項弱點適用於 managed 和原生應用程式會執行自己的加密與解密。 這包括，例如：

- 加密 cookie，以更新解密在伺服器上的應用程式。
- 可讓您的使用者將資料插入資料表的資料行的資料庫應用程式會稍後進行解密。
- 資料傳輸應用程式所使用的加密來保護傳輸中的資料使用共用的金鑰。
- 應用程式來加密及解密訊息 「 內部 」 TLS 通道。

請注意，使用 TLS 單獨可能無法保護您在這些案例。

易受攻擊的應用程式：

- 使用 CBC 加密模式可驗證的填補模式中，例如 PKCS #7 或 ANSI X.923 解密資料。
- 執行解密，而不需要執行資料完整性檢查 （透過 MAC 或非對稱的數位簽章）。

這也適用於之上的抽象概念，透過下列基本類型，例如密碼編譯訊息語法 (PKCS #7/CMS) EnvelopedData 結構頂端的應用程式。

## <a name="related-areas-of-concern"></a>相關的問題區域

研究導致 Microsoft 進一步考量到會填補 ISO 10126 等同填補訊息具有已知或可預測的頁尾結構時的 CBC 訊息。 例如，內容備妥的 W3C XML 加密語法和處理建議 (xmlenc EncryptedXml) 的規則。 雖然 W3C 指引，來簽署訊息，然後加密已被視為適當時，Microsoft 現在建議您一律加密後簽署。

應用程式開發人員應該一律留意驗證適用性的非對稱簽章金鑰，因為沒有之間的非對稱金鑰和任意訊息沒有固有的信任關係。

## <a name="details"></a>詳細資料

在過去，已經很重要，來加密和驗證很重要的資料，使用方式如 HMAC 或 RSA 簽章的共識。 不過，有較少清楚的指引，來選擇加密和驗證作業的序列。 此文件中詳述的弱點，因為 Microsoft 的指南現在是一律使用 「 加密然後-簽署 」 開發架構。 也就是第一次使用對稱金鑰，加密資料，然後透過加密文字 （已加密的資料） 會計算 MAC 或非對稱簽章。 解密資料，當執行反向。 首先，確認 MAC 或簽章的加密文字，然後再將其解密。

稱為 「 填補 oracle 攻擊"存在於過去 10 年的已知弱點的類別。 這些弱點可能會允許攻擊者來解密使用不超過 4096 嘗試每個資料區塊的區塊對稱演算法，例如 AES 和 3DES 加密資料。 這些弱點請使用下列事實的區塊密碼最常搭配可驗證的邊框距離結尾的資料。 它找不到攻擊者可以竄改加密文字，並找出是否遭到竄改會導致錯誤的尾端填補格式中，是否攻擊者可以解密資料。

一開始，實際的攻擊根據服務，會傳回不同的錯誤代碼，根據是否有效，例如 ASP.NET 的弱點可能會填補[MS10 070](https://technet.microsoft.com/library/security/ms10-070.aspx)。 不過，Microsoft 現在相信會實際進行類似攻擊使用只在處理有效和無效的邊框距離之間的時間差異。

而不發出任何資訊的加密配置會使用簽章，並指定長度的資料 （不管內容） 的固定執行階段與執行簽章驗證，可以確認資料完整性攻擊者透過[側邊通道](https://en.wikipedia.org/wiki/Side-channel_attack)。 因為完整性檢查會拒絕遭竄改的任何訊息，以降低填補 oracle 威脅。

## <a name="guidance"></a>指引

首先和最重要，Microsoft 建議透過傳輸層安全性 (TLS)，以安全通訊端層 (SSL) 的後續版本需要傳輸任何資料的機密性。

接下來，分析您的應用程式：

- 了解精確地將您要執行何種加密，並由平台和您所使用的應用程式開發介面提供何種加密。
- 會確認每個對稱的每個層級的用法[區塊編碼演算法](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)，例如 AES 和 3DES、 CBC 模式的合併使用的密碼為索引鍵的資料完整性檢查 (非對稱簽章的 HMAC，或變更的 cipher 模式[驗證加密](https://en.wikipedia.org/wiki/Authenticated_encryption)(AE) 模式，例如 GCM 或 CCM)。

根據目前的參考資料，因此一般認為當驗證及加密的步驟會單獨執行加密的非 AE 模式中，驗證加密文字 （加密--簽署） 是最佳的一般選項。 不過，沒有一體適用接聽正確密碼編譯，這項通則不從專業安全無不如導向的建議。

無法變更其訊息的格式，但執行未經驗證的 CBC 解密的應用程式應該在嘗試併入緩和措施，例如：

- 不允許的解密程式來驗證或移除填補解密：
  - 已套用任何填補仍然需要移除或略過，您要移動到您的應用程式的負擔。
  - 好處是，填補驗證及移除可以會合併到其他應用程式資料的驗證邏輯。 如果填補驗證及資料驗證，就可以完成以常數時間會降低威脅。
  - 因為填補的解譯會改變認知的訊息長度，仍可能從這種方法發出的計時資訊。
- 變更 ISO10126 解密填補模式：
  - ISO10126 解密填補為相容於 PKCS7 加密填補和 ANSIX923 加密填補。
  - 變更模式會填補 oracle 知識減少至 1 個位元組，而不是整個區塊。 不過，如果內容有已知的頁尾，結尾 XML 項目，例如相關的攻擊可以繼續攻擊其餘的訊息。
  - 這也不會阻止純文字攻擊者可以強制轉換相同的純文字加密多次以不同的訊息位移的情況下復原。
- 閘道解密呼叫水輥計時訊號的評估：
  - 計算的保留時間必須至少有超過最大解密作業會採取任何包含填補的資料區段的時間量。
  - 時間運算，應該要根據中的指導方針[取得高解析度的時間戳記](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx)，不是使用<xref:System.Environment.TickCount?displayProperty=nameWithType>（受限於向前復原超過/溢位） 上或減去兩個的系統時間戳記 （受限於 NTP 調整錯誤）。
  - 時間運算必須包含解密作業，包括所有可能的例外狀況中管理或 c + + 應用程式，不只是尾端填補。
  - 如果已尚未決定成功或失敗，計時閘道需要過期時傳回失敗。
- 要執行未經驗證的解密的服務都應該具有監視中用來偵測已通過大量的 「 無效 」 訊息。
  - 請記住此訊號會誤判 （合法損毀的資料） 和誤否定 （分配段夠長的時間，以避開偵測攻擊）。

## <a name="finding-vulnerable-code---native-applications"></a>尋找受到程式碼的原生應用程式

針對 Windows 密碼編譯所建立的程式： Next Generation (CNG) 程式庫：

- 解密呼叫[BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx)，並指定`BCRYPT_BLOCK_PADDING`旗標。
- 索引鍵的控制代碼已藉由呼叫初始化[BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx)與[BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE)設`BCRYPT_CHAIN_MODE_CBC`。
  - 因為`BCRYPT_CHAIN_MODE_CBC`是預設設定，受影響的程式碼可能未指派任何值`BCRYPT_CHAINING_MODE`。

針對較舊的 Windows 密碼編譯 API 所建立的程式：

- 解密呼叫[CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx)與`Final=TRUE`。
- 索引鍵的控制代碼已藉由呼叫初始化[CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx)與[KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE)設`CRYPT_MODE_CBC`。
  - 因為`CRYPT_MODE_CBC`是預設設定，受影響的程式碼可能未指派任何值`KP_MODE`。

## <a name="finding-vulnerable-code---managed-applications"></a>尋找受到程式碼的 managed 應用程式

- 解密呼叫<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor>或<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])>方法<xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>。
  - 這包括.NET 中的下列衍生型別，但也可能包括第三方類型：
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
  - 因為<xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>是預設設定，受影響的程式碼可能永遠不會指派<xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>屬性。
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>屬性設定為 <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - 因為<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>是預設設定，受影響的程式碼可能永遠不會指派<xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>屬性。

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>密碼編譯訊息語法中尋找受到程式碼-

未經驗證的 CMS EnvelopedData 訊息其加密的內容會使用 CBC 模式的 AES （2.16.840.1.101.3.4.1.2、 2.16.840.1.101.3.4.1.22、 2.16.840.1.101.3.4.1.42）、 DES (1.3.14.3.2.7)、 3DES (1.2.840.113549.3.7) 或 RC2 (1.2.840.113549.3.2) 是易受攻擊，以及做為訊息使用 CBC 模式的任何其他的區塊加密演算法。

資料流加密不容易受到這項特定弱點，Microsoft 建議一律在檢查 ContentEncryptionAlgorithm 值進行驗證資料。

對於受管理的應用程式，blob 可以是 CMS EnvelopedData 偵測到任何值，傳遞至<xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>。

原生應用程式，可以偵測 CMS EnvelopedData blob 做為 CMS 控點，透過提供任何值[CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx)其產生[CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx)是`CMSG_ENVELOPED`，及/或 CMS 控制代碼稍後傳送`CMSG_CTRL_DECRYPT`指令透過[CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx)。

## <a name="vulnerable-code-example---managed"></a>易受攻擊的程式碼範例-管理

這個方法會讀取 cookie，然後加以解密及檢視任何資料完整性檢查。 因此，使用者已收到，或任何攻擊者取得加密的 cookie 值，這個方法所讀取的 cookie 的內容可能會遭受攻擊。

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

## <a name="example-code-following-recommended-practices---managed"></a>範例程式碼下列建議的作法-管理

下列範例程式碼會使用非標準的訊息格式

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

其中`cipher_algorithm_id`和`hmac_algorithm_id`演算法識別項是應用程式的本機 （非標準） 的這些演算法。 這些識別項合理的其他部分而不是您現有的訊息通訊協定為裸機串連位元組資料流。

此範例也使用單一的主要金鑰來加密金鑰和 HMAC 金鑰衍生。 這會提供方便同時開啟單一索引鍵的應用程式到做為索引鍵雙重應用程式，並保留兩個索引鍵為不同的值。 進一步可保證沒有進行同步處理無法取得的 HMAC 金鑰和加密金鑰。

此範例不接受<xref:System.IO.Stream>加密或解密。 目前的資料格式可讓一段式加密困難因為`hmac_tag`值之前加密文字。 不過，因為它讓剖析器更簡單的開頭會將所有的固定大小的項目已被選擇這種格式。 此資料格式時，一段式解密是可行的實作者 cautioned 呼叫 GetHashAndReset 並驗證的結果，然後再呼叫 TransformFinalBlock 也一樣。 如果資料流加密很重要的不同的 AE 模式可能需要。

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
