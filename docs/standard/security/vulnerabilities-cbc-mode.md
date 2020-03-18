---
title: CBC 解密漏洞
description: 瞭解如何使用填充使用密碼塊鏈 （CBC） 模式對稱解密來檢測和緩解計時漏洞。
ms.date: 06/12/2018
author: blowdart
ms.openlocfilehash: 47520ea4c9c7d0ef4d79378c93c6ce1f2ba7dd6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186089"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="70f34-103">使用填補進行 CBC 模式對稱解密的時間弱點</span><span class="sxs-lookup"><span data-stu-id="70f34-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="70f34-104">Microsoft 認為，在應用可驗證填充時，無需首先確保密文的完整性（非常具體的除外），則不再安全地解密使用密碼-塊鏈 （CBC） 對稱加密模式加密的資料情況 下。</span><span class="sxs-lookup"><span data-stu-id="70f34-104">Microsoft believes that it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext, except for very specific circumstances.</span></span> <span data-ttu-id="70f34-105">這一判斷基於目前已知的加密研究。</span><span class="sxs-lookup"><span data-stu-id="70f34-105">This judgement is based on currently known cryptographic research.</span></span>

## <a name="introduction"></a><span data-ttu-id="70f34-106">簡介</span><span class="sxs-lookup"><span data-stu-id="70f34-106">Introduction</span></span>

