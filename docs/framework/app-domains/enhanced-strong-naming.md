---
title: "進階強式命名"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 429a54340cef6d608692abd71311c012afe9a3d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="48200-102">進階強式命名</span><span class="sxs-lookup"><span data-stu-id="48200-102">Enhanced Strong Naming</span></span>
<span data-ttu-id="48200-103">強式名稱簽章是 .NET Framework 中的身分識別機制，用來識別組件。</span><span class="sxs-lookup"><span data-stu-id="48200-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="48200-104">它是公開金鑰數位簽章，通常用來驗證從建立者 (簽署者) 傳遞給收件者 (驗證者) 的資料完整性。</span><span class="sxs-lookup"><span data-stu-id="48200-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="48200-105">此簽章用來當作組件的唯一身分識別，並可確保對組件的參考不會模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="48200-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="48200-106">組件在建置程序的一部分簽署，然後在載入時加以驗證。</span><span class="sxs-lookup"><span data-stu-id="48200-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="48200-107">強式名稱簽章可協助防止惡徒竄改組件，然後使用原始簽署者的金鑰重新簽署組件。</span><span class="sxs-lookup"><span data-stu-id="48200-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="48200-108">不過，強式名稱金鑰並不包含關於發行者的任何可靠資訊，也不包含憑證階層。</span><span class="sxs-lookup"><span data-stu-id="48200-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="48200-109">強式名稱簽章不保證簽署組件之人的可信度，或指出該人是否為金鑰的合法擁有者；它僅指出金鑰的擁有者簽署了該組件。</span><span class="sxs-lookup"><span data-stu-id="48200-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="48200-110">因此，我們不建議使用強式名稱簽章作為安全性驗證而來信任協力廠商程式碼。</span><span class="sxs-lookup"><span data-stu-id="48200-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="48200-111">Microsoft Authenticode 是驗證程式碼的建議方式。</span><span class="sxs-lookup"><span data-stu-id="48200-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="48200-112">傳統強式名稱的限制</span><span class="sxs-lookup"><span data-stu-id="48200-112">Limitations of Conventional Strong Names</span></span>  
 <span data-ttu-id="48200-113">在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 之前的版本所使用的強式命名技術有下列缺點：</span><span class="sxs-lookup"><span data-stu-id="48200-113">The strong naming technology used in versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has the following shortcomings:</span></span>  
  
-   <span data-ttu-id="48200-114">金鑰經常受到攻擊，改善的技術和硬體能夠更輕鬆從公開金鑰推斷私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="48200-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="48200-115">為了防範攻擊，必須使用較大的金鑰。</span><span class="sxs-lookup"><span data-stu-id="48200-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="48200-116">在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 之前的 .NET Framework 版本，可讓您以任何大小的金鑰 (預設大小為 1024 位元) 簽署，但使用新的金鑰簽署組件會中斷參考組件較舊身分識別的所有二進位檔。</span><span class="sxs-lookup"><span data-stu-id="48200-116">.NET Framework versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="48200-117">因此，如果您想要維護相容性，很難升級簽署金鑰的大小。</span><span class="sxs-lookup"><span data-stu-id="48200-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
-   <span data-ttu-id="48200-118">強式名稱簽署只支援 SHA-1 演算法。</span><span class="sxs-lookup"><span data-stu-id="48200-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="48200-119">最近已發現 SHA-1 不足以應付安全雜湊應用程式。</span><span class="sxs-lookup"><span data-stu-id="48200-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="48200-120">因此，必須使用更強的演算法 (SHA-256 或以上)。</span><span class="sxs-lookup"><span data-stu-id="48200-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="48200-121">很可能 SHA-1 會失去其與 FIPS 相容的地位，如此對於選擇只使用與 FIPS 相容的軟體和演算法的人會造成問題。</span><span class="sxs-lookup"><span data-stu-id="48200-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="48200-122">增強強式名稱的優點</span><span class="sxs-lookup"><span data-stu-id="48200-122">Advantages of Enhanced Strong Names</span></span>  
 <span data-ttu-id="48200-123">增強強式名稱的主要優點是與預先存在的強式名稱相容，以及能夠宣告一個身分識別相當於另一個身分識別：</span><span class="sxs-lookup"><span data-stu-id="48200-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
