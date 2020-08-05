---
title: CBC 解密弱點
description: 瞭解如何使用填補 (CBC) 模式對稱式解密，偵測和減輕密碼區塊連結的時機弱點。
ms.date: 07/15/2020
author: blowdart
ms.openlocfilehash: e9bbeeefa2ef6ef90f3a752742667d30aec0a3da
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557199"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="4f5f2-103">使用填補進行 CBC 模式對稱解密的時間弱點</span><span class="sxs-lookup"><span data-stu-id="4f5f2-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="4f5f2-104">Microsoft 認為，如果已套用可驗證的填補，而未先確定加密文字的完整性，則不需要先確定加密文字的完整性，就能解密以密碼區塊連結 (CBC) 模式對稱加密的資料，但非常特定的情況除外。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-104">Microsoft believes that it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext, except for very specific circumstances.</span></span> <span data-ttu-id="4f5f2-105">此 judgement 是以目前已知的密碼編譯研究為基礎。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-105">This judgement is based on currently known cryptographic research.</span></span>

## <a name="introduction"></a><span data-ttu-id="4f5f2-106">簡介</span><span class="sxs-lookup"><span data-stu-id="4f5f2-106">Introduction</span></span>

<span data-ttu-id="4f5f2-107">填補 oracle 攻擊是針對加密資料的一種攻擊類型，可讓攻擊者解密資料的內容，而不需要知道金鑰。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-107">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="4f5f2-108">Oracle 指的是「告訴」，它會提供攻擊者有關他們所執行的動作是否正確的資訊。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-108">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="4f5f2-109">想像一下使用子系來播放電路板或撲克牌遊戲。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-109">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="4f5f2-110">當他們的臉部表面上有很大的笑臉，因為他們認為這是 oracle。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-110">When their face lights up with a big smile because they think they're about to make a good move, that's an oracle.</span></span> <span data-ttu-id="4f5f2-111">身為對手，您可以使用此 oracle 來適當規劃下一個移動。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-111">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="4f5f2-112">填補是特定的密碼編譯詞彙。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-112">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="4f5f2-113">有些是用來加密資料的演算法，可處理資料區塊，其中每個區塊都是固定的大小。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-113">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="4f5f2-114">如果您想要加密的資料不是用來填滿區塊的正確大小，您的資料將會填補，直到它完成為止。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-114">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="4f5f2-115">許多形式的填補要求一定要有填補，即使原始輸入的大小正確也一樣。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-115">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="4f5f2-116">如此一來，在解密時，一律可以安全地移除填補。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-116">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="4f5f2-117">將這兩件事放在一起，以 oracle 填補軟體執行會顯示解密的資料是否有有效的填補。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-117">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="4f5f2-118">Oracle 可以像傳回「無效填補」之類的值一樣簡單，或比較複雜的東西，像是採取顯著提升不同的時間來處理有效的區塊，而不是不正確區塊。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-118">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="4f5f2-119">以區塊為基礎的加密具有另一個屬性，稱為「模式」（mode），可判斷第一個區塊中的資料與第二個區塊中的資料之間的關聯性等等。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-119">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="4f5f2-120">最常使用的模式之一是 CBC。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-120">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="4f5f2-121">CBC 引進初始隨機區塊（稱為初始化向量 (IV) ），並將前一個區塊與靜態加密的結果結合，讓它能夠使用相同的金鑰來加密相同的訊息，而不一定會產生相同的加密輸出。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-121">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="4f5f2-122">攻擊者可以將 oracle 填補與 CBC 資料的結構化，以將稍有變更的訊息傳送至公開 oracle 的程式碼，並持續傳送資料，直到 oracle 通知資料正確為止。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-122">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="4f5f2-123">攻擊者可以從這個回應，以位元組為單位來解密訊息位元組。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-123">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="4f5f2-124">新式電腦網路的品質很高，攻擊者可以偵測到非常小的 (低於0.1 毫秒，) 在遠端系統上的執行時間差異。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-124">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span><span data-ttu-id="4f5f2-125">假設成功解密的應用程式，只有在資料未遭篡改時才會發生，這可能會受到攻擊，而這些工具是設計用來觀察成功和不成功解密的差異。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-125"> Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="4f5f2-126">雖然這種時間差異在某些語言或程式庫中可能會比其他方式更重要，但是現在我們認為當應用程式的回應失敗時，對於所有語言和程式庫而言，這是一項實際的威脅。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-126">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="4f5f2-127">這種攻擊會依賴變更加密資料的能力，並以 oracle 測試結果。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-127">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="4f5f2-128">完全減輕攻擊的唯一方法，是偵測加密資料的變更，並拒絕對其執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-128">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="4f5f2-129">執行此動作的標準方式是建立資料的簽章，並在執行任何作業之前驗證該簽章。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-129">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="4f5f2-130">簽章必須是可驗證的，攻擊者無法建立簽章，否則會變更加密的資料，然後根據變更的資料計算新的簽章。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-130">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="4f5f2-131">一種常見的適當簽章類型稱為「金鑰雜湊消息驗證」程式碼， (HMAC) 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-131">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="4f5f2-132">HMAC 與總和檢查碼不同之處在于，它會接受秘密金鑰，只知道產生 HMAC 的人員，以及驗證它的人員。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-132">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="4f5f2-133">若未擁有金鑰，您就無法產生正確的 HMAC。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-133">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="4f5f2-134">當您收到資料時，您會取得加密的資料，並使用您和寄件者共用的秘密金鑰來獨立計算 HMAC，然後將其所傳送的 HMAC 與您所計算的帳戶進行比對。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-134">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="4f5f2-135">這項比較必須是固定時間，否則您已加入另一個可偵測的 oracle，以允許不同類型的攻擊。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-135">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="4f5f2-136">總而言之，若要安全地使用填補的 CBC 區塊加密，您必須將它們與 HMAC (或另一個資料完整性檢查結合) ，以便在嘗試解密資料之前，使用持續時間比較來驗證。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-136">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="4f5f2-137">由於所有改變的訊息會耗用相同的時間來產生回應，因此會防止攻擊。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-137">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="4f5f2-138">易受攻擊者</span><span class="sxs-lookup"><span data-stu-id="4f5f2-138">Who is vulnerable</span></span>