<span data-ttu-id="70f34-107">填充 oracle 攻擊是一種針對加密資料的攻擊類型，允許攻擊者在不知道金鑰的情況下解密資料的內容。</span><span class="sxs-lookup"><span data-stu-id="70f34-107">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="70f34-108">oracle 是指"告訴"，它向攻擊者提供有關他們執行的操作是否正確的資訊。</span><span class="sxs-lookup"><span data-stu-id="70f34-108">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="70f34-109">想像一下，和孩子玩棋盤或紙牌遊戲。</span><span class="sxs-lookup"><span data-stu-id="70f34-109">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="70f34-110">當他們的臉上露出燦爛的笑容，因為他們認為自己要做出一個不錯的動作，那是一個神仙。</span><span class="sxs-lookup"><span data-stu-id="70f34-110">When their face lights up with a big smile because they think they're about to make a good move, that's an oracle.</span></span> <span data-ttu-id="70f34-111">作為對手，您可以使用此預言來適當地規劃您的下一步行動。</span><span class="sxs-lookup"><span data-stu-id="70f34-111">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="70f34-112">填充是一個特定的加密術語。</span><span class="sxs-lookup"><span data-stu-id="70f34-112">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="70f34-113">某些密碼（即用於加密資料的演算法）處理資料塊，其中每個資料塊的大小都是固定大小的。</span><span class="sxs-lookup"><span data-stu-id="70f34-113">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="70f34-114">如果要加密的資料的大小不是填充資料塊的正確大小，則將填充資料，直到資料填充為止。</span><span class="sxs-lookup"><span data-stu-id="70f34-114">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="70f34-115">許多形式的填充要求填充始終存在，即使原始輸入的大小正確。</span><span class="sxs-lookup"><span data-stu-id="70f34-115">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="70f34-116">這允許在解密時始終安全地刪除填充。</span><span class="sxs-lookup"><span data-stu-id="70f34-116">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="70f34-117">將兩件事情放在一起，帶有填充 oracle 的軟體實現會顯示解密資料是否具有有效的填充。</span><span class="sxs-lookup"><span data-stu-id="70f34-117">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="70f34-118">oracle 可以非常簡單，例如返回顯示"無效填充"的值，或者返回更複雜的值，例如花一個可衡量的不同時間來處理有效的塊而不是無效塊。</span><span class="sxs-lookup"><span data-stu-id="70f34-118">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="70f34-119">基於塊的密碼具有另一個屬性，稱為模式，它確定第一個塊中的資料與第二個塊中的資料的關係，等等。</span><span class="sxs-lookup"><span data-stu-id="70f34-119">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="70f34-120">最常用的模式之一是 CBC。</span><span class="sxs-lookup"><span data-stu-id="70f34-120">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="70f34-121">CBC 引入了一個初始隨機塊，稱為初始化向量 （IV），並將前一個塊與靜態加密的結果相結合，使其使用相同的金鑰加密同一消息並不總是產生相同的加密輸出。</span><span class="sxs-lookup"><span data-stu-id="70f34-121">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="70f34-122">攻擊者可以使用填充 oracle，結合 CBC 資料的結構化方式，向公開 oracle 的代碼發送稍微更改的消息，並持續發送資料，直到 oracle 告訴他們資料正確為止。</span><span class="sxs-lookup"><span data-stu-id="70f34-122">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="70f34-123">通過此回應，攻擊者可以解密消息位元組位元組。</span><span class="sxs-lookup"><span data-stu-id="70f34-123">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="70f34-124">現代電腦網路的品質非常之高，攻擊者可以檢測到遠端系統上的極小（小於 0.1 ms）的執行時間差異。</span><span class="sxs-lookup"><span data-stu-id="70f34-124">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span><span data-ttu-id="70f34-125">假定成功解密的應用程式只有在資料未被篡改時才能發生，但訪問時，很容易受到旨在觀察成功解密和不成功解密差異的工具的攻擊。</span><span class="sxs-lookup"><span data-stu-id="70f34-125"> Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="70f34-126">雖然在某些語言或庫中，這種時間差異可能比其他語言或庫更重要，但現在人們認為，如果考慮到應用程式對失敗的回應，這對所有語言和庫都是實際威脅。</span><span class="sxs-lookup"><span data-stu-id="70f34-126">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="70f34-127">此攻擊依賴于更改加密資料並與 oracle 測試結果的能力。</span><span class="sxs-lookup"><span data-stu-id="70f34-127">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="70f34-128">完全緩解攻擊的唯一方法是檢測加密資料的更改，並拒絕對加密資料執行任何操作。</span><span class="sxs-lookup"><span data-stu-id="70f34-128">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="70f34-129">執行此操作的標準方法是為數據創建簽名，並在執行任何操作之前驗證該簽名。</span><span class="sxs-lookup"><span data-stu-id="70f34-129">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="70f34-130">簽名必須是可驗證的，攻擊者無法創建簽名，否則它們會更改加密資料，然後根據更改的資料計算新簽名。</span><span class="sxs-lookup"><span data-stu-id="70f34-130">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="70f34-131">一種常見類型的適當簽名稱為金鑰雜湊消息身份驗證代碼 （HMAC）。</span><span class="sxs-lookup"><span data-stu-id="70f34-131">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="70f34-132">HMAC 與校驗和不同，因為它需要一個金鑰，只有生成 HMAC 的人員和驗證者知道。</span><span class="sxs-lookup"><span data-stu-id="70f34-132">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="70f34-133">如果沒有金鑰，您就無法生成正確的 HMAC。</span><span class="sxs-lookup"><span data-stu-id="70f34-133">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="70f34-134">收到資料時，您將獲取加密資料，使用您和寄件者共用的金鑰獨立計算 HMAC，然後將他們發送的 HMAC 與您計算的 HMAC 進行比較。</span><span class="sxs-lookup"><span data-stu-id="70f34-134">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="70f34-135">此比較必須是恒定的時間，否則您添加了另一個可檢測的 oracle，允許不同類型的攻擊。</span><span class="sxs-lookup"><span data-stu-id="70f34-135">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="70f34-136">總之，要安全地使用填充的 CBC 塊密碼，您必須將它們與 HMAC（或其他資料完整性檢查）相結合，在嘗試解密資料之前，使用恒定的時間比較進行驗證。</span><span class="sxs-lookup"><span data-stu-id="70f34-136">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="70f34-137">由於所有更改的消息都花費相同的時間生成回應，因此可防止攻擊。</span><span class="sxs-lookup"><span data-stu-id="70f34-137">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="70f34-138">誰是脆弱的</span><span class="sxs-lookup"><span data-stu-id="70f34-138">Who is vulnerable</span></span>

<span data-ttu-id="70f34-139">此漏洞適用于執行自己的加密和解密的託管和本機應用程式。</span><span class="sxs-lookup"><span data-stu-id="70f34-139">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="70f34-140">這包括：例如：</span><span class="sxs-lookup"><span data-stu-id="70f34-140">This includes, for example:</span></span>

- <span data-ttu-id="70f34-141">加密 Cookie 以在伺服器上稍後解密的應用程式。</span><span class="sxs-lookup"><span data-stu-id="70f34-141">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="70f34-142">一種資料庫應用程式，它為使用者提供將資料插入到稍後解密列的表中的功能。</span><span class="sxs-lookup"><span data-stu-id="70f34-142">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="70f34-143">一種資料傳輸應用程式，它使用共用金鑰進行加密來保護傳輸中的資料。</span><span class="sxs-lookup"><span data-stu-id="70f34-143">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="70f34-144">加密和解密"內部"TLS 隧道中的消息的應用程式。</span><span class="sxs-lookup"><span data-stu-id="70f34-144">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="70f34-145">請注意，在這些情況下，單獨使用 TLS 可能無法保護您。</span><span class="sxs-lookup"><span data-stu-id="70f34-145">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="70f34-146">易受攻擊的應用程式：</span><span class="sxs-lookup"><span data-stu-id="70f34-146">A vulnerable application:</span></span>

