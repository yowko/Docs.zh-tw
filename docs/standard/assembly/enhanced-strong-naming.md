---
title: 增強的強式命名
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ab1087a840fe41b9fac7779c73797c470899408
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834886"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="517d6-102">增強的強式命名</span><span class="sxs-lookup"><span data-stu-id="517d6-102">Enhanced strong naming</span></span>
<span data-ttu-id="517d6-103">強式名稱簽章是 .NET Framework 中的身分識別機制，用來識別組件。</span><span class="sxs-lookup"><span data-stu-id="517d6-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="517d6-104">它是公開金鑰數位簽章，通常用來驗證從建立者 (簽署者) 傳遞給收件者 (驗證者) 的資料完整性。</span><span class="sxs-lookup"><span data-stu-id="517d6-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="517d6-105">此簽章用來當作組件的唯一身分識別，並可確保對組件的參考不會模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="517d6-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="517d6-106">組件在建置程序的一部分簽署，然後在載入時加以驗證。</span><span class="sxs-lookup"><span data-stu-id="517d6-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="517d6-107">強式名稱簽章可協助防止惡徒竄改組件，然後使用原始簽署者的金鑰重新簽署組件。</span><span class="sxs-lookup"><span data-stu-id="517d6-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="517d6-108">不過，強式名稱金鑰並不包含關於發行者的任何可靠資訊，也不包含憑證階層。</span><span class="sxs-lookup"><span data-stu-id="517d6-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="517d6-109">強式名稱簽章不保證簽署組件之人的可信度，或指出該人是否為金鑰的合法擁有者；它僅指出金鑰的擁有者簽署了該組件。</span><span class="sxs-lookup"><span data-stu-id="517d6-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="517d6-110">因此，我們不建議使用強式名稱簽章作為安全性驗證而來信任協力廠商程式碼。</span><span class="sxs-lookup"><span data-stu-id="517d6-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="517d6-111">Microsoft Authenticode 是驗證程式碼的建議方式。</span><span class="sxs-lookup"><span data-stu-id="517d6-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="517d6-112">傳統強式名稱的限制</span><span class="sxs-lookup"><span data-stu-id="517d6-112">Limitations of conventional strong names</span></span>  
 <span data-ttu-id="517d6-113">在 .NET Framework 4.5 之前版本所使用的強式命名技術有下列缺點：</span><span class="sxs-lookup"><span data-stu-id="517d6-113">The strong naming technology used in versions before the .NET Framework 4.5 has the following shortcomings:</span></span>  
  
- <span data-ttu-id="517d6-114">金鑰經常受到攻擊，改善的技術和硬體能夠更輕鬆從公開金鑰推斷私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="517d6-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="517d6-115">為了防範攻擊，必須使用較大的金鑰。</span><span class="sxs-lookup"><span data-stu-id="517d6-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="517d6-116">在 .NET Framework 4.5 之前的 .NET Framework 版本可讓您以任何大小金鑰 (預設大小為 1024 位元) 來簽署，但使用新金鑰來簽署組件會中斷參考組件較舊身分識別的所有二進位檔。</span><span class="sxs-lookup"><span data-stu-id="517d6-116">.NET Framework versions before the .NET Framework 4.5 provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="517d6-117">因此，如果您想要維護相容性，很難升級簽署金鑰的大小。</span><span class="sxs-lookup"><span data-stu-id="517d6-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
- <span data-ttu-id="517d6-118">強式名稱簽署只支援 SHA-1 演算法。</span><span class="sxs-lookup"><span data-stu-id="517d6-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="517d6-119">最近已發現 SHA-1 不足以應付安全雜湊應用程式。</span><span class="sxs-lookup"><span data-stu-id="517d6-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="517d6-120">因此，必須使用更強的演算法 (SHA-256 或以上)。</span><span class="sxs-lookup"><span data-stu-id="517d6-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="517d6-121">很可能 SHA-1 會失去其與 FIPS 相容的地位，如此對於選擇只使用與 FIPS 相容的軟體和演算法的人會造成問題。</span><span class="sxs-lookup"><span data-stu-id="517d6-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="517d6-122">增強型強式名稱的優點</span><span class="sxs-lookup"><span data-stu-id="517d6-122">Advantages of enhanced strong names</span></span>  
 <span data-ttu-id="517d6-123">增強強式名稱的主要優點是與預先存在的強式名稱相容，以及能夠宣告一個身分識別相當於另一個身分識別：</span><span class="sxs-lookup"><span data-stu-id="517d6-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