<span data-ttu-id="4f5f2-139">此弱點適用于執行自己的加密和解密的受控和原生應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-139">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="4f5f2-140">這包括：</span><span class="sxs-lookup"><span data-stu-id="4f5f2-140">This includes, for example:</span></span>

- <span data-ttu-id="4f5f2-141">加密 cookie 的應用程式，以便稍後在伺服器上解密。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-141">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="4f5f2-142">一種資料庫應用程式，可讓使用者將資料插入資料表，並在稍後將其解密。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-142">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="4f5f2-143">依賴加密使用共用金鑰來保護傳輸中資料的資料傳輸應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-143">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="4f5f2-144">在 TLS 通道中加密和解密訊息的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-144">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="4f5f2-145">請注意，在這些情況下，單獨使用 TLS 可能無法保護您。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-145">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="4f5f2-146">易受攻擊的應用程式：</span><span class="sxs-lookup"><span data-stu-id="4f5f2-146">A vulnerable application:</span></span>

- <span data-ttu-id="4f5f2-147">使用 CBC 加密模式搭配可驗證的填補模式（例如 PKCS # 7 或 ANSI 923）來解密資料。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-147">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="4f5f2-148">執行解密，而不需透過 MAC 或非對稱數位簽章)  (執行資料完整性檢查。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-148">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="4f5f2-149">這也適用于在這些基本專案之上以抽象概念為基礎的應用程式，例如 (PKCS # 7/CMS) EnvelopedData 結構的密碼編譯訊息語法。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-149">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="4f5f2-150">相關的考慮區域</span><span class="sxs-lookup"><span data-stu-id="4f5f2-150">Related areas of concern</span></span>

<span data-ttu-id="4f5f2-151">當訊息具有知名或可預測的頁尾結構時，Research 讓 Microsoft 進一步關心以 ISO 10126 對等填補填補的 CBC 訊息。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-151">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="4f5f2-152">例如，在 W3C XML 加密語法和處理建議規則下準備的內容， (xmlenc，System.security.cryptography.xml.encryptedxml.encrypt) 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-152">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="4f5f2-153">雖然簽署訊息的 W3C 指導方針，在當時會將加密視為適當，但 Microsoft 現在建議一律進行加密-then 簽署。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-153">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="4f5f2-154">應用程式開發人員應該一律留意驗證非對稱簽章金鑰的適用性，因為非對稱金鑰與任意訊息之間沒有任何固有的信任關係。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-154">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="4f5f2-155">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4f5f2-155">Details</span></span>