- <span data-ttu-id="70f34-147">使用具有可驗證填充模式的 CBC 密碼模式（如 PKCS_7 或 ANSI X.923）解密資料。</span><span class="sxs-lookup"><span data-stu-id="70f34-147">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="70f34-148">無需執行資料完整性檢查（通過 MAC 或非對稱數位簽章）即可執行解密。</span><span class="sxs-lookup"><span data-stu-id="70f34-148">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="70f34-149">這也適用于在這些基元之上構建的抽象之上的應用程式，例如加密消息語法 （PKCS_7/CMS） 包絡資料結構。</span><span class="sxs-lookup"><span data-stu-id="70f34-149">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="70f34-150">相關關注領域</span><span class="sxs-lookup"><span data-stu-id="70f34-150">Related areas of concern</span></span>

<span data-ttu-id="70f34-151">研究導致 Microsoft 進一步關注在消息具有眾所周知或可預測的頁腳結構時，使用 ISO 10126 等效填充填充的 CBC 消息。</span><span class="sxs-lookup"><span data-stu-id="70f34-151">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="70f34-152">例如，根據 W3C XML 加密語法和處理建議（xmlenc，加密Xml）的規則準備的內容。</span><span class="sxs-lookup"><span data-stu-id="70f34-152">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="70f34-153">雖然 W3C 在此時對消息進行簽名然後加密被認為是適當的，但 Microsoft 現在建議始終執行加密然後簽名。</span><span class="sxs-lookup"><span data-stu-id="70f34-153">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="70f34-154">應用程式開發人員應始終注意驗證非對稱簽名金鑰的適用性，因為非對稱金鑰和任意消息之間沒有固有的信任關係。</span><span class="sxs-lookup"><span data-stu-id="70f34-154">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="70f34-155">詳細資料</span><span class="sxs-lookup"><span data-stu-id="70f34-155">Details</span></span>

