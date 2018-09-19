---
title: 使用 CBC 模式的對稱式解密使用邊框間距的計時弱點
description: 了解如何偵測及降低計時弱點與 Cipher Block Chaining (CBC) 模式對稱式解密使用的填補。
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 6d16b6849bfd4744f1828cda38a537f842243c1d
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288377"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="a6a91-103">使用 CBC 模式的對稱式解密使用邊框間距的計時弱點</span><span class="sxs-lookup"><span data-stu-id="a6a91-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="a6a91-104">Microsoft 認為它是無法再解密資料加密使用對稱式加密 Cipher Block Chaining (CBC) 模式，而不先確保完整性的密碼文字，除了已套用可驗證的填補時的安全非常特定情況。</span><span class="sxs-lookup"><span data-stu-id="a6a91-104">Microsoft believes that it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext, except for very specific circumstances.</span></span> <span data-ttu-id="a6a91-105">此判斷是以目前已知的密碼編譯研究為基礎。</span><span class="sxs-lookup"><span data-stu-id="a6a91-105">This judgement is based on currently known cryptographic research.</span></span> 

## <a name="introduction"></a><span data-ttu-id="a6a91-106">簡介</span><span class="sxs-lookup"><span data-stu-id="a6a91-106">Introduction</span></span>

