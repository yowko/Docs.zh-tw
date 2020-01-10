---
title: CBC 解密弱點
description: 瞭解如何使用填補來偵測和減輕密碼區塊連結（CBC）模式對稱解密的時間弱點。
ms.date: 06/12/2018
author: blowdart
ms.openlocfilehash: 87f8e3c53e4d06f6a4edc7670891ac83ec8d65ab
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705843"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>使用填補進行 CBC 模式對稱解密的時間弱點

Microsoft 認為在套用可驗證的填補時，若未先確定加密文字的完整性，就無法再將加密的資料解密為對稱式加密模式，但非常特定具體. 此 judgement 是以目前已知的密碼編譯研究為基礎。 

## <a name="introduction"></a>簡介

填補 oracle 攻擊是針對加密資料的一種攻擊類型，可讓攻擊者解密資料的內容，而不需要知道金鑰。

Oracle 指的是「告訴」，它會提供攻擊者有關他們所執行的動作是否正確的資訊。 想像一下使用子系來播放電路板或撲克牌遊戲。 當她的臉部上有很大的笑臉時，因為她認為她要做的是一種不錯的移動，這就是 oracle。 身為對手，您可以使用此 oracle 來適當規劃下一個移動。

填補是特定的密碼編譯詞彙。 有些是用來加密資料的演算法，可處理資料區塊，其中每個區塊都是固定的大小。 如果您想要加密的資料不是用來填滿區塊的正確大小，您的資料將會填補，直到它完成為止。 許多形式的填補要求一定要有填補，即使原始輸入的大小正確也一樣。 如此一來，在解密時，一律可以安全地移除填補。

將這兩件事放在一起，以 oracle 填補軟體執行會顯示解密的資料是否有有效的填補。 Oracle 可以像傳回「無效填補」之類的值一樣簡單，或比較複雜的東西，像是採取顯著提升不同的時間來處理有效的區塊，而不是不正確區塊。

以區塊為基礎的加密具有另一個屬性，稱為「模式」（mode），可判斷第一個區塊中的資料與第二個區塊中的資料之間的關聯性等等。 最常使用的模式之一是 CBC。 CBC 引進初始隨機區塊（稱為初始化向量（IV）），並將前一個區塊與靜態加密的結果結合，讓它以相同的金鑰來加密相同的訊息不一定會產生相同的加密輸出。

攻擊者可以將 oracle 填補與 CBC 資料的結構化，以將稍有變更的訊息傳送至公開 oracle 的程式碼，並持續傳送資料，直到 oracle 通知資料正確為止。 攻擊者可以從這個回應，以位元組為單位來解密訊息位元組。

新式電腦網路的品質很高，攻擊者可以在遠端系統上偵測到非常小（少於0.1 毫秒）的執行時間差異。 假設成功解密的應用程式，只有在資料未遭篡改時才會發生，這可能會受到攻擊，而這些工具是設計用來觀察成功和不成功解密的差異。 雖然這種時間差異在某些語言或程式庫中可能會比其他方式更重要，但是現在我們認為當應用程式的回應失敗時，對於所有語言和程式庫而言，這是一項實際的威脅。

這種攻擊會依賴變更加密資料的能力，並以 oracle 測試結果。 完全減輕攻擊的唯一方法，是偵測加密資料的變更，並拒絕對其執行任何動作。 執行此動作的標準方式是建立資料的簽章，並在執行任何作業之前驗證該簽章。 簽章必須是可驗證的，攻擊者無法建立簽章，否則會變更加密的資料，然後根據變更的資料計算新的簽章。 適當簽章的其中一個常見類型稱為「金鑰雜湊訊息驗證碼（HMAC）」。 HMAC 與總和檢查碼不同之處在于，它會接受秘密金鑰，只知道產生 HMAC 的人員，以及驗證它的人員。 若未擁有金鑰，您就無法產生正確的 HMAC。 當您收到資料時，您會取得加密的資料，並使用您和寄件者共用的秘密金鑰來獨立計算 HMAC，然後將其所傳送的 HMAC 與您所計算的帳戶進行比對。 這項比較必須是固定時間，否則您已加入另一個可偵測的 oracle，以允許不同類型的攻擊。

