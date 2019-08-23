---
title: 強式命名 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 343abf450a49ad222c403c28e46c6e3aac33e1b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966157"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="d3fa2-102">強式命名 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="d3fa2-102">Strong Naming (Unmanaged API Reference)</span></span>
<span data-ttu-id="d3fa2-103">強式命名 API 可讓用戶端管理組件的強式命名簽署。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="d3fa2-104">使用強式名稱簽署組件，就會將公開金鑰加密加入含有組件資訊清單的檔案中。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="d3fa2-105">強式名稱簽署可協助驗證名稱唯一性，防止名稱冒用，並且在解析參考時為呼叫者提供唯一身分識別。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="d3fa2-106">但是，並沒有任何信任等級與強式名稱關聯。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3fa2-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="d3fa2-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3fa2-108">從 .NET Framework 4 開始，所有這些函式都已過時。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="d3fa2-109">如需建議的替代函式，請參閱 [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-109">For suggested alternatives, see the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="d3fa2-110">GetHashFromAssemblyFile 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-110">GetHashFromAssemblyFile Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 <span data-ttu-id="d3fa2-111">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="d3fa2-112">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-113">GetHashFromAssemblyFileW 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-113">GetHashFromAssemblyFileW Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="d3fa2-114">使用指定的雜湊演算法取得以 Unicode 字串形式指定的組件檔案雜湊。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="d3fa2-115">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-116">GetHashFromBlob 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-116">GetHashFromBlob Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 <span data-ttu-id="d3fa2-117">使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="d3fa2-118">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-119">GetHashFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-119">GetHashFromFile Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 <span data-ttu-id="d3fa2-120">產生指定檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="d3fa2-121">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-122">GetHashFromFileW 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-122">GetHashFromFileW Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 <span data-ttu-id="d3fa2-123">產生以 Unicode 字串指定之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="d3fa2-124">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-125">GetHashFromHandle 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-125">GetHashFromHandle Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 <span data-ttu-id="d3fa2-126">使用指定的雜湊演算法產生以指定檔案控制代碼指定之檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="d3fa2-127">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-128">StrongNameCompareAssemblies 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-128">StrongNameCompareAssemblies Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 <span data-ttu-id="d3fa2-129">判斷兩個組件是否只有強制名稱簽章不同。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="d3fa2-130">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-131">StrongNameErrorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-131">StrongNameErrorInfo Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 <span data-ttu-id="d3fa2-132">取得由其中一強式名稱函式所引發的最後一個錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="d3fa2-133">StrongNameFreeBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-133">StrongNameFreeBuffer Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 <span data-ttu-id="d3fa2-134">釋放使用對強式名稱函式 (例如 [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md) 或 [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)) 的上一個呼叫所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="d3fa2-135">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-136">StrongNameGetBlob 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-136">StrongNameGetBlob Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 <span data-ttu-id="d3fa2-137">使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="d3fa2-138">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-139">StrongNameGetBlobFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-139">StrongNameGetBlobFromImage Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="d3fa2-140">取得位於所指定記憶體位置之組件影像的二進位表示法。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="d3fa2-141">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-142">StrongNameGetPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-142">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 <span data-ttu-id="d3fa2-143">從私密/公開金鑰組取得公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="d3fa2-144">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-145">StrongNameHashSize 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-145">StrongNameHashSize Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 <span data-ttu-id="d3fa2-146">使用指定的雜湊演算法取得雜湊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="d3fa2-147">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-148">StrongNameKeyDelete 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-148">StrongNameKeyDelete Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 <span data-ttu-id="d3fa2-149">刪除指定的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-149">Deletes the specified key container.</span></span> <span data-ttu-id="d3fa2-150">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-151">StrongNameKeyGen 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-151">StrongNameKeyGen Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 <span data-ttu-id="d3fa2-152">建立將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="d3fa2-153">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-154">StrongNameKeyGenEx 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-154">StrongNameKeyGenEx Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 <span data-ttu-id="d3fa2-155">使用指定的金鑰大小產生將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="d3fa2-156">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-157">StrongNameKeyInstall 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-157">StrongNameKeyInstall Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 <span data-ttu-id="d3fa2-158">將公開/私密金鑰組匯入到容器中。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="d3fa2-159">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-160">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-160">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="d3fa2-161">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="d3fa2-162">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-163">StrongNameSignatureGenerationEx 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-163">StrongNameSignatureGenerationEx Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="d3fa2-164">以指定的旗標為基礎產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="d3fa2-165">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-166">StrongNameSignatureSize 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-166">StrongNameSignatureSize Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 <span data-ttu-id="d3fa2-167">傳回強式名稱簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="d3fa2-168">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-169">StrongNameSignatureVerification 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-169">StrongNameSignatureVerification Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 <span data-ttu-id="d3fa2-170">取得指出位於所指定路徑之組件資訊清單是否包含強式名稱簽章的值 (會根據指定的旗標驗證此值)。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="d3fa2-171">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-172">StrongNameSignatureVerificationEx 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-172">StrongNameSignatureVerificationEx Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="d3fa2-173">取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="d3fa2-174">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-175">StrongNameSignatureVerificationFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-175">StrongNameSignatureVerificationFromImage Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="d3fa2-176">驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="d3fa2-177">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-178">StrongNameTokenFromAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-178">StrongNameTokenFromAssembly Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 <span data-ttu-id="d3fa2-179">從指定的組件檔案建立強式名稱權杖。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="d3fa2-180">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-181">StrongNameTokenFromAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-181">StrongNameTokenFromAssemblyEx Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="d3fa2-182">從指定組件檔案建立強式名稱權杖，並傳回公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="d3fa2-183">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-184">StrongNameTokenFromPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="d3fa2-184">StrongNameTokenFromPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="d3fa2-185">取得代表公開金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-185">Gets a token representing a public key.</span></span> <span data-ttu-id="d3fa2-186">自 .NET Framework 4 起淘汰。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="d3fa2-187">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="d3fa2-187">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 <span data-ttu-id="d3fa2-188">代表公開/私密金鑰組的公開金鑰 (二進位格式)。</span><span class="sxs-lookup"><span data-stu-id="d3fa2-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3fa2-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3fa2-189">See also</span></span>

- [<span data-ttu-id="d3fa2-190">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d3fa2-190">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="d3fa2-191">Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="d3fa2-191">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)
