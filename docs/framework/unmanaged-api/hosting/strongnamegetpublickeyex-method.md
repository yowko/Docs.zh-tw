---
title: "StrongNameGetPublicKeyEx 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2.StrongNameGetPublicKeyEx
api_location: mscoree.dll
api_type: COM
f1_keywords: StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f39c5c948d43fd0e9387c1cc0319a46d25ec86ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="ab87d-102">StrongNameGetPublicKeyEx 方法</span><span class="sxs-lookup"><span data-stu-id="ab87d-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="ab87d-103">公開/私密金鑰組，從取得的公開金鑰，並指定雜湊演算法和簽章演算法。</span><span class="sxs-lookup"><span data-stu-id="ab87d-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab87d-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab87d-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ab87d-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab87d-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="ab87d-106">[in]包含 public/private 金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="ab87d-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="ab87d-107">如果`pbKeyBlob`為 null，`szKeyContainer`必須指定有效的容器內的密碼編譯服務提供者 (CSP)。</span><span class="sxs-lookup"><span data-stu-id="ab87d-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="ab87d-108">在此情況下，`StrongNameGetPublicKeyEx`方法會從儲存在容器中的金鑰組擷取公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="ab87d-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="ab87d-109">如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="ab87d-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ab87d-110">索引鍵必須是 1024年位元用於 Rivest-shamir-adleman (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="ab87d-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ab87d-111">此時會支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="ab87d-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ab87d-112">[in]公開/私密金鑰組指標。</span><span class="sxs-lookup"><span data-stu-id="ab87d-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ab87d-113">此配對的格式建立 win32`CryptExportKey`函式。</span><span class="sxs-lookup"><span data-stu-id="ab87d-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ab87d-114">如果`pbKeyBlob`是 null，所指定的金鑰容器`szKeyContainer`假設為包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="ab87d-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ab87d-115">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="ab87d-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ab87d-116">[out]傳回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="ab87d-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="ab87d-117">`ppbPublicKeyBlob`參數是由 common language runtime 配置並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="ab87d-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="ab87d-118">呼叫端必須釋放的記憶體使用[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ab87d-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ab87d-119">[out]傳回的公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="ab87d-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="ab87d-120">[in]組件的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="ab87d-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="ab87d-121">請參閱 < 備註 > 一節清單的可接受的值。</span><span class="sxs-lookup"><span data-stu-id="ab87d-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="ab87d-122">[in]保留供未來使用。預設值是 null。</span><span class="sxs-lookup"><span data-stu-id="ab87d-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab87d-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="ab87d-123">Return Value</span></span>  
 <span data-ttu-id="ab87d-124">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="ab87d-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab87d-125">備註</span><span class="sxs-lookup"><span data-stu-id="ab87d-125">Remarks</span></span>  
 <span data-ttu-id="ab87d-126">中包含公用金鑰[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="ab87d-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab87d-127">備註</span><span class="sxs-lookup"><span data-stu-id="ab87d-127">Remarks</span></span>  
 <span data-ttu-id="ab87d-128">下表顯示可接受的值組`uHashAlgId`參數。</span><span class="sxs-lookup"><span data-stu-id="ab87d-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="ab87d-129">名稱</span><span class="sxs-lookup"><span data-stu-id="ab87d-129">Name</span></span>|<span data-ttu-id="ab87d-130">值</span><span class="sxs-lookup"><span data-stu-id="ab87d-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="ab87d-131">無</span><span class="sxs-lookup"><span data-stu-id="ab87d-131">None</span></span>|<span data-ttu-id="ab87d-132">0</span><span class="sxs-lookup"><span data-stu-id="ab87d-132">0</span></span>|  
|<span data-ttu-id="ab87d-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="ab87d-133">SHA-1</span></span>|<span data-ttu-id="ab87d-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="ab87d-134">0x8004</span></span>|  
|<span data-ttu-id="ab87d-135">SHA 256</span><span class="sxs-lookup"><span data-stu-id="ab87d-135">SHA-256</span></span>|<span data-ttu-id="ab87d-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="ab87d-136">0x800c</span></span>|  
|<span data-ttu-id="ab87d-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="ab87d-137">SHA-384</span></span>|<span data-ttu-id="ab87d-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="ab87d-138">0x800d</span></span>|  
|<span data-ttu-id="ab87d-139">SHA 512</span><span class="sxs-lookup"><span data-stu-id="ab87d-139">SHA-512</span></span>|<span data-ttu-id="ab87d-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="ab87d-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab87d-141">需求</span><span class="sxs-lookup"><span data-stu-id="ab87d-141">Requirements</span></span>  
 <span data-ttu-id="ab87d-142">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab87d-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab87d-143">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ab87d-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ab87d-144">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ab87d-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab87d-145">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab87d-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab87d-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab87d-146">See Also</span></span>  
 [<span data-ttu-id="ab87d-147">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="ab87d-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="ab87d-148">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="ab87d-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="ab87d-149">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="ab87d-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="ab87d-150">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="ab87d-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
