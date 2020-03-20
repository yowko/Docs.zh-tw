---
title: StrongNameGetPublicKeyEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176223"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="ab93b-102">StrongNameGetPublicKeyEx 方法</span><span class="sxs-lookup"><span data-stu-id="ab93b-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="ab93b-103">從公開金鑰/私密金鑰對獲取公開金鑰，並指定雜湊演算法和簽名演算法。</span><span class="sxs-lookup"><span data-stu-id="ab93b-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab93b-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab93b-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab93b-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab93b-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="ab93b-106">[在]包含公開金鑰/私密金鑰對的金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab93b-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="ab93b-107">如果`pbKeyBlob`為 null，`szKeyContainer`則必須在加密服務提供者 （CSP） 中指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="ab93b-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="ab93b-108">在這種情況下，`StrongNameGetPublicKeyEx`該方法從存儲在容器中的金鑰組中提取公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="ab93b-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="ab93b-109">如果`pbKeyBlob`不是空，則假定金鑰組包含在金鑰二進位大型物件 （BLOB） 中。</span><span class="sxs-lookup"><span data-stu-id="ab93b-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ab93b-110">金鑰必須是 1024 位裡維斯-沙米爾-阿德爾曼 （RSA） 簽名金鑰。</span><span class="sxs-lookup"><span data-stu-id="ab93b-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ab93b-111">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="ab93b-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ab93b-112">[在]指向公開金鑰/私密金鑰對的指標。</span><span class="sxs-lookup"><span data-stu-id="ab93b-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ab93b-113">此對採用 Win32`CryptExportKey`函數創建的格式。</span><span class="sxs-lookup"><span data-stu-id="ab93b-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ab93b-114">如果`pbKeyBlob`為 null，則假定 指定的`szKeyContainer`鍵容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="ab93b-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ab93b-115">[在]的大小（以位元組為單位）的大小`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="ab93b-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ab93b-116">[出]返回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="ab93b-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="ab93b-117">參數`ppbPublicKeyBlob`由通用語言運行時分配並返回到調用方。</span><span class="sxs-lookup"><span data-stu-id="ab93b-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="ab93b-118">調用方必須使用[ICLRStrongNameName：：StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="ab93b-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ab93b-119">[出]返回的公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="ab93b-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="ab93b-120">[在]程式集雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="ab93b-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="ab93b-121">有關已接受值的清單，請參閱備註部分。</span><span class="sxs-lookup"><span data-stu-id="ab93b-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="ab93b-122">[在]保留供將來使用;預設值為 null。</span><span class="sxs-lookup"><span data-stu-id="ab93b-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab93b-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="ab93b-123">Return Value</span></span>  
 <span data-ttu-id="ab93b-124">`S_OK`如果方法成功完成;如果方法成功完成;否則，指示失敗的 HRESULT 值（請參閱清單[的常用 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="ab93b-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab93b-125">備註</span><span class="sxs-lookup"><span data-stu-id="ab93b-125">Remarks</span></span>  
 <span data-ttu-id="ab93b-126">公開金鑰包含在[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構中。</span><span class="sxs-lookup"><span data-stu-id="ab93b-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab93b-127">備註</span><span class="sxs-lookup"><span data-stu-id="ab93b-127">Remarks</span></span>  
 <span data-ttu-id="ab93b-128">下表顯示了`uHashAlgId`參數的接受值集。</span><span class="sxs-lookup"><span data-stu-id="ab93b-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="ab93b-129">名稱</span><span class="sxs-lookup"><span data-stu-id="ab93b-129">Name</span></span>|<span data-ttu-id="ab93b-130">值</span><span class="sxs-lookup"><span data-stu-id="ab93b-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="ab93b-131">None</span><span class="sxs-lookup"><span data-stu-id="ab93b-131">None</span></span>|<span data-ttu-id="ab93b-132">0</span><span class="sxs-lookup"><span data-stu-id="ab93b-132">0</span></span>|  
|<span data-ttu-id="ab93b-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="ab93b-133">SHA-1</span></span>|<span data-ttu-id="ab93b-134">0 x8004</span><span class="sxs-lookup"><span data-stu-id="ab93b-134">0x8004</span></span>|  
|<span data-ttu-id="ab93b-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="ab93b-135">SHA-256</span></span>|<span data-ttu-id="ab93b-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="ab93b-136">0x800c</span></span>|  
|<span data-ttu-id="ab93b-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="ab93b-137">SHA-384</span></span>|<span data-ttu-id="ab93b-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="ab93b-138">0x800d</span></span>|  
|<span data-ttu-id="ab93b-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="ab93b-139">SHA-512</span></span>|<span data-ttu-id="ab93b-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="ab93b-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab93b-141">需求</span><span class="sxs-lookup"><span data-stu-id="ab93b-141">Requirements</span></span>  
 <span data-ttu-id="ab93b-142">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab93b-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab93b-143">**標題：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ab93b-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ab93b-144">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ab93b-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab93b-145">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab93b-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab93b-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab93b-146">See also</span></span>

- [<span data-ttu-id="ab93b-147">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="ab93b-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="ab93b-148">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="ab93b-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="ab93b-149">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="ab93b-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="ab93b-150">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="ab93b-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
