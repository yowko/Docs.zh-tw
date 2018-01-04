---
title: "強式命名 (Unmanaged API 參考)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2127cdb1178da37bcfe77a0e1a02ccd34be2d800
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="b0303-102">強式命名 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="b0303-102">Strong Naming (Unmanaged API Reference)</span></span>
<span data-ttu-id="b0303-103">強式命名 API 可讓用戶端管理強式名稱簽署組件。</span><span class="sxs-lookup"><span data-stu-id="b0303-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="b0303-104">使用強式名稱簽署組件，就會將公開金鑰加密加入含有組件資訊清單的檔案中。</span><span class="sxs-lookup"><span data-stu-id="b0303-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="b0303-105">強式名稱簽署可協助驗證唯一名稱，可防止冒用名稱，並解析參考時呼叫端提供的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="b0303-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="b0303-106">不過，任何層級不是信任的強式名稱與相關聯。</span><span class="sxs-lookup"><span data-stu-id="b0303-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0303-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="b0303-107">In This Section</span></span>  
 [<span data-ttu-id="b0303-108">強式命名全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="b0303-108">Strong Naming Global Static Functions</span></span>](http://msdn.microsoft.com/en-us/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)  
 <span data-ttu-id="b0303-109">描述的 unmanaged 全域靜態函式強式命名 API 所使用。</span><span class="sxs-lookup"><span data-stu-id="b0303-109">Describes the unmanaged global static functions that the strong naming API uses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0303-110">所有這些函式被取代開頭為[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-110">All of these functions have been deprecated starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="b0303-111">建議的替代項目，請參閱[ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="b0303-111">For suggested alternatives, see the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="b0303-112">GetHashFromAssemblyFile 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-112">GetHashFromAssemblyFile Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 <span data-ttu-id="b0303-113">取得指定的組件檔案，使用指定的雜湊演算法的雜湊。</span><span class="sxs-lookup"><span data-stu-id="b0303-113">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="b0303-114">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-114">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-115">GetHashFromAssemblyFileW 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-115">GetHashFromAssemblyFileW Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="b0303-116">取得指定的 Unicode 字串，使用指定的雜湊演算法的組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="b0303-116">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="b0303-117">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-117">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-118">GetHashFromBlob 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-118">GetHashFromBlob Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 <span data-ttu-id="b0303-119">取得該組件的雜湊指定的記憶體位址，使用指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="b0303-119">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="b0303-120">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-120">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-121">GetHashFromFile 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-121">GetHashFromFile Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 <span data-ttu-id="b0303-122">透過指定檔案的內容中產生之雜湊。</span><span class="sxs-lookup"><span data-stu-id="b0303-122">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="b0303-123">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-123">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-124">GetHashFromFileW 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-124">GetHashFromFileW Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 <span data-ttu-id="b0303-125">產生之雜湊的 Unicode 字串所指定的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="b0303-125">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="b0303-126">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-126">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-127">GetHashFromHandle 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-127">GetHashFromHandle Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 <span data-ttu-id="b0303-128">產生之雜湊與指定的檔案控制代碼，使用指定的雜湊演算法檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="b0303-128">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="b0303-129">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-129">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-130">StrongNameCompareAssemblies 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-130">StrongNameCompareAssemblies Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 <span data-ttu-id="b0303-131">判斷兩個組件是否只有其強式名稱簽章不同。</span><span class="sxs-lookup"><span data-stu-id="b0303-131">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="b0303-132">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-132">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-133">StrongNameErrorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-133">StrongNameErrorInfo Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 <span data-ttu-id="b0303-134">取得其中一個強式名稱的函式所引發的最後一個錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="b0303-134">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="b0303-135">StrongNameFreeBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-135">StrongNameFreeBuffer Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 <span data-ttu-id="b0303-136">釋放記憶體配置與先前的強式名稱的函式呼叫這類[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)， [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)，或[StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="b0303-136">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="b0303-137">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-137">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-138">StrongNameGetBlob 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-138">StrongNameGetBlob Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 <span data-ttu-id="b0303-139">在指定位址之可執行檔的二進位表示法中填入指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b0303-139">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="b0303-140">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-140">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-141">StrongNameGetBlobFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-141">StrongNameGetBlobFromImage Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="b0303-142">取得組件映像的二進位表示法，在指定的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="b0303-142">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="b0303-143">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-143">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-144">StrongNameGetPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-144">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 <span data-ttu-id="b0303-145">從私密/公開金鑰組取得的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="b0303-145">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="b0303-146">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-146">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-147">StrongNameHashSize 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-147">StrongNameHashSize Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 <span data-ttu-id="b0303-148">取得所需的雜湊，並使用指定的雜湊演算法的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="b0303-148">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="b0303-149">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-149">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-150">StrongNameKeyDelete 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-150">StrongNameKeyDelete Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 <span data-ttu-id="b0303-151">刪除指定的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="b0303-151">Deletes the specified key container.</span></span> <span data-ttu-id="b0303-152">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-152">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-153">StrongNameKeyGen 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-153">StrongNameKeyGen Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 <span data-ttu-id="b0303-154">建立新公用/私密金鑰組的強式名稱使用。</span><span class="sxs-lookup"><span data-stu-id="b0303-154">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="b0303-155">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-155">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-156">StrongNameKeyGenEx 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-156">StrongNameKeyGenEx Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 <span data-ttu-id="b0303-157">會產生新的公用/私用金鑰組的強式名稱使用指定的金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="b0303-157">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="b0303-158">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-158">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-159">StrongNameKeyInstall 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-159">StrongNameKeyInstall Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 <span data-ttu-id="b0303-160">匯入容器的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="b0303-160">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="b0303-161">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-161">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-162">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-162">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="b0303-163">產生強式名稱簽章的指定組件。</span><span class="sxs-lookup"><span data-stu-id="b0303-163">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="b0303-164">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-164">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-165">StrongNameSignatureGenerationEx 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-165">StrongNameSignatureGenerationEx Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="b0303-166">指定的組件，並根據指定的旗標產生的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="b0303-166">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="b0303-167">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-167">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-168">StrongNameSignatureSize 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-168">StrongNameSignatureSize Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 <span data-ttu-id="b0303-169">傳回強式名稱簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="b0303-169">Returns the size of the strong name signature.</span></span> <span data-ttu-id="b0303-170">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-170">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-171">StrongNameSignatureVerification 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-171">StrongNameSignatureVerification Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 <span data-ttu-id="b0303-172">取得值，指出是否在提供的路徑上組件資訊清單包含強式名稱簽章，根據指定的旗標加以確認。</span><span class="sxs-lookup"><span data-stu-id="b0303-172">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="b0303-173">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-173">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-174">StrongNameSignatureVerificationEx 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-174">StrongNameSignatureVerificationEx Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="b0303-175">取得值，指出是否在提供的路徑上組件資訊清單包含強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="b0303-175">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="b0303-176">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-176">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-177">StrongNameSignatureVerificationFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-177">StrongNameSignatureVerificationFromImage Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="b0303-178">請確認已對應到記憶體的組件適用於相關聯的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="b0303-178">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="b0303-179">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-179">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-180">StrongNameTokenFromAssembly 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-180">StrongNameTokenFromAssembly Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 <span data-ttu-id="b0303-181">從指定的組件檔案中建立強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b0303-181">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="b0303-182">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-182">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-183">StrongNameTokenFromAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-183">StrongNameTokenFromAssemblyEx Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="b0303-184">從指定的組件檔案中，建立強式名稱語彙基元，並傳回公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="b0303-184">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="b0303-185">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-185">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-186">StrongNameTokenFromPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="b0303-186">StrongNameTokenFromPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="b0303-187">取得代表公開金鑰的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b0303-187">Gets a token representing a public key.</span></span> <span data-ttu-id="b0303-188">起過時的[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b0303-188">Deprecated starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="b0303-189">強式命名結構</span><span class="sxs-lookup"><span data-stu-id="b0303-189">Strong Naming Structure</span></span>](http://msdn.microsoft.com/en-us/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)  
 <span data-ttu-id="b0303-190">描述強式命名 API 來管理強式名稱簽署組件所使用的 unmanaged 的結構...</span><span class="sxs-lookup"><span data-stu-id="b0303-190">Describes the unmanaged structure that the strong naming API uses  to administer strong name signing for assemblies..</span></span>  
  
 [<span data-ttu-id="b0303-191">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="b0303-191">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 <span data-ttu-id="b0303-192">表示以二進位格式公開/私密金鑰組的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="b0303-192">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0303-193">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0303-193">See Also</span></span>  
 [<span data-ttu-id="b0303-194">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="b0303-194">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="b0303-195">Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="b0303-195">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)