總而言之，若要安全地使用填補的 CBC 區塊加密，您必須將它們與 HMAC （或其他資料完整性檢查）結合，以便在嘗試解密資料之前，使用持續時間比較來驗證。 由於所有改變的訊息會耗用相同的時間來產生回應，因此會防止攻擊。

## <a name="who-is-vulnerable"></a>易受攻擊者

此弱點適用于執行自己的加密和解密的受控和原生應用程式。 這包括：

- 加密 cookie 的應用程式，以便稍後在伺服器上解密。
- 一種資料庫應用程式，可讓使用者將資料插入資料表，並在稍後將其解密。
- 依賴加密使用共用金鑰來保護傳輸中資料的資料傳輸應用程式。
- 在 TLS 通道中加密和解密訊息的應用程式。

請注意，在這些情況下，單獨使用 TLS 可能無法保護您。

易受攻擊的應用程式：

- 使用 CBC 加密模式搭配可驗證的填補模式（例如 PKCS # 7 或 ANSI 923）來解密資料。
- 執行解密，而不執行資料完整性檢查（透過 MAC 或非對稱數位簽章）。

這也適用于以抽象概念為基礎的應用程式，而這些基本專案是以「密碼編譯訊息語法」（PKCS # 7/CMS） EnvelopedData 結構為基礎。

## <a name="related-areas-of-concern"></a>相關的考慮區域

當訊息具有知名或可預測的頁尾結構時，Research 讓 Microsoft 進一步關心以 ISO 10126 對等填補填補的 CBC 訊息。 例如，在 W3C XML 加密語法和處理建議的規則下準備的內容（xmlenc、System.security.cryptography.xml.encryptedxml.encrypt）。 雖然簽署訊息的 W3C 指導方針，在當時會將加密視為適當，但 Microsoft 現在建議一律進行加密-then 簽署。

應用程式開發人員應該一律留意驗證非對稱簽章金鑰的適用性，因為非對稱金鑰與任意訊息之間沒有任何固有的信任關係。

## <a name="details"></a>詳細資料

在過去，已有共識，請務必使用 HMAC 或 RSA 簽章等方式來加密和驗證重要資料。 不過，對於如何排序加密和驗證作業，並沒有更清楚的指引。 由於本文詳述的弱點，Microsoft 的指導方針現在一律使用「加密後簽署」的範例。 也就是說，先使用對稱金鑰來加密資料，然後透過加密文字（加密資料）計算 MAC 或非對稱簽章。 解密資料時，請反向執行。 首先，確認加密文字的 MAC 或簽章，然後將它解密。

已知「填補 oracle 攻擊」這類弱點已有超過10年的時間。 這些弱點可讓攻擊者將對稱式區塊演算法（例如 AES 和3DES）所加密的資料解密，並在每個資料區塊中使用4096次以上的嘗試。 這些弱點會利用區塊密碼最常與結尾的可驗證填補資料搭配使用的事實。 發現，如果攻擊者可以使用加密文字來篡改，並找出在結尾處的填補格式是否造成了錯誤，攻擊者就可以將資料解密。

一開始，實際的攻擊是以服務為基礎，根據填補是否有效而傳回不同的錯誤碼，例如 ASP.NET 弱[MS10-070](/security-updates/SecurityBulletins/2010/ms10-070)。 不過，Microsoft 現在相信，只使用處理有效和無效填補之間的時間差異來進行類似的攻擊。

