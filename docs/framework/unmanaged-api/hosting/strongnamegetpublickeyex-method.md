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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cb1f55e1d8643feb2750e8ea468f608dc3d5d40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212059"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="00106-102">StrongNameGetPublicKeyEx 方法</span><span class="sxs-lookup"><span data-stu-id="00106-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="00106-103">公開/私密金鑰組，從取得的公開金鑰，並指定雜湊演算法和簽章演算法。</span><span class="sxs-lookup"><span data-stu-id="00106-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00106-104">語法</span><span class="sxs-lookup"><span data-stu-id="00106-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="00106-105">參數</span><span class="sxs-lookup"><span data-stu-id="00106-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="00106-106">[in]包含 public/private 金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="00106-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="00106-107">如果`pbKeyBlob`為 null，`szKeyContainer`必須指定有效的容器內的密碼編譯服務提供者 (CSP)。</span><span class="sxs-lookup"><span data-stu-id="00106-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="00106-108">在此情況下，`StrongNameGetPublicKeyEx`方法會從容器中所儲存的金鑰組擷取公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="00106-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="00106-109">如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="00106-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="00106-110">索引鍵必須是 1024年位元 Rivest-shamir-adleman/digital signature Standard (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="00106-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="00106-111">目前支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="00106-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="00106-112">[in]Public/private 金鑰組指標。</span><span class="sxs-lookup"><span data-stu-id="00106-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="00106-113">此配對的格式建立 win32`CryptExportKey`函式。</span><span class="sxs-lookup"><span data-stu-id="00106-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="00106-114">如果`pbKeyBlob`是 null，藉由指定之金鑰容器`szKeyContainer`會假設包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="00106-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="00106-115">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="00106-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="00106-116">[out]傳回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="00106-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="00106-117">`ppbPublicKeyBlob`參數是由 common language runtime 配置，並傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="00106-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="00106-118">呼叫端必須使用釋放記憶體[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="00106-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="00106-119">[out]傳回的公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="00106-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="00106-120">[in]組件雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="00106-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="00106-121">請參閱 < 備註 > 一節的清單接受的值。</span><span class="sxs-lookup"><span data-stu-id="00106-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="00106-122">[in]保留供未來使用;預設值是 null。</span><span class="sxs-lookup"><span data-stu-id="00106-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00106-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="00106-123">Return Value</span></span>  
 `S_OK` <span data-ttu-id="00106-124">如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="00106-124">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00106-125">備註</span><span class="sxs-lookup"><span data-stu-id="00106-125">Remarks</span></span>  
 <span data-ttu-id="00106-126">中包含的公開金鑰[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="00106-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00106-127">備註</span><span class="sxs-lookup"><span data-stu-id="00106-127">Remarks</span></span>  
 <span data-ttu-id="00106-128">下表顯示可接受的值組`uHashAlgId`參數。</span><span class="sxs-lookup"><span data-stu-id="00106-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="00106-129">名稱</span><span class="sxs-lookup"><span data-stu-id="00106-129">Name</span></span>|<span data-ttu-id="00106-130">值</span><span class="sxs-lookup"><span data-stu-id="00106-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="00106-131">None</span><span class="sxs-lookup"><span data-stu-id="00106-131">None</span></span>|<span data-ttu-id="00106-132">0</span><span class="sxs-lookup"><span data-stu-id="00106-132">0</span></span>|  
|<span data-ttu-id="00106-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="00106-133">SHA-1</span></span>|<span data-ttu-id="00106-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="00106-134">0x8004</span></span>|  
|<span data-ttu-id="00106-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="00106-135">SHA-256</span></span>|<span data-ttu-id="00106-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="00106-136">0x800c</span></span>|  
|<span data-ttu-id="00106-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="00106-137">SHA-384</span></span>|<span data-ttu-id="00106-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="00106-138">0x800d</span></span>|  
|<span data-ttu-id="00106-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="00106-139">SHA-512</span></span>|<span data-ttu-id="00106-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="00106-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00106-141">需求</span><span class="sxs-lookup"><span data-stu-id="00106-141">Requirements</span></span>  
 <span data-ttu-id="00106-142">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00106-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00106-143">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="00106-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="00106-144">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="00106-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="00106-145">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="00106-145">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="00106-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00106-146">See also</span></span>

- [<span data-ttu-id="00106-147">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="00106-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="00106-148">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="00106-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="00106-149">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="00106-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="00106-150">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="00106-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