<span data-ttu-id="a6a91-107">填補 oracle 攻擊是一種攻擊可讓攻擊者來解密資料，而不需要知道金鑰的加密資料。</span><span class="sxs-lookup"><span data-stu-id="a6a91-107">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="a6a91-108">Oracle 指的是 「 告訴 」 讓它們執行的動作是否為正確的攻擊者資訊。</span><span class="sxs-lookup"><span data-stu-id="a6a91-108">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="a6a91-109">想像一下播放面板或卡片具有子系的遊戲。</span><span class="sxs-lookup"><span data-stu-id="a6a91-109">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="a6a91-110">當她臉部會點亮並以巨量的笑臉替因為她認為她是即將進行的良好移動，是一種 oracle。</span><span class="sxs-lookup"><span data-stu-id="a6a91-110">When her face lights up with a big smile because she thinks she's about to make a good move, that's an oracle.</span></span> <span data-ttu-id="a6a91-111">為對手，可以使用此 oracle 適當地規劃下一步的移動。</span><span class="sxs-lookup"><span data-stu-id="a6a91-111">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="a6a91-112">填補為特定的密碼編譯期間。</span><span class="sxs-lookup"><span data-stu-id="a6a91-112">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="a6a91-113">某些編碼器，也就是用來加密資料的演算法，適用於其中每個區塊的大小是固定的資料區塊。</span><span class="sxs-lookup"><span data-stu-id="a6a91-113">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="a6a91-114">如果您想要加密的資料不正確的大小以填滿的區塊，直到它會填補資料。</span><span class="sxs-lookup"><span data-stu-id="a6a91-114">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="a6a91-115">許多形式的邊框距離要求一律必須存在，即使已正確大小的原始輸入該邊框距離。</span><span class="sxs-lookup"><span data-stu-id="a6a91-115">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="a6a91-116">這可讓一律可以安全地移除時解密的填補。</span><span class="sxs-lookup"><span data-stu-id="a6a91-116">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="a6a91-117">將兩個項目放在一起，與邊框距離 oracle 軟體實作，顯示解密的資料是否具有有效的填補。</span><span class="sxs-lookup"><span data-stu-id="a6a91-117">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="a6a91-118">傳回值，指出 「 無效的邊框距離 」 簡單或更複雜，例如處理而不是無效的區塊是有效區塊的具體不同時間，可能是 oracle。</span><span class="sxs-lookup"><span data-stu-id="a6a91-118">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="a6a91-119">區塊編碼器會有另一個屬性，稱為模式，用來決定第一個區塊的第二個區塊中的資料中的資料關聯性，等等。</span><span class="sxs-lookup"><span data-stu-id="a6a91-119">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="a6a91-120">其中一個最常使用的模式是 CBC。</span><span class="sxs-lookup"><span data-stu-id="a6a91-120">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="a6a91-121">CBC 引進初始的隨機區塊，已知為初始化向量 (IV)，並結合的靜態加密，以方便，使用相同的金鑰加密相同的訊息不一定會產生相同加密的輸出結果中的前一個區塊。</span><span class="sxs-lookup"><span data-stu-id="a6a91-121">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="a6a91-122">攻擊者可以使用填補 oracle，搭配 CBC 資料結構的方式，將稍有變更的訊息傳送至 oracle，公開 （expose） 的程式碼，並持續傳送資料，直到 oracle 告訴他們的資料正確。</span><span class="sxs-lookup"><span data-stu-id="a6a91-122">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="a6a91-123">從這個回應，攻擊者可以解密逐位元組的訊息。</span><span class="sxs-lookup"><span data-stu-id="a6a91-123">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="a6a91-124">現代電腦網路都屬於這類高品質攻擊者可以偵測很小 （小於 0.1 毫秒） 在遠端系統上執行的差異時間。</span><span class="sxs-lookup"><span data-stu-id="a6a91-124">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span> <span data-ttu-id="a6a91-125">假設資料未曾遭到竄改時，可以只會發生成功解密的應用程式可能容易遭受攻擊的工具，專為觀察在成功和失敗的解密的差異。</span><span class="sxs-lookup"><span data-stu-id="a6a91-125">Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="a6a91-126">雖然這項時間差異可能是在某些語言或程式庫比其他更重要的現在認為這是實際服務威脅中的所有語言和程式庫，當失敗的應用程式的回應會納入考量。</span><span class="sxs-lookup"><span data-stu-id="a6a91-126">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="a6a91-127">這種攻擊會依賴變更加密的資料和測試結果與 oracle 的能力。</span><span class="sxs-lookup"><span data-stu-id="a6a91-127">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="a6a91-128">完全緩和攻擊的唯一方法是偵測加密資料的變更，並拒絕在其上執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="a6a91-128">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="a6a91-129">若要這樣做的標準方式是建立資料的簽章，並執行任何作業之前，請驗證該簽章。</span><span class="sxs-lookup"><span data-stu-id="a6a91-129">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="a6a91-130">簽章必須可供驗證，攻擊者無法加以建立，否則它們就可以變更加密的資料，然後計算新的簽章已變更的資料為基礎。</span><span class="sxs-lookup"><span data-stu-id="a6a91-130">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="a6a91-131">一個常見的適當簽章的類型稱為金鑰式雜湊訊息驗證碼 (HMAC)。</span><span class="sxs-lookup"><span data-stu-id="a6a91-131">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="a6a91-132">HMAC 與總和檢查碼不同，在於它會使用祕密金鑰，已知只產生 HMAC 的人員，並確認它的人員。</span><span class="sxs-lookup"><span data-stu-id="a6a91-132">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="a6a91-133">而不需要擁有金鑰，您無法產生正確的 HMAC。</span><span class="sxs-lookup"><span data-stu-id="a6a91-133">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="a6a91-134">當您收到您的資料時，您會需要加密的資料，獨立計算 HMAC 使用祕密金鑰，您寄件者共用，然後它們傳送給其中一個您 HMAC 計算的比較。</span><span class="sxs-lookup"><span data-stu-id="a6a91-134">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="a6a91-135">這項比較必須是固定的時間，否則您已新增另一個偵測到 oracle，可讓不同類型的攻擊。</span><span class="sxs-lookup"><span data-stu-id="a6a91-135">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="a6a91-136">總而言之，使用填補 CBC 區塊加密方式安全地，您必須將它們合併 HMAC （或其他資料完整性檢查） 進行驗證再試一次使用固定時間的比較，來解密資料。</span><span class="sxs-lookup"><span data-stu-id="a6a91-136">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="a6a91-137">由於所有變更的訊息需要產生回應的相同時間量，防止攻擊。</span><span class="sxs-lookup"><span data-stu-id="a6a91-137">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="a6a91-138">易受攻擊是誰</span><span class="sxs-lookup"><span data-stu-id="a6a91-138">Who is vulnerable</span></span>