<span data-ttu-id="4f5f2-156">在過去，已有共識，請務必使用 HMAC 或 RSA 簽章等方式來加密和驗證重要資料。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-156">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="4f5f2-157">不過，對於如何排序加密和驗證作業，並沒有更清楚的指引。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-157">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="4f5f2-158">由於本文詳述的弱點，Microsoft 的指導方針現在一律使用「加密後簽署」的範例。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-158">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="4f5f2-159">也就是，使用對稱金鑰來加密資料，然後透過加密文字來計算 MAC 或非對稱簽章 (加密的資料) 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-159">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="4f5f2-160">解密資料時，請反向執行。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-160">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="4f5f2-161">首先，確認加密文字的 MAC 或簽章，然後將它解密。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-161">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="4f5f2-162">已知「填補 oracle 攻擊」這類弱點已有超過10年的時間。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-162">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="4f5f2-163">這些弱點可讓攻擊者將對稱式區塊演算法（例如 AES 和3DES）所加密的資料解密，並在每個資料區塊中使用4096次以上的嘗試。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-163">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="4f5f2-164">這些弱點會利用區塊密碼最常與結尾的可驗證填補資料搭配使用的事實。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-164">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="4f5f2-165">發現，如果攻擊者可以使用加密文字來篡改，並找出在結尾處的填補格式是否造成了錯誤，攻擊者就可以將資料解密。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-165">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="4f5f2-166">一開始，實際的攻擊是以服務為基礎，根據填補是否有效而傳回不同的錯誤碼，例如 ASP.NET 弱[MS10-070](/security-updates/SecurityBulletins/2010/ms10-070)。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-166">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span></span> <span data-ttu-id="4f5f2-167">不過，Microsoft 現在相信，只使用處理有效和無效填補之間的時間差異來進行類似的攻擊。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-167">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="4f5f2-168">假設加密配置採用簽章，且針對指定的資料長度使用固定的執行時間來執行簽章驗證， (不論) 內容，都可以驗證資料完整性，而不會透過[端通道](https://en.wikipedia.org/wiki/Side-channel_attack)向攻擊者發出任何資訊。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-168">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="4f5f2-169">由於完整性檢查會拒絕任何遭篡改的訊息，因此會降低對 oracle 威脅的填補。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-169">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="4f5f2-170">指引</span><span class="sxs-lookup"><span data-stu-id="4f5f2-170">Guidance</span></span>

<span data-ttu-id="4f5f2-171">首先最重要的是，Microsoft 建議所有具有機密性的資料都必須透過傳輸層安全性傳輸 (TLS) ，安全通訊端層 (SSL) 的後續版本。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-171">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="4f5f2-172">接下來，分析您的應用程式以：</span><span class="sxs-lookup"><span data-stu-id="4f5f2-172">Next, analyze your application to:</span></span>

- <span data-ttu-id="4f5f2-173">精確瞭解您正在執行的加密，以及您所使用的平臺和 Api 提供了哪些加密功能。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-173">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="4f5f2-174">確定每一層的對稱式[區塊加密演算法](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)（例如 AES 和3des）在 CBC 模式中的每個使用方式，都不會使用秘密金鑰資料完整性檢查 (非對稱簽章、HMAC，或將加密模式變更為[已驗證的加密](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) 模式，例如 GCM 或 CCM) 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-174">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="4f5f2-175">根據目前的研究，通常會認為當驗證和加密步驟獨立執行以進行非 AE 模式的加密時，驗證加密文字 (加密-然後簽署) 是最佳的一般選項。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-175">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="4f5f2-176">不過，密碼編譯的所有正確答案並不適用，而這項一般化並不是來自專業解碼員的導向建議。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-176">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="4f5f2-177">我們鼓勵無法變更訊息格式，但執行未驗證之 CBC 解密的應用程式嘗試納入緩和措施，例如：</span><span class="sxs-lookup"><span data-stu-id="4f5f2-177">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="4f5f2-178">解密而不允許解密器驗證或移除填補：</span><span class="sxs-lookup"><span data-stu-id="4f5f2-178">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="4f5f2-179">所有已套用的填補都必須移除或略過，您會將負擔移到您的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-179">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="4f5f2-180">其優點是填補驗證和移除可以併入其他應用程式資料驗證邏輯中。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-180">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="4f5f2-181">如果填補驗證和資料驗證可以在固定時間內完成，就會減少威脅。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-181">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="4f5f2-182">由於填補的轉譯會變更所見的訊息長度，因此此方法可能仍會發出計時資訊。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-182">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="4f5f2-183">將 [解密填補模式] 變更為 ISO10126：</span><span class="sxs-lookup"><span data-stu-id="4f5f2-183">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="4f5f2-184">ISO10126 解密填補與 PKCS7 加密填補和 ANSIX923 加密填補相容。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-184">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="4f5f2-185">變更模式可將 oracle 知識的填補減少為1個位元組，而不是整個區塊。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-185">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="4f5f2-186">不過，如果內容具有已知的頁尾（例如，結尾 XML 元素），相關的攻擊可能會繼續攻擊訊息的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-186">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="4f5f2-187">這也不會防止純文字復原，因為攻擊者可以使用不同的訊息位移，強制將相同的純文字還原成多次加密。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-187">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="4f5f2-188">閘道評估要 dampen 計時信號的解密呼叫：</span><span class="sxs-lookup"><span data-stu-id="4f5f2-188">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="4f5f2-189">「保存時間」的計算，必須有超過解密作業針對任何包含填補之資料區段所需的最大時間量。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-189">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="4f5f2-190">時間運算應該根據取得[高解析度時間戳記](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)中的指引來完成，而不是使用 <xref:System.Environment.TickCount?displayProperty=nameWithType> (主體來變換/溢位) 或減去兩個系統時間戳記 (受限於 NTP 調整錯誤) 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-190">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="4f5f2-191">時間計算必須包含解密作業，包括 managed 或 c + + 應用程式中的所有可能例外狀況，而不只是填補到結尾。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-191">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="4f5f2-192">如果已判定成功或失敗，計時閘道就必須在過期時傳回失敗。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-192">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="4f5f2-193">執行未驗證解密的服務應該準備好監視，以偵測是否有大量的「無效」訊息。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-193">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="4f5f2-194">請記住，這個信號會同時攜帶誤報 (合法損毀的資料) 和誤否定 (將攻擊分散到很長的時間，以規避偵測) 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-194">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="4f5f2-195">尋找易受攻擊的程式碼原生應用程式</span><span class="sxs-lookup"><span data-stu-id="4f5f2-195">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="4f5f2-196">針對 Windows 密碼編譯：新一代 (CNG) 程式庫的程式：</span><span class="sxs-lookup"><span data-stu-id="4f5f2-196">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="4f5f2-197">解密呼叫是[BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt)，指定 `BCRYPT_BLOCK_PADDING` 旗標。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-197">The decryption call is to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="4f5f2-198">已初始化索引鍵控制碼，方法是呼叫[BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty)並將設定為[BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) `BCRYPT_CHAIN_MODE_CBC` 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-198">The key handle has been initialized by calling [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) with [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="4f5f2-199">由於 `BCRYPT_CHAIN_MODE_CBC` 是預設值，因此受影響的程式碼可能未指派任何值給 `BCRYPT_CHAINING_MODE` 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-199">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="4f5f2-200">針對舊版 Windows 密碼編譯 API 所建立的程式：</span><span class="sxs-lookup"><span data-stu-id="4f5f2-200">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="4f5f2-201">解密呼叫是使用[CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) `Final=TRUE` 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-201">The decryption call is to [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) with `Final=TRUE`.</span></span>
- <span data-ttu-id="4f5f2-202">已初始化索引鍵控制碼，方法是呼叫[CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam)並將設定為[KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) `CRYPT_MODE_CBC` 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-202">The key handle has been initialized by calling [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) with [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="4f5f2-203">由於 `CRYPT_MODE_CBC` 是預設值，因此受影響的程式碼可能未指派任何值給 `KP_MODE` 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-203">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="4f5f2-204">尋找易受程式碼管理的應用程式</span><span class="sxs-lookup"><span data-stu-id="4f5f2-204">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="4f5f2-205">解密呼叫是 <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> 上的或 <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> 方法 <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-205">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="4f5f2-206">這包括 .NET 中的下列衍生類型，但也可能包含協力廠商類型：</span><span class="sxs-lookup"><span data-stu-id="4f5f2-206">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="4f5f2-207"><xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>屬性已設定為 <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> 、 <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType> 或 <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-207">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="4f5f2-208">由於 <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> 是預設值，因此受影響的程式碼可能永遠不會指派 <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-208">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="4f5f2-209"><xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>屬性已設定為<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4f5f2-209">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="4f5f2-210">由於 <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> 是預設值，因此受影響的程式碼可能永遠不會指派 <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-210">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="4f5f2-211">尋找易受攻擊的程式碼密碼編譯訊息語法</span><span class="sxs-lookup"><span data-stu-id="4f5f2-211">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="4f5f2-212">未經驗證的 CMS EnvelopedData 訊息，其加密內容使用 AES 的 CBC 模式 (2.16.840.1.101.3.4.1.2、2.16.840.1.101.3.4.1.22、2.16.840.1.101.3.4.1.42) 、DES (1.3.14.3.2.7) 、3DES (1.2.840.113549.3.7) 或 RC2 (1.2.840.113549.3.2) 會受到攻擊，以及在 CBC 模式中使用任何其他區塊密碼演算法的訊息。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-212">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="4f5f2-213">雖然串流密碼不容易受到此特定弱點的影響，但 Microsoft 建議一律透過檢查 ContentEncryptionAlgorithm 值來驗證資料。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-213">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="4f5f2-214">針對受控應用程式，可以將 CMS EnvelopedData blob 當做傳遞至的任何值來偵測 <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-214">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="4f5f2-215">對於原生應用程式，可以透過[CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) （其產生的[CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam)為 `CMSG_ENVELOPED` 和/或 cms 控制碼，稍後透過 CryptMsgControl 傳送指示），將 cms ENVELOPEDDATA blob 視為提供給 cms 控制碼的任何值 `CMSG_CTRL_DECRYPT` 。 [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol)</span><span class="sxs-lookup"><span data-stu-id="4f5f2-215">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) whose resulting [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="4f5f2-216">易受攻擊的程式碼範例-受控</span><span class="sxs-lookup"><span data-stu-id="4f5f2-216">Vulnerable code example - managed</span></span>

<span data-ttu-id="4f5f2-217">這個方法會讀取 cookie 並將它解密，而且不會顯示任何資料完整性檢查。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-217">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="4f5f2-218">因此，此方法所讀取之 cookie 的內容可能會受到接收它的使用者攻擊，或已取得加密 cookie 值的任何攻擊者所攻擊。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-218">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="4f5f2-219">遵循建議做法的範例程式碼-受管理</span><span class="sxs-lookup"><span data-stu-id="4f5f2-219">Example code following recommended practices - managed</span></span>

<span data-ttu-id="4f5f2-220">下列範例程式碼會使用非標準的訊息格式</span><span class="sxs-lookup"><span data-stu-id="4f5f2-220">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="4f5f2-221">其中 `cipher_algorithm_id` 和 `hmac_algorithm_id` 演算法識別碼是應用程式本機 (這些演算法的非標準) 標記法。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-221">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="4f5f2-222">這些識別碼在現有訊息通訊協定的其他部分中可能會有意義，而不是以裸機串連的位流。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-222">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="4f5f2-223">這個範例也會使用單一主要金鑰來衍生加密金鑰和 HMAC 金鑰。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-223">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="4f5f2-224">這是為了方便您將單一索引應用程式轉換成雙重索引應用程式，並鼓勵將這兩個索引鍵保留為不同的值。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-224">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="4f5f2-225">它會進一步保證 HMAC 金鑰和加密金鑰無法同步處理。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-225">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="4f5f2-226">這個範例不接受 <xref:System.IO.Stream> 加密或解密的。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-226">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="4f5f2-227">目前的資料格式會使單次加密變得很艱難，因為 `hmac_tag` 值在加密文字之前。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-227">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="4f5f2-228">不過，這種格式是選擇的，因為它會在一開始保留所有固定大小的元素，以簡化剖析器的作業。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-228">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="4f5f2-229">有了這種資料格式，就可以使用一次傳遞解密，雖然實施者會匯呼叫 GetHashAndReset，並在呼叫 System.security.cryptography.icryptotransform.transformfinalblock 之前驗證結果。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-229">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="4f5f2-230">如果串流加密很重要，則可能需要不同的 AE 模式。</span><span class="sxs-lookup"><span data-stu-id="4f5f2-230">If streaming encryption is important, then a different AE mode may be required.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4f5f2-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f5f2-231">See also</span></span>

- [<span data-ttu-id="4f5f2-232">密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="4f5f2-232">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="4f5f2-233">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="4f5f2-233">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="4f5f2-234">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="4f5f2-234">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="4f5f2-235">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="4f5f2-235">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