-   <span data-ttu-id="48200-124">有預先存在的已簽署組件的開發人員，可以將他們的身分識別移轉至 SHA-2 演算法，同時維持與參考舊身分識別的組件相容性。</span><span class="sxs-lookup"><span data-stu-id="48200-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
-   <span data-ttu-id="48200-125">建立新組件而且不在意預先存在的強式名稱簽章的開發人員，可以使用更安全的 SHA-2 演算法，並如往常般簽署組件。</span><span class="sxs-lookup"><span data-stu-id="48200-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="using-enhanced-strong-names"></a><span data-ttu-id="48200-126">使用進階強式名稱</span><span class="sxs-lookup"><span data-stu-id="48200-126">Using Enhanced Strong Names</span></span>  
 <span data-ttu-id="48200-127">強式名稱金鑰包含簽章金鑰和身分識別金鑰。</span><span class="sxs-lookup"><span data-stu-id="48200-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="48200-128">組件以簽章金鑰簽署，而以身分識別金鑰識別。</span><span class="sxs-lookup"><span data-stu-id="48200-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="48200-129">在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 之前，這兩個金鑰完全相同。</span><span class="sxs-lookup"><span data-stu-id="48200-129">Prior to the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], these two keys were identical.</span></span> <span data-ttu-id="48200-130">從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，身分識別金鑰保留與較早 .NET Framework 版本中的相同，但簽章金鑰已經使用更強的雜湊演算法增強。</span><span class="sxs-lookup"><span data-stu-id="48200-130">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="48200-131">此外，簽章金鑰以身分識別金鑰簽署，以便建立副署。</span><span class="sxs-lookup"><span data-stu-id="48200-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="48200-132"><xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性讓組件中繼資料能使用預先存在的公開金鑰處理組件身分識別，如此能讓舊組件參考繼續運作。</span><span class="sxs-lookup"><span data-stu-id="48200-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="48200-133"><xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性使用副署來確保新簽章金鑰的擁有者也是舊身分識別金鑰的擁有者。</span><span class="sxs-lookup"><span data-stu-id="48200-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="signing-with-sha-2-without-key-migration"></a><span data-ttu-id="48200-134">使用 SHA-2 簽署，而不需要金鑰移轉</span><span class="sxs-lookup"><span data-stu-id="48200-134">Signing with SHA-2, Without Key Migration</span></span>  
 <span data-ttu-id="48200-135">從命令提示字元視窗中執行下列命令簽署組件，而不移轉強式名稱簽章：</span><span class="sxs-lookup"><span data-stu-id="48200-135">Run the following commands from a Command Prompt window to sign an assembly without migrating a strong name signature:</span></span>  
  
1.  <span data-ttu-id="48200-136">(如有必要) 產生新的身分識別金鑰。</span><span class="sxs-lookup"><span data-stu-id="48200-136">Generate the new identity key (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  <span data-ttu-id="48200-137">取得身分識別公開金鑰，並指定使用此金鑰簽署時，應該使用 SHA-2 演算法。</span><span class="sxs-lookup"><span data-stu-id="48200-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="48200-138">使用身分識別公用金鑰檔案延遲簽署組件。</span><span class="sxs-lookup"><span data-stu-id="48200-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  <span data-ttu-id="48200-139">使用完整身分識別金鑰組重新簽署組件。</span><span class="sxs-lookup"><span data-stu-id="48200-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a><span data-ttu-id="48200-140">使用 SHA-2 簽署，並且進行金鑰移轉</span><span class="sxs-lookup"><span data-stu-id="48200-140">Signing with SHA-2, with Key Migration</span></span>  
 <span data-ttu-id="48200-141">從命令提示字元視窗中執行下列命令，使用移轉的強式名稱簽章來簽署組件。</span><span class="sxs-lookup"><span data-stu-id="48200-141">Run the following commands from a Command Prompt window to sign an assembly with a migrated strong name signature.</span></span>  
  
1.  <span data-ttu-id="48200-142">(如有必要) 產生身分識別與簽章金鑰組。</span><span class="sxs-lookup"><span data-stu-id="48200-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  <span data-ttu-id="48200-143">取得簽章公開金鑰，並指定使用此金鑰簽署時，應該使用 SHA-2 演算法。</span><span class="sxs-lookup"><span data-stu-id="48200-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="48200-144">取得身分識別公開金鑰，它決定產生副署的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="48200-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  <span data-ttu-id="48200-145">產生 <xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性的參數，然後將屬性附加至組件。</span><span class="sxs-lookup"><span data-stu-id="48200-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  <span data-ttu-id="48200-146">使用身分識別公用金鑰延遲簽署組件。</span><span class="sxs-lookup"><span data-stu-id="48200-146">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  <span data-ttu-id="48200-147">使用簽章金鑰組完整簽署組件。</span><span class="sxs-lookup"><span data-stu-id="48200-147">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="48200-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48200-148">See Also</span></span>  
 [<span data-ttu-id="48200-149">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="48200-149">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