<span data-ttu-id="a6a91-139">這項弱點適用於 managed 和原生應用程式會執行自己的加密和解密。</span><span class="sxs-lookup"><span data-stu-id="a6a91-139">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="a6a91-140">這包括，例如：</span><span class="sxs-lookup"><span data-stu-id="a6a91-140">This includes, for example:</span></span>

- <span data-ttu-id="a6a91-141">應用程式來加密伺服器上的更新版本解密 cookie。</span><span class="sxs-lookup"><span data-stu-id="a6a91-141">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="a6a91-142">提供可讓使用者將資料插入資料表的資料行的資料庫應用程式會稍後會進行解密。</span><span class="sxs-lookup"><span data-stu-id="a6a91-142">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="a6a91-143">使用共用的金鑰來保護傳輸中的資料加密所依賴的應用程式的資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="a6a91-143">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="a6a91-144">應用程式來加密及解密 「 內部 」 TLS 通道的訊息。</span><span class="sxs-lookup"><span data-stu-id="a6a91-144">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="a6a91-145">請注意，使用 TLS 本身可能不保護您在這些情況下。</span><span class="sxs-lookup"><span data-stu-id="a6a91-145">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="a6a91-146">易受攻擊的應用程式：</span><span class="sxs-lookup"><span data-stu-id="a6a91-146">A vulnerable application:</span></span>

- <span data-ttu-id="a6a91-147">使用 CBC 加密模式，可驗證的填補模式，例如 PKCS #7 或 ANSI X.923 解密資料。</span><span class="sxs-lookup"><span data-stu-id="a6a91-147">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="a6a91-148">執行解密，而不需要執行資料完整性檢查 （透過在 MAC 或非對稱的數位簽章）。</span><span class="sxs-lookup"><span data-stu-id="a6a91-148">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="a6a91-149">這也適用於應用程式之上，請在下列基本類型，例如密碼編譯訊息語法 (PKCS #7/CMS) EnvelopedData 結構為基礎的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="a6a91-149">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="a6a91-150">相關的關切的區域</span><span class="sxs-lookup"><span data-stu-id="a6a91-150">Related areas of concern</span></span>

<span data-ttu-id="a6a91-151">參考資料造成 Microsoft 進一步考量到會填補填補訊息時的已知或可預測的頁尾結構的 ISO 10126-對等的 CBC 訊息。</span><span class="sxs-lookup"><span data-stu-id="a6a91-151">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="a6a91-152">例如，內容已備妥的 W3C XML 加密語法和處理建議 (xmlenc EncryptedXml) 的規則。</span><span class="sxs-lookup"><span data-stu-id="a6a91-152">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="a6a91-153">雖然 W3C 指導方針，以簽署訊息，然後加密已被視為適當時，Microsoft 現在會建議一律進行加密再簽署。</span><span class="sxs-lookup"><span data-stu-id="a6a91-153">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="a6a91-154">因為沒有任何固有之間的信任關係的非對稱金鑰和任意的訊息，應用程式開發人員應該一律是留意驗證的非對稱簽章金鑰的適用性。</span><span class="sxs-lookup"><span data-stu-id="a6a91-154">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="a6a91-155">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a6a91-155">Details</span></span>