<span data-ttu-id="70f34-156">從歷史上看，人們一致認為，使用 HMAC 或 RSA 簽名等手段對重要資料進行加密和身份驗證非常重要。</span><span class="sxs-lookup"><span data-stu-id="70f34-156">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="70f34-157">但是，對於如何對加密和身份驗證操作進行排序，沒有明確的指導。</span><span class="sxs-lookup"><span data-stu-id="70f34-157">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="70f34-158">由於本文中詳述的漏洞，Microsoft 的指南現在始終使用"加密然後符號"範例。</span><span class="sxs-lookup"><span data-stu-id="70f34-158">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="70f34-159">也就是說，首先使用對稱金鑰加密資料，然後通過密文（加密資料）計算 MAC 或非對稱簽名。</span><span class="sxs-lookup"><span data-stu-id="70f34-159">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="70f34-160">解密資料時，執行相反。</span><span class="sxs-lookup"><span data-stu-id="70f34-160">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="70f34-161">首先，確認 MAC 或密碼文本的簽名，然後解密它。</span><span class="sxs-lookup"><span data-stu-id="70f34-161">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="70f34-162">已知存在一類稱為"填充 oracle 攻擊"的漏洞已有 10 多年的歷史。</span><span class="sxs-lookup"><span data-stu-id="70f34-162">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="70f34-163">這些漏洞允許攻擊者使用不超過 4096 次嘗試來解密通過對稱塊演算法（如 AES 和 3DES）加密的資料。</span><span class="sxs-lookup"><span data-stu-id="70f34-163">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="70f34-164">這些漏洞利用了阻止密碼在末尾最常用與可驗證填充資料一起使用這一事實。</span><span class="sxs-lookup"><span data-stu-id="70f34-164">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="70f34-165">結果發現，如果攻擊者可以篡改密文，並找出篡改是否導致末尾填充格式的錯誤，攻擊者可以解密資料。</span><span class="sxs-lookup"><span data-stu-id="70f34-165">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="70f34-166">最初，實際攻擊基於基於填充是否有效的服務返回不同的錯誤代碼，例如ASP.NET漏洞[MS10-070](/security-updates/SecurityBulletins/2010/ms10-070)。</span><span class="sxs-lookup"><span data-stu-id="70f34-166">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span></span> <span data-ttu-id="70f34-167">但是，Microsoft 現在認為，僅使用處理有效填充和無效填充之間的時間差異進行類似的攻擊是切實可行的。</span><span class="sxs-lookup"><span data-stu-id="70f34-167">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="70f34-168">如果加密方案使用簽名，並且簽名驗證是在給定資料長度（無論內容如何）使用固定運行時執行的，則可以驗證資料完整性，而無需通過[側通道](https://en.wikipedia.org/wiki/Side-channel_attack)向攻擊者發出任何資訊。</span><span class="sxs-lookup"><span data-stu-id="70f34-168">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="70f34-169">由於完整性檢查拒絕任何篡改的消息，因此填充 oracle 威脅得到緩解。</span><span class="sxs-lookup"><span data-stu-id="70f34-169">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="70f34-170">指引</span><span class="sxs-lookup"><span data-stu-id="70f34-170">Guidance</span></span>

<span data-ttu-id="70f34-171">首先，Microsoft 建議通過傳輸層安全 （TLS） 傳輸任何需要保密的資料，這是安全通訊端層 （SSL） 的繼承者。</span><span class="sxs-lookup"><span data-stu-id="70f34-171">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="70f34-172">接下來，分析您的應用程式，以便：</span><span class="sxs-lookup"><span data-stu-id="70f34-172">Next, analyze your application to:</span></span>

- <span data-ttu-id="70f34-173">準確瞭解您正在執行的加密功能以及正在使用的平臺和 API 提供的加密。</span><span class="sxs-lookup"><span data-stu-id="70f34-173">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="70f34-174">確保在 CBC 模式下，對稱[塊密碼演算法](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)（如 AES 和 3DES）每一層的每個用法都包含使用金鑰鍵資料完整性檢查（非對稱簽名、HMAC，或將密碼模式更改為[經過身份驗證的加密](https://en.wikipedia.org/wiki/Authenticated_encryption)（AE） 模式（如 GCM 或 CCM）。</span><span class="sxs-lookup"><span data-stu-id="70f34-174">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="70f34-175">根據目前的研究，人們普遍認為，當針對非 AE 加密模式獨立執行身份驗證和加密步驟時，對密碼文本（加密然後簽名）進行身份驗證是最好的常規選項。</span><span class="sxs-lookup"><span data-stu-id="70f34-175">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="70f34-176">但是，對於加密學，沒有一刀切的正確答案，這種概括不如專業密碼學家的定向建議。</span><span class="sxs-lookup"><span data-stu-id="70f34-176">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="70f34-177">鼓勵無法更改其消息傳遞格式但執行未經身份驗證的 CBC 解密的應用程式嘗試合併緩解措施，例如：</span><span class="sxs-lookup"><span data-stu-id="70f34-177">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="70f34-178">解密，不允許解密器驗證或刪除填充：</span><span class="sxs-lookup"><span data-stu-id="70f34-178">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="70f34-179">應用的任何填充仍需要刪除或忽略，您將負擔轉移到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="70f34-179">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="70f34-180">好處是填充驗證和刪除可以合併到其他應用程式資料驗證邏輯中。</span><span class="sxs-lookup"><span data-stu-id="70f34-180">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="70f34-181">如果填充驗證和資料驗證可以持續完成，威脅就會減少。</span><span class="sxs-lookup"><span data-stu-id="70f34-181">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="70f34-182">由於填充的解釋會更改感知到的消息長度，因此此方法可能仍發出計時資訊。</span><span class="sxs-lookup"><span data-stu-id="70f34-182">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="70f34-183">將解密填充模式更改為 ISO10126：</span><span class="sxs-lookup"><span data-stu-id="70f34-183">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="70f34-184">ISO10126 解密填充與 PKCS7 加密填充和 ANSIX923 加密填充相容。</span><span class="sxs-lookup"><span data-stu-id="70f34-184">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="70f34-185">更改模式可將填充 oracle 知識減少到 1 個位元組，而不是整個塊。</span><span class="sxs-lookup"><span data-stu-id="70f34-185">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="70f34-186">但是，如果內容具有眾所周知的腳法（如關閉的 XML 元素），則相關攻擊可以繼續攻擊消息的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="70f34-186">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="70f34-187">這也不能阻止純文字恢復，在這種情況下，攻擊者可以強制相同的純文字加密多次使用不同的消息偏移。</span><span class="sxs-lookup"><span data-stu-id="70f34-187">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="70f34-188">對解密調用的評估以抑制計時信號：</span><span class="sxs-lookup"><span data-stu-id="70f34-188">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="70f34-189">對於包含填充的任何資料段，保持時間的計算必須至少超過解密操作所花費的最大時間。</span><span class="sxs-lookup"><span data-stu-id="70f34-189">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="70f34-190">時間計算應按照[獲取高解析度時間戳記](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)的指南進行，而不是通過使用<xref:System.Environment.TickCount?displayProperty=nameWithType>（受滾動/溢出）或減去兩個系統時間戳記（受 NTP 調整錯誤約束）。</span><span class="sxs-lookup"><span data-stu-id="70f34-190">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="70f34-191">時間計算必須包括解密操作，包括託管或C++應用程式中的所有潛在異常，而不僅僅是填充到末尾。</span><span class="sxs-lookup"><span data-stu-id="70f34-191">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="70f34-192">如果成功或失敗尚未確定，則時序門需要在故障過期時返回故障。</span><span class="sxs-lookup"><span data-stu-id="70f34-192">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="70f34-193">執行未經身份驗證解密的服務應具有監視位置，以檢測大量"無效"消息已通過。</span><span class="sxs-lookup"><span data-stu-id="70f34-193">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="70f34-194">請記住，此信號同時包含誤報（合法損壞的資料）和假負數（在足夠長的時間內展開攻擊以逃避檢測）。</span><span class="sxs-lookup"><span data-stu-id="70f34-194">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="70f34-195">查找易受攻擊的代碼 - 本機應用程式</span><span class="sxs-lookup"><span data-stu-id="70f34-195">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="70f34-196">對於根據 Windows 加密功能構建的程式：下一代 （CNG） 庫：</span><span class="sxs-lookup"><span data-stu-id="70f34-196">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="70f34-197">解密調用是到[BCrypt解密](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt)，指定標誌`BCRYPT_BLOCK_PADDING`。</span><span class="sxs-lookup"><span data-stu-id="70f34-197">The decryption call is to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="70f34-198">通過調用[BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty)並BCRYPT_CHAINING_MODE[設置為](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE)`BCRYPT_CHAIN_MODE_CBC`，已初始化金鑰控制碼。</span><span class="sxs-lookup"><span data-stu-id="70f34-198">The key handle has been initialized by calling [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) with [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="70f34-199">由於`BCRYPT_CHAIN_MODE_CBC`預設值為，受影響的代碼可能未為`BCRYPT_CHAINING_MODE`分配任何值。</span><span class="sxs-lookup"><span data-stu-id="70f34-199">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="70f34-200">對於根據較舊的 Windows 加密 API 構建的程式：</span><span class="sxs-lookup"><span data-stu-id="70f34-200">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="70f34-201">解密調用是使用[Crypt 解密](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt)`Final=TRUE`。</span><span class="sxs-lookup"><span data-stu-id="70f34-201">The decryption call is to [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) with `Final=TRUE`.</span></span>
- <span data-ttu-id="70f34-202">通過調用[CryptSetKeyParam，](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam)將[KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam)設置為`CRYPT_MODE_CBC`，從而初始化了金鑰控制碼。</span><span class="sxs-lookup"><span data-stu-id="70f34-202">The key handle has been initialized by calling [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) with [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="70f34-203">由於`CRYPT_MODE_CBC`預設值為，受影響的代碼可能未為`KP_MODE`分配任何值。</span><span class="sxs-lookup"><span data-stu-id="70f34-203">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="70f34-204">查找易受攻擊的代碼 - 託管應用程式</span><span class="sxs-lookup"><span data-stu-id="70f34-204">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="70f34-205">解密調用是 或<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor>上 上的<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])><xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>或 上的 方法。</span><span class="sxs-lookup"><span data-stu-id="70f34-205">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="70f34-206">這包括 .NET 中的以下派生類型，但也可能包括協力廠商類型：</span><span class="sxs-lookup"><span data-stu-id="70f34-206">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="70f34-207">屬性<xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>設置為<xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>或<xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>。 <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="70f34-207">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="70f34-208">由於<xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>預設為，受影響的代碼可能從未分配過該<xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="70f34-208">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="70f34-209">屬性<xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>設置為<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="70f34-209">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="70f34-210">由於<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>預設為，受影響的代碼可能從未分配過該<xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="70f34-210">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="70f34-211">查找易受攻擊的代碼 - 加密消息語法</span><span class="sxs-lookup"><span data-stu-id="70f34-211">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="70f34-212">未經身份驗證的 CMS EnvelopedData 消息，其加密內容使用 AES 的 CBC 模式 （2.16.840.1.1.101.3.4.1.2， 2.16.840.1.1.1.3.4.1.22， 2.16.840.1.101.3.4.1.42）、DES （1.3.14.3.2.7）、3DES（1.2.840.113549.3.7）或 RC2 （1.2.840.113549.3.2）易受攻擊，以及在 CBC 模式下使用任何其他塊密碼演算法的消息。</span><span class="sxs-lookup"><span data-stu-id="70f34-212">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="70f34-213">雖然流密碼不受此特定漏洞的影響，但 Microsoft 建議始終通過檢查 Content加密演算法值來驗證資料。</span><span class="sxs-lookup"><span data-stu-id="70f34-213">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="70f34-214">對於託管應用程式，可以將 CMS EnvelopedData blob 檢測為傳遞給<xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>的任何值。</span><span class="sxs-lookup"><span data-stu-id="70f34-214">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="70f34-215">對於本機應用程式，CMS EnvelopedData blob 可以檢測為通過[CryptMgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate)提供給 CMS 控制碼的任何[CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam)值，`CMSG_ENVELOPED`其生成的CMSG_TYPE_PARAM是和/或 CMS`CMSG_CTRL_DECRYPT`控制碼，稍後通過[CryptMgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol)發送指令。</span><span class="sxs-lookup"><span data-stu-id="70f34-215">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) whose resulting [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="70f34-216">易受攻擊的代碼示例 - 託管</span><span class="sxs-lookup"><span data-stu-id="70f34-216">Vulnerable code example - managed</span></span>

<span data-ttu-id="70f34-217">此方法讀取 Cookie 並對其進行解密，並且資料完整性檢查不可見。</span><span class="sxs-lookup"><span data-stu-id="70f34-217">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="70f34-218">因此，此方法讀取的 Cookie 的內容可能會由接收該 Cookie 的使用者或任何獲得加密 Cookie 值的攻擊者攻擊。</span><span class="sxs-lookup"><span data-stu-id="70f34-218">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="70f34-219">建議的做法示例代碼 - 託管</span><span class="sxs-lookup"><span data-stu-id="70f34-219">Example code following recommended practices - managed</span></span>

<span data-ttu-id="70f34-220">以下示例代碼使用非標準消息格式</span><span class="sxs-lookup"><span data-stu-id="70f34-220">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="70f34-221">其中`cipher_algorithm_id`和`hmac_algorithm_id`演算法識別碼是這些演算法的應用程式本地（非標準）表示形式。</span><span class="sxs-lookup"><span data-stu-id="70f34-221">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="70f34-222">這些識別碼在現有消息傳遞協定的其他部分可能有意義，而不是作為裸聯位元組流。</span><span class="sxs-lookup"><span data-stu-id="70f34-222">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="70f34-223">此示例還使用單個主金鑰派生加密金鑰和 HMAC 金鑰。</span><span class="sxs-lookup"><span data-stu-id="70f34-223">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="70f34-224">這既便於將單鍵應用程式轉換為雙鍵應用程式，又鼓勵將兩個鍵保留為不同的值。</span><span class="sxs-lookup"><span data-stu-id="70f34-224">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="70f34-225">它還保證 HMAC 金鑰和加密金鑰不能出同步。</span><span class="sxs-lookup"><span data-stu-id="70f34-225">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="70f34-226">此示例不接受加密或解密的<xref:System.IO.Stream>。</span><span class="sxs-lookup"><span data-stu-id="70f34-226">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="70f34-227">當前資料格式使單路加密變得困難，`hmac_tag`因為值位於密文之前。</span><span class="sxs-lookup"><span data-stu-id="70f34-227">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="70f34-228">但是，之所以選擇此格式，是因為它使所有固定大小的元素在開始時保持簡單。</span><span class="sxs-lookup"><span data-stu-id="70f34-228">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="70f34-229">使用此資料格式，可以進行一次性解密，但被警告實施者在調用 TransformFinalBlock 之前調用 GetHashAndReset 並驗證結果。</span><span class="sxs-lookup"><span data-stu-id="70f34-229">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="70f34-230">如果流加密很重要，則可能需要其他 AE 模式。</span><span class="sxs-lookup"><span data-stu-id="70f34-230">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
