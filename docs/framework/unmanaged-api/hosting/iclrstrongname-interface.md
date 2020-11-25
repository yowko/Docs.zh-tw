---
title: ICLRStrongName 介面
ms.date: 03/30/2017
api_name:
- ICLRStrongName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName
helpviewer_keywords:
- ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type:
- apiref
ms.openlocfilehash: 691cc3cf4ec8d036a4de04247f243d99daa887d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733629"
---
# <a name="iclrstrongname-interface"></a><span data-ttu-id="245e0-102">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="245e0-102">ICLRStrongName Interface</span></span>

<span data-ttu-id="245e0-103">提供基本的全域靜態函式來簽署具有強式名稱的元件。</span><span class="sxs-lookup"><span data-stu-id="245e0-103">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="245e0-104">所有 `ICLRStrongName` 方法都會傳回標準 COM hresult。</span><span class="sxs-lookup"><span data-stu-id="245e0-104">All `ICLRStrongName` methods return standard COM HRESULTs.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="245e0-105">方法</span><span class="sxs-lookup"><span data-stu-id="245e0-105">Methods</span></span>  
  
|<span data-ttu-id="245e0-106">方法</span><span class="sxs-lookup"><span data-stu-id="245e0-106">Method</span></span>|<span data-ttu-id="245e0-107">描述</span><span class="sxs-lookup"><span data-stu-id="245e0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="245e0-108">GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-108">GetHashFromAssemblyFile Method</span></span>](iclrstrongname-gethashfromassemblyfile-method.md)|<span data-ttu-id="245e0-109">使用指定的雜湊演算法取得所指定組件檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="245e0-109">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>|  
|[<span data-ttu-id="245e0-110">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-110">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)|<span data-ttu-id="245e0-111">使用指定的雜湊演算法取得以 Unicode 字串形式指定的組件檔案雜湊。</span><span class="sxs-lookup"><span data-stu-id="245e0-111">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span>|  
|[<span data-ttu-id="245e0-112">GetHashFromBlob 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-112">GetHashFromBlob Method</span></span>](iclrstrongname-gethashfromblob-method.md)|<span data-ttu-id="245e0-113">使用指定的雜湊演算法取得位於指定記憶體位址之組件的雜湊。</span><span class="sxs-lookup"><span data-stu-id="245e0-113">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>|  
|[<span data-ttu-id="245e0-114">GetHashFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-114">GetHashFromFile Method</span></span>](iclrstrongname-gethashfromfile-method.md)|<span data-ttu-id="245e0-115">產生指定檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="245e0-115">Generates a hash over the contents of the specified file.</span></span>|  
|[<span data-ttu-id="245e0-116">GetHashFromFileW 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-116">GetHashFromFileW Method</span></span>](iclrstrongname-gethashfromfilew-method.md)|<span data-ttu-id="245e0-117">產生以 Unicode 字串指定之檔案內容的雜湊。</span><span class="sxs-lookup"><span data-stu-id="245e0-117">Generates a hash over the contents of the file specified by a Unicode string.</span></span>|  
|[<span data-ttu-id="245e0-118">GetHashFromHandle 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-118">GetHashFromHandle Method</span></span>](iclrstrongname-gethashfromhandle-method.md)|<span data-ttu-id="245e0-119">使用指定的雜湊演算法產生以指定檔案控制代碼指定之檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="245e0-119">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>|  
|[<span data-ttu-id="245e0-120">StrongNameCompareAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-120">StrongNameCompareAssemblies Method</span></span>](iclrstrongname-strongnamecompareassemblies-method.md)|<span data-ttu-id="245e0-121">判斷兩個組件是否只有強制名稱簽章不同。</span><span class="sxs-lookup"><span data-stu-id="245e0-121">Determines whether two assemblies differ only by their strong name signatures.</span></span>|  
|[<span data-ttu-id="245e0-122">StrongNameFreeBuffer 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-122">StrongNameFreeBuffer Method</span></span>](iclrstrongname-strongnamefreebuffer-method.md)|<span data-ttu-id="245e0-123">釋放先前呼叫強式名稱方法（例如 [StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md)、 [StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md)或 [StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md)）所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="245e0-123">Frees memory that was allocated with a previous call to a strong name method such as [StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md), or [StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>|  
|[<span data-ttu-id="245e0-124">StrongNameGetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-124">StrongNameGetBlob Method</span></span>](iclrstrongname-strongnamegetblob-method.md)|<span data-ttu-id="245e0-125">使用位於所指定位址之可執行檔的二進位表示法填滿指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="245e0-125">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>|  
|[<span data-ttu-id="245e0-126">StrongNameGetBlobFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-126">StrongNameGetBlobFromImage Method</span></span>](iclrstrongname-strongnamegetblobfromimage-method.md)|<span data-ttu-id="245e0-127">取得位於所指定記憶體位置之組件影像的二進位表示法。</span><span class="sxs-lookup"><span data-stu-id="245e0-127">Gets a binary representation of the assembly image at the specified memory address.</span></span>|  
|[<span data-ttu-id="245e0-128">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-128">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)|<span data-ttu-id="245e0-129">從私密/公開金鑰組取得公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="245e0-129">Gets the public key from a private/public key pair.</span></span>|  
|[<span data-ttu-id="245e0-130">StrongNameHashSize 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-130">StrongNameHashSize Method</span></span>](iclrstrongname-strongnamehashsize-method.md)|<span data-ttu-id="245e0-131">使用指定的雜湊演算法取得雜湊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="245e0-131">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>|  
|[<span data-ttu-id="245e0-132">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-132">StrongNameKeyDelete Method</span></span>](iclrstrongname-strongnamekeydelete-method.md)|<span data-ttu-id="245e0-133">刪除指定的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="245e0-133">Deletes the specified key container.</span></span>|  
|[<span data-ttu-id="245e0-134">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-134">StrongNameKeyGen Method</span></span>](iclrstrongname-strongnamekeygen-method.md)|<span data-ttu-id="245e0-135">建立將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="245e0-135">Creates a new public/private key pair for strong name use.</span></span>|  
|[<span data-ttu-id="245e0-136">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-136">StrongNameKeyGenEx Method</span></span>](iclrstrongname-strongnamekeygenex-method.md)|<span data-ttu-id="245e0-137">使用指定的金鑰大小產生將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="245e0-137">Generates a new public/private key pair with the specified key size for strong name use.</span></span>|  
|[<span data-ttu-id="245e0-138">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-138">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)|<span data-ttu-id="245e0-139">將公開/私密金鑰組匯入到容器中。</span><span class="sxs-lookup"><span data-stu-id="245e0-139">Imports a public/private key pair into a container.</span></span>|  
|[<span data-ttu-id="245e0-140">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-140">StrongNameSignatureGeneration Method</span></span>](iclrstrongname-strongnamesignaturegeneration-method.md)|<span data-ttu-id="245e0-141">產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="245e0-141">Generates a strong name signature for the specified assembly.</span></span>|  
|[<span data-ttu-id="245e0-142">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-142">StrongNameSignatureGenerationEx Method</span></span>](iclrstrongname-strongnamesignaturegenerationex-method.md)|<span data-ttu-id="245e0-143">以指定的旗標為基礎產生指定組件的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="245e0-143">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>|  
|[<span data-ttu-id="245e0-144">StrongNameSignatureSize 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-144">StrongNameSignatureSize Method</span></span>](iclrstrongname-strongnamesignaturesize-method.md)|<span data-ttu-id="245e0-145">傳回強式名稱簽章的大小。</span><span class="sxs-lookup"><span data-stu-id="245e0-145">Returns the size of the strong name signature.</span></span>|  
|[<span data-ttu-id="245e0-146">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-146">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)|<span data-ttu-id="245e0-147">取得指出位於所指定路徑之組件資訊清單是否包含強式名稱簽章的值 (會根據指定的旗標驗證此值)。</span><span class="sxs-lookup"><span data-stu-id="245e0-147">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>|  
|[<span data-ttu-id="245e0-148">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-148">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)|<span data-ttu-id="245e0-149">取得指出位於指定路徑的組件資訊清單是否包含強式名稱簽章的值。</span><span class="sxs-lookup"><span data-stu-id="245e0-149">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>|  
|[<span data-ttu-id="245e0-150">StrongNameSignatureVerificationFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-150">StrongNameSignatureVerificationFromImage Method</span></span>](iclrstrongname-strongnamesignatureverificationfromimage-method.md)|<span data-ttu-id="245e0-151">驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。</span><span class="sxs-lookup"><span data-stu-id="245e0-151">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>|  
|[<span data-ttu-id="245e0-152">StrongNameTokenFromAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-152">StrongNameTokenFromAssembly Method</span></span>](iclrstrongname-strongnametokenfromassembly-method.md)|<span data-ttu-id="245e0-153">從指定的組件檔案建立強式名稱權杖。</span><span class="sxs-lookup"><span data-stu-id="245e0-153">Creates a strong name token from the specified assembly file.</span></span>|  
|[<span data-ttu-id="245e0-154">StrongNameTokenFromAssemblyEx 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-154">StrongNameTokenFromAssemblyEx Method</span></span>](iclrstrongname-strongnametokenfromassemblyex-method.md)|<span data-ttu-id="245e0-155">從指定組件檔案建立強式名稱權杖，並傳回公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="245e0-155">Creates a strong name token from the specified assembly file, and returns the public key.</span></span>|  
|[<span data-ttu-id="245e0-156">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="245e0-156">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)|<span data-ttu-id="245e0-157">取得代表公開金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="245e0-157">Gets a token representing a public key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="245e0-158">備註</span><span class="sxs-lookup"><span data-stu-id="245e0-158">Remarks</span></span>  

 <span data-ttu-id="245e0-159">您可以 `ICLRStrongName` 使用和做為參數來呼叫 [ICLRRuntimeInfo：： GetInterface](iclrruntimeinfo-getinterface-method.md) 方法，以取得的實例 `CLSID_CLRStrongName` `IID_ICLRStrongName` 。</span><span class="sxs-lookup"><span data-stu-id="245e0-159">You can get an instance of the `ICLRStrongName` by calling the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method using `CLSID_CLRStrongName` and `IID_ICLRStrongName` as parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="245e0-160">需求</span><span class="sxs-lookup"><span data-stu-id="245e0-160">Requirements</span></span>  

 <span data-ttu-id="245e0-161">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="245e0-161">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="245e0-162">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="245e0-162">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="245e0-163">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="245e0-163">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="245e0-164">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="245e0-164">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="245e0-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="245e0-165">See also</span></span>

- [<span data-ttu-id="245e0-166">裝載介面</span><span class="sxs-lookup"><span data-stu-id="245e0-166">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="245e0-167">裝載</span><span class="sxs-lookup"><span data-stu-id="245e0-167">Hosting</span></span>](index.md)