- <span data-ttu-id="517d6-124">有預先存在的已簽署組件的開發人員，可以將他們的身分識別移轉至 SHA-2 演算法，同時維持與參考舊身分識別的組件相容性。</span><span class="sxs-lookup"><span data-stu-id="517d6-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
- <span data-ttu-id="517d6-125">建立新組件而且不在意預先存在的強式名稱簽章的開發人員，可以使用更安全的 SHA-2 演算法，並如往常般簽署組件。</span><span class="sxs-lookup"><span data-stu-id="517d6-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="use-enhanced-strong-names"></a><span data-ttu-id="517d6-126">使用增強的強式名稱</span><span class="sxs-lookup"><span data-stu-id="517d6-126">Use enhanced strong names</span></span>  
 <span data-ttu-id="517d6-127">強式名稱金鑰包含簽章金鑰和身分識別金鑰。</span><span class="sxs-lookup"><span data-stu-id="517d6-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="517d6-128">組件以簽章金鑰簽署，而以身分識別金鑰識別。</span><span class="sxs-lookup"><span data-stu-id="517d6-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="517d6-129">在 .NET Framework 4.5 之前，這兩個金鑰完全相同。</span><span class="sxs-lookup"><span data-stu-id="517d6-129">Prior to the .NET Framework 4.5, these two keys were identical.</span></span> <span data-ttu-id="517d6-130">從 .NET Framework 4.5 開始，身分識別金鑰保留與較早 .NET Framework 版本中的相同，但簽章金鑰已經使用更強的雜湊演算法增強。</span><span class="sxs-lookup"><span data-stu-id="517d6-130">Starting with the .NET Framework 4.5, the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="517d6-131">此外，簽章金鑰以身分識別金鑰簽署，以便建立副署。</span><span class="sxs-lookup"><span data-stu-id="517d6-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="517d6-132"><xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性讓組件中繼資料能使用預先存在的公開金鑰處理組件身分識別，如此能讓舊組件參考繼續運作。</span><span class="sxs-lookup"><span data-stu-id="517d6-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="517d6-133"><xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性使用副署來確保新簽章金鑰的擁有者也是舊身分識別金鑰的擁有者。</span><span class="sxs-lookup"><span data-stu-id="517d6-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="sign-with-sha-2-without-key-migration"></a><span data-ttu-id="517d6-134">使用 SHA-1 進行簽署，而不需要金鑰遷移</span><span class="sxs-lookup"><span data-stu-id="517d6-134">Sign with SHA-2, without key migration</span></span>  
 <span data-ttu-id="517d6-135">從命令提示字元執行下列命令來簽署元件，而不需遷移強式名稱簽章：</span><span class="sxs-lookup"><span data-stu-id="517d6-135">Run the following commands from a command prompt to sign an assembly without migrating a strong name signature:</span></span>  
  
1. <span data-ttu-id="517d6-136">(如有必要) 產生新的身分識別金鑰。</span><span class="sxs-lookup"><span data-stu-id="517d6-136">Generate the new identity key (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. <span data-ttu-id="517d6-137">取得身分識別公開金鑰，並指定使用此金鑰簽署時，應該使用 SHA-2 演算法。</span><span class="sxs-lookup"><span data-stu-id="517d6-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="517d6-138">使用身分識別公用金鑰檔案延遲簽署組件。</span><span class="sxs-lookup"><span data-stu-id="517d6-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. <span data-ttu-id="517d6-139">使用完整身分識別金鑰組重新簽署組件。</span><span class="sxs-lookup"><span data-stu-id="517d6-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a><span data-ttu-id="517d6-140">以 SHA-2 簽署，並使用金鑰遷移</span><span class="sxs-lookup"><span data-stu-id="517d6-140">Sign with SHA-2, with key migration</span></span>  
 <span data-ttu-id="517d6-141">從命令提示字元執行下列命令，以使用已遷移的強式名稱簽章來簽署元件。</span><span class="sxs-lookup"><span data-stu-id="517d6-141">Run the following commands from a command prompt to sign an assembly with a migrated strong name signature.</span></span>  
  
1. <span data-ttu-id="517d6-142">(如有必要) 產生身分識別與簽章金鑰組。</span><span class="sxs-lookup"><span data-stu-id="517d6-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. <span data-ttu-id="517d6-143">取得簽章公開金鑰，並指定使用此金鑰簽署時，應該使用 SHA-2 演算法。</span><span class="sxs-lookup"><span data-stu-id="517d6-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="517d6-144">取得身分識別公開金鑰，它決定產生副署的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="517d6-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. <span data-ttu-id="517d6-145">產生 <xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性的參數，然後將屬性附加至組件。</span><span class="sxs-lookup"><span data-stu-id="517d6-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="517d6-146">這會產生類似下列內容的輸出。</span><span class="sxs-lookup"><span data-stu-id="517d6-146">This produces output similar to the following.</span></span>

    ```output
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    <span data-ttu-id="517d6-147">此輸出即會轉換成 AssemblySignatureKeyAttribute。</span><span class="sxs-lookup"><span data-stu-id="517d6-147">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. <span data-ttu-id="517d6-148">使用身分識別公用金鑰延遲簽署組件。</span><span class="sxs-lookup"><span data-stu-id="517d6-148">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. <span data-ttu-id="517d6-149">使用簽章金鑰組完整簽署組件。</span><span class="sxs-lookup"><span data-stu-id="517d6-149">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="517d6-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="517d6-150">See also</span></span>

- [<span data-ttu-id="517d6-151">建立和使用強式名稱的元件</span><span class="sxs-lookup"><span data-stu-id="517d6-151">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