<span data-ttu-id="a6a91-156">在過去，已經很重要，來加密和驗證使用 HMAC 或 RSA 簽章等方式的重要資料的共識。</span><span class="sxs-lookup"><span data-stu-id="a6a91-156">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="a6a91-157">不過，已減少清楚的指引，來選擇要排序的加密和驗證作業。</span><span class="sxs-lookup"><span data-stu-id="a6a91-157">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="a6a91-158">本文章中的弱點，因為 Microsoft 的指引是現在一律使用 「 加密然後-簽署 」 典範。</span><span class="sxs-lookup"><span data-stu-id="a6a91-158">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="a6a91-159">也就是第一次使用對稱金鑰，加密資料，則計算加密文字 （加密的資料） 的 MAC 或非對稱簽章。</span><span class="sxs-lookup"><span data-stu-id="a6a91-159">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="a6a91-160">當解密資料，請執行反向。</span><span class="sxs-lookup"><span data-stu-id="a6a91-160">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="a6a91-161">首先，確認 MAC 或簽章的加密文字，然後將它解密。</span><span class="sxs-lookup"><span data-stu-id="a6a91-161">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="a6a91-162">稱為 「 填補 oracle 攻擊 」 存在超過 10 年已知的弱點類別。</span><span class="sxs-lookup"><span data-stu-id="a6a91-162">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="a6a91-163">這些弱點會允許攻擊者使用來解密資料加密的對稱區塊的演算法，例如 AES 和 3DES，超過 4096 個嘗試每個資料區塊。</span><span class="sxs-lookup"><span data-stu-id="a6a91-163">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="a6a91-164">進行這些弱點可驗證的邊框距離結尾的資料最常使用的區塊編碼器的事實使用。</span><span class="sxs-lookup"><span data-stu-id="a6a91-164">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="a6a91-165">它找不到攻擊者可以修改加密文字，並了解是否遭到竄改而造成錯誤的結尾填補格式，是否攻擊者可以解密資料。</span><span class="sxs-lookup"><span data-stu-id="a6a91-165">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="a6a91-166">一開始，會傳回不同的錯誤代碼是否有效，例如 ASP.NET 的弱點可能會填補為基礎的服務以實際的攻擊[MS10 070](https://technet.microsoft.com/library/security/ms10-070.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a6a91-166">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](https://technet.microsoft.com/library/security/ms10-070.aspx).</span></span> <span data-ttu-id="a6a91-167">不過，Microsoft 現在認為它是實際進行類似的攻擊使用只在處理有效和無效的邊框距離之間的時間差異。</span><span class="sxs-lookup"><span data-stu-id="a6a91-167">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="a6a91-168">而不發出任何資訊，提供的加密配置採用簽章和簽章驗證會使用固定的執行階段指定長度的資料 （不論內容中） 執行的可以驗證資料完整性攻擊者透過[側邊通道](https://en.wikipedia.org/wiki/Side-channel_attack)。</span><span class="sxs-lookup"><span data-stu-id="a6a91-168">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="a6a91-169">因為完整性檢查會拒絕遭竄改的任何訊息，以降低填補 oracle 威脅。</span><span class="sxs-lookup"><span data-stu-id="a6a91-169">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="a6a91-170">指引</span><span class="sxs-lookup"><span data-stu-id="a6a91-170">Guidance</span></span>

<span data-ttu-id="a6a91-171">首先，Microsoft 建議透過傳輸層安全性 (TLS)，以安全通訊端層 (SSL) 的後續版本需要傳送任何具有機密性的資料。</span><span class="sxs-lookup"><span data-stu-id="a6a91-171">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="a6a91-172">接下來，分析您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="a6a91-172">Next, analyze your application to:</span></span>

- <span data-ttu-id="a6a91-173">了解精確地將您要執行何種加密，並由平台和您使用的 Api 提供何種加密。</span><span class="sxs-lookup"><span data-stu-id="a6a91-173">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="a6a91-174">可確定每個使用方式，在每一層的對稱[區塊加密演算法](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)，例如 AES 和 3DES，CBC 模式的合併使用的密碼為索引鍵的資料完整性檢查 (非對稱簽章的 HMAC，或若要變更加密模式[驗證加密](https://en.wikipedia.org/wiki/Authenticated_encryption)(AE) 模式，例如 GCM 或 CCM)。</span><span class="sxs-lookup"><span data-stu-id="a6a91-174">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="a6a91-175">以目前研究為基礎，因此一般認為，非 AE 模式，加密的獨立執行的驗證和加密步驟時，驗證加密文字 （加密-然後-簽署） 時，最佳的一般選項。</span><span class="sxs-lookup"><span data-stu-id="a6a91-175">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="a6a91-176">不過，沒有一體適用的正確解答，密碼編譯，而且這個一般化不專業的解碼員從不如導向的建議。</span><span class="sxs-lookup"><span data-stu-id="a6a91-176">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="a6a91-177">無法變更其訊息的格式，但執行未經驗證的 CBC 解密的應用程式，建議嘗試將緩和措施，例如：</span><span class="sxs-lookup"><span data-stu-id="a6a91-177">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="a6a91-178">不允許的解密程式來驗證或移除填補解密：</span><span class="sxs-lookup"><span data-stu-id="a6a91-178">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="a6a91-179">已套用任何填補字元仍必須移除，或略過，您要移動到您的應用程式的負擔。</span><span class="sxs-lookup"><span data-stu-id="a6a91-179">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="a6a91-180">優點是，填補驗證及移除，可以合併到其他應用程式資料的驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="a6a91-180">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="a6a91-181">如果填補驗證及資料驗證可以以常數時間來完成，則會降低潛在威脅。</span><span class="sxs-lookup"><span data-stu-id="a6a91-181">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="a6a91-182">因為填補的解譯變更察覺到的訊息長度，仍可能從這種方法發出的計時資訊。</span><span class="sxs-lookup"><span data-stu-id="a6a91-182">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="a6a91-183">變更 ISO10126 解密的填補模式：</span><span class="sxs-lookup"><span data-stu-id="a6a91-183">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="a6a91-184">ISO10126 解密填補是與 PKCS7 加密填補和 ANSIX923 加密填補相容。</span><span class="sxs-lookup"><span data-stu-id="a6a91-184">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="a6a91-185">將模式變更成 1 個位元組，而不是整個區塊減少填補 oracle 知識。</span><span class="sxs-lookup"><span data-stu-id="a6a91-185">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="a6a91-186">不過，如果內容有已知的頁尾中，例如結尾 XML 項目相關的攻擊可以繼續攻擊其餘的訊息。</span><span class="sxs-lookup"><span data-stu-id="a6a91-186">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="a6a91-187">這也不會阻止在其中，攻擊者可以強制轉型會以不同的訊息位移加密多次相同的純文字的情況下的純文字復原。</span><span class="sxs-lookup"><span data-stu-id="a6a91-187">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="a6a91-188">閘道評估的解密呼叫水輥計時訊號：</span><span class="sxs-lookup"><span data-stu-id="a6a91-188">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="a6a91-189">等候時間的計算必須解密作業會針對包含填補的任何資料 」 區段所需的時間的最大數量超過最小值。</span><span class="sxs-lookup"><span data-stu-id="a6a91-189">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="a6a91-190">時間計算應該根據中的指導方針[取得高解析度的時間戳記](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx)，不是使用<xref:System.Environment.TickCount?displayProperty=nameWithType>（受限於向前復原移轉/溢位） 上或減去兩個系統的時間戳記，（受限於 NTP 調整錯誤）。</span><span class="sxs-lookup"><span data-stu-id="a6a91-190">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="a6a91-191">時間計算必須包括在所有可能的例外狀況解密作業包含管理或 c + + 應用程式，不只是加在尾端填補。</span><span class="sxs-lookup"><span data-stu-id="a6a91-191">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="a6a91-192">如果已尚未決定成功或失敗，計時閘道需要它過期時傳回失敗。</span><span class="sxs-lookup"><span data-stu-id="a6a91-192">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="a6a91-193">監視機制來偵測已通過的 「 無效 」 訊息時，應該執行未經驗證的解密的服務。</span><span class="sxs-lookup"><span data-stu-id="a6a91-193">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="a6a91-194">請記住此訊號會誤肯定 （合法的損毀的資料） 和誤否定 （經過一段夠長的時間來規避偵測攻擊散佈）。</span><span class="sxs-lookup"><span data-stu-id="a6a91-194">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="a6a91-195">尋找易受攻擊的程式碼-原生應用程式</span><span class="sxs-lookup"><span data-stu-id="a6a91-195">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="a6a91-196">建置 Windows 密碼編譯的程式： Next Generation (CNG) 程式庫：</span><span class="sxs-lookup"><span data-stu-id="a6a91-196">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="a6a91-197">解密呼叫是對[BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt)，並指定`BCRYPT_BLOCK_PADDING`旗標。</span><span class="sxs-lookup"><span data-stu-id="a6a91-197">The decryption call is to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="a6a91-198">藉由呼叫已經初始化的金鑰控制代碼[BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty)具有[BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE)設定為`BCRYPT_CHAIN_MODE_CBC`。</span><span class="sxs-lookup"><span data-stu-id="a6a91-198">The key handle has been initialized by calling [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) with [BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="a6a91-199">由於`BCRYPT_CHAIN_MODE_CBC`是預設設定，受影響的程式碼可能未指派任何值`BCRYPT_CHAINING_MODE`。</span><span class="sxs-lookup"><span data-stu-id="a6a91-199">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="a6a91-200">針對較舊的 Windows 密碼編譯 API 建置的程式：</span><span class="sxs-lookup"><span data-stu-id="a6a91-200">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="a6a91-201">解密呼叫是對[CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt)使用`Final=TRUE`。</span><span class="sxs-lookup"><span data-stu-id="a6a91-201">The decryption call is to [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) with `Final=TRUE`.</span></span>
- <span data-ttu-id="a6a91-202">藉由呼叫已經初始化的金鑰控制代碼[CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam)具有[KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE)設定為`CRYPT_MODE_CBC`。</span><span class="sxs-lookup"><span data-stu-id="a6a91-202">The key handle has been initialized by calling [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) with [KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="a6a91-203">由於`CRYPT_MODE_CBC`是預設設定，受影響的程式碼可能未指派任何值`KP_MODE`。</span><span class="sxs-lookup"><span data-stu-id="a6a91-203">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="a6a91-204">尋找受到程式碼-受管理的應用程式</span><span class="sxs-lookup"><span data-stu-id="a6a91-204">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="a6a91-205">解密呼叫是對<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor>或是<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])>上的方法<xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a6a91-205">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="a6a91-206">這包括在.NET 中，下列的衍生型別，但也可能包含協力廠商類型：</span><span class="sxs-lookup"><span data-stu-id="a6a91-206">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
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
- <span data-ttu-id="a6a91-207"><xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>屬性設定為<xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>， <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>，或<xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a6a91-207">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="a6a91-208">由於<xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>是預設設定，受影響的程式碼可能永遠不會指派<xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="a6a91-208">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="a6a91-209"><xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>屬性設定為 <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a6a91-209">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="a6a91-210">由於<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>是預設設定，受影響的程式碼可能永遠不會指派<xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="a6a91-210">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="a6a91-211">尋找易受攻擊的程式碼-密碼編譯訊息語法</span><span class="sxs-lookup"><span data-stu-id="a6a91-211">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="a6a91-212">未驗證的 CMS EnvelopedData 訊息，其加密的內容會使用 CBC 模式的 AES （2.16.840.1.101.3.4.1.2、 2.16.840.1.101.3.4.1.22 2.16.840.1.101.3.4.1.42）、 DES (1.3.14.3.2.7)、 3DES (1.2.840.113549.3.7) 或 RC2 (1.2.840.113549.3.2) 是易受攻擊，以及做為訊息使用 CBC 模式的任何其他的區塊加密演算法。</span><span class="sxs-lookup"><span data-stu-id="a6a91-212">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="a6a91-213">雖然資料流加密不容易受到這項特定弱點，Microsoft 建議一律透過檢查 ContentEncryptionAlgorithm 值進行驗證的資料。</span><span class="sxs-lookup"><span data-stu-id="a6a91-213">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="a6a91-214">對於受管理的應用程式，blob 可以是 CMS EnvelopedData 偵測到任何值，會傳遞至<xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="a6a91-214">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="a6a91-215">原生應用程式，CMS EnvelopedData blob 可以偵測到的 CMS 控點，透過提供任何值[CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate)其產生[CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam)是`CMSG_ENVELOPED`和/或 CMS 控制代碼稍後傳送`CMSG_CTRL_DECRYPT`透過指令[CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol)。</span><span class="sxs-lookup"><span data-stu-id="a6a91-215">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) whose resulting [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="a6a91-216">易受攻擊的程式碼範例-管理</span><span class="sxs-lookup"><span data-stu-id="a6a91-216">Vulnerable code example - managed</span></span>

<span data-ttu-id="a6a91-217">這個方法會讀取 cookie，然後將它解密且可以看見任何資料完整性檢查。</span><span class="sxs-lookup"><span data-stu-id="a6a91-217">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="a6a91-218">因此，使用者已收到，或任何攻擊者取得加密的 cookie 值，這個方法會讀取 cookie 的內容可能會遭受攻擊。</span><span class="sxs-lookup"><span data-stu-id="a6a91-218">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

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

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="a6a91-219">下列範例程式碼建議的作法-管理</span><span class="sxs-lookup"><span data-stu-id="a6a91-219">Example code following recommended practices - managed</span></span>

<span data-ttu-id="a6a91-220">下列範例程式碼會使用非標準的訊息格式</span><span class="sxs-lookup"><span data-stu-id="a6a91-220">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="a6a91-221">何處`cipher_algorithm_id`和`hmac_algorithm_id`演算法識別項是這些演算法的應用程式的本機 （非標準） 的表示法。</span><span class="sxs-lookup"><span data-stu-id="a6a91-221">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="a6a91-222">這些識別碼合理的其他部分，而不是您現有的傳訊通訊協定為裸機串連位元組資料流。</span><span class="sxs-lookup"><span data-stu-id="a6a91-222">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="a6a91-223">此範例也會使用單一的主要金鑰來加密金鑰和 HMAC 金鑰衍生。</span><span class="sxs-lookup"><span data-stu-id="a6a91-223">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="a6a91-224">這被提供兩者都是為了方便起見，開啟單一索引應用程式到雙重為索引鍵的應用程式，並鼓勵保留兩個索引鍵為不同的值。</span><span class="sxs-lookup"><span data-stu-id="a6a91-224">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="a6a91-225">它進一步保證的 HMAC 金鑰和加密金鑰無法取得未執行同步處理。</span><span class="sxs-lookup"><span data-stu-id="a6a91-225">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="a6a91-226">此範例不會接受<xref:System.IO.Stream>加密或解密。</span><span class="sxs-lookup"><span data-stu-id="a6a91-226">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="a6a91-227">目前的資料格式進行一段式加密不容易因為`hmac_tag`值之前加密文字。</span><span class="sxs-lookup"><span data-stu-id="a6a91-227">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="a6a91-228">不過，因為它在最開頭一直到簡單的剖析器會將所有固定大小的項目，已選擇這種格式。</span><span class="sxs-lookup"><span data-stu-id="a6a91-228">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="a6a91-229">此資料格式時，一段式解密是可行的但實作者 cautioned 呼叫 GetHashAndReset 並呼叫 TransformFinalBlock 之前驗證結果。</span><span class="sxs-lookup"><span data-stu-id="a6a91-229">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="a6a91-230">如果資料流加密很重要的不同的 AE 模式可能需要。</span><span class="sxs-lookup"><span data-stu-id="a6a91-230">If streaming encryption is important, then a different AE mode may be required.</span></span>

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