假設加密配置採用簽章，而且針對指定的資料長度使用固定的執行時間來執行簽章驗證（不論內容如何），可以驗證資料完整性，而不需要透過[端通道](https://en.wikipedia.org/wiki/Side-channel_attack)向攻擊者發出任何資訊。 由於完整性檢查會拒絕任何遭篡改的訊息，因此會降低對 oracle 威脅的填補。

## <a name="guidance"></a>指引

首先最重要的是，Microsoft 建議必須透過傳輸層安全性（TLS）傳輸任何具有機密性的資料，安全通訊端層（SSL）的後續版本。

接下來，分析您的應用程式以：

- 精確瞭解您正在執行的加密，以及您所使用的平臺和 Api 提供了哪些加密功能。
- 確定每一層的對稱式[區塊加密演算法](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)（例如 AES 和3des）在 CBC 模式中的每個使用方式都納入了秘密金鑰資料完整性檢查（非對稱簽章、HMAC，或將加密模式變更為[已驗證的加密](https://en.wikipedia.org/wiki/Authenticated_encryption)（AE）模式，例如 GCM 或 CCM）。

根據目前的研究，通常會認為當驗證和加密步驟獨立執行，以進行非 AE 模式的加密時，驗證加密文字（encrypt-then-sign）是最佳的一般選項。 不過，密碼編譯的所有正確答案並不適用，而這項一般化並不是來自專業解碼員的導向建議。

我們鼓勵無法變更訊息格式，但執行未驗證之 CBC 解密的應用程式嘗試納入緩和措施，例如：

- 解密而不允許解密器驗證或移除填補：
  - 所有已套用的填補都必須移除或略過，您會將負擔移到您的應用程式中。
  - 其優點是填補驗證和移除可以併入其他應用程式資料驗證邏輯中。 如果填補驗證和資料驗證可以在固定時間內完成，就會減少威脅。
  - 由於填補的轉譯會變更所見的訊息長度，因此此方法可能仍會發出計時資訊。
- 將 [解密填補模式] 變更為 ISO10126：
  - ISO10126 解密填補與 PKCS7 加密填補和 ANSIX923 加密填補相容。
  - 變更模式可將 oracle 知識的填補減少為1個位元組，而不是整個區塊。 不過，如果內容具有已知的頁尾（例如，結尾 XML 元素），相關的攻擊可能會繼續攻擊訊息的其餘部分。
  - 這也不會防止純文字復原，因為攻擊者可以使用不同的訊息位移，強制將相同的純文字還原成多次加密。
- 閘道評估要 dampen 計時信號的解密呼叫：
  - 「保存時間」的計算，必須有超過解密作業針對任何包含填補之資料區段所需的最大時間量。
  - 應該根據取得[高解析度時間戳記](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)中的指引來完成時間計算，而不是使用 <xref:System.Environment.TickCount?displayProperty=nameWithType> （可能會變換/溢位）或減去兩個系統時間戳記（受限於 NTP 調整錯誤）。
  - 時間計算必須包含解密作業，包括 managed 或C++應用程式中所有可能的例外狀況，而不只是填補到結尾。
  - 如果已判定成功或失敗，計時閘道就必須在過期時傳回失敗。
- 執行未驗證解密的服務應該準備好監視，以偵測是否有大量的「無效」訊息。
  - 請記住，這個信號會同時攜帶誤報（合法損毀的資料）和誤否定（將攻擊分散到很長的時間以規避偵測）。

## <a name="finding-vulnerable-code---native-applications"></a>尋找易受攻擊的程式碼原生應用程式

針對 Windows 密碼編譯：新一代（CNG）程式庫所建立的程式：

- 解密呼叫是[BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt)，指定 `BCRYPT_BLOCK_PADDING` 旗標。
- 已初始化索引鍵控制碼，方法是呼叫[BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty)並將[BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE)設為 `BCRYPT_CHAIN_MODE_CBC`。
  - 由於 `BCRYPT_CHAIN_MODE_CBC` 是預設值，因此受影響的程式碼可能未指派任何 `BCRYPT_CHAINING_MODE`的值。

針對舊版 Windows 密碼編譯 API 所建立的程式：

- 解密呼叫是使用 `Final=TRUE`來[CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) 。
- 已初始化索引鍵控制碼，方法是呼叫[CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam)並將[KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam)設為 `CRYPT_MODE_CBC`。
  - 由於 `CRYPT_MODE_CBC` 是預設值，因此受影響的程式碼可能未指派任何 `KP_MODE`的值。

## <a name="finding-vulnerable-code---managed-applications"></a>尋找易受程式碼管理的應用程式

- 解密呼叫是在 <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>上的 <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> 或 <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> 方法。
  - 這包括 .NET 中的下列衍生類型，但也可能包含協力廠商類型：
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
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> 屬性已設為 <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>、<xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>或 <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>。
  - 由於 <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> 是預設值，因此受影響的程式碼可能永遠不會指派 <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> 屬性。
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> 屬性已設為 <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - 由於 <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> 是預設值，因此受影響的程式碼可能永遠不會指派 <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> 屬性。

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>尋找易受攻擊的程式碼密碼編譯訊息語法

未經驗證的 CMS EnvelopedData 訊息，其加密內容使用 AES （2.16.840.1.101.3.4.1.2、2.16.840.1.101.3.4.1.22、2.16.840.1.101.3.4.1.42）、DES （1.3.14.3.2.7）、3DES （1.2.840.113549.3.7）或 RC2 （1.2.840.113549.3.2）的 CBC 模式易受攻擊，以及在 CBC 模式中使用任何其他區塊密碼演算法的訊息。

雖然串流密碼不容易受到此特定弱點的影響，但 Microsoft 建議一律透過檢查 ContentEncryptionAlgorithm 值來驗證資料。

對於受控應用程式，可以偵測到 CMS EnvelopedData blob，做為傳遞給 <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>的任何值。

對於原生應用程式，可以透過[CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate)來偵測 cms EnvelopedData blob，其產生的[CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam)是由 `CMSG_ENVELOPED` 和/或 cms 處理常式稍後透過[CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol)傳送 `CMSG_CTRL_DECRYPT` 指令的任何值。

## <a name="vulnerable-code-example---managed"></a>易受攻擊的程式碼範例-受控

這個方法會讀取 cookie 並將它解密，而且不會顯示任何資料完整性檢查。 因此，此方法所讀取之 cookie 的內容可能會受到接收它的使用者攻擊，或已取得加密 cookie 值的任何攻擊者所攻擊。

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

## <a name="example-code-following-recommended-practices---managed"></a>遵循建議做法的範例程式碼-受管理

下列範例程式碼會使用非標準的訊息格式

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

其中，`cipher_algorithm_id` 和 `hmac_algorithm_id` 演算法識別碼是那些演算法的應用程式本機（非標準）標記法。 這些識別碼在現有訊息通訊協定的其他部分中可能會有意義，而不是以裸機串連的位流。

這個範例也會使用單一主要金鑰來衍生加密金鑰和 HMAC 金鑰。 這是為了方便您將單一索引應用程式轉換成雙重索引應用程式，並鼓勵將這兩個索引鍵保留為不同的值。 它會進一步保證 HMAC 金鑰和加密金鑰無法同步處理。

此範例不接受加密或解密的 <xref:System.IO.Stream>。 目前的資料格式會使一次加密變得很棘手，因為 `hmac_tag` 值在加密文字之前。 不過，這種格式是選擇的，因為它會在一開始保留所有固定大小的元素，以簡化剖析器的作業。 有了這種資料格式，就可以使用一次傳遞解密，雖然實施者會匯呼叫 GetHashAndReset，並在呼叫 System.security.cryptography.icryptotransform.transformfinalblock 之前驗證結果。 如果串流加密很重要，則可能需要不同的 AE 模式。

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
