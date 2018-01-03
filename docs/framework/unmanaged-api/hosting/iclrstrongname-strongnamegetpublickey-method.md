---
title: "ICLRStrongName::StrongNameGetPublicKey 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameGetPublicKey
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a639644405ce215a373dadf248e9a0e1a5558ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="da0d4-102">ICLRStrongName::StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="da0d4-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="da0d4-103">取得從公開/私密金鑰組的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="da0d4-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="da0d4-104">密碼編譯服務提供者 (CSP) 內的金鑰容器名稱，或是為未經處理位元組的集合，您可以提供的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="da0d4-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da0d4-105">語法</span><span class="sxs-lookup"><span data-stu-id="da0d4-105">Syntax</span></span>  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da0d4-106">參數</span><span class="sxs-lookup"><span data-stu-id="da0d4-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="da0d4-107">[in]包含 public/private 金鑰組的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="da0d4-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="da0d4-108">如果`pbKeyBlob`為 null，`szKeyContainer`必須指定 CSP 內是有效的容器。</span><span class="sxs-lookup"><span data-stu-id="da0d4-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="da0d4-109">在此情況下， [iclrstrongname:: Strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)方法會從儲存在容器中的金鑰組擷取公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="da0d4-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="da0d4-110">如果`pbKeyBlob`不是 null，金鑰組會假設要包含在索引鍵二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="da0d4-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="da0d4-111">索引鍵必須是 1024年位元用於 Rivest-shamir-adleman (RSA) 簽署金鑰。</span><span class="sxs-lookup"><span data-stu-id="da0d4-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="da0d4-112">此時會支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="da0d4-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="da0d4-113">[in]公開/私密金鑰組指標。</span><span class="sxs-lookup"><span data-stu-id="da0d4-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="da0d4-114">此配對的格式建立 win32`CryptExportKey`函式。</span><span class="sxs-lookup"><span data-stu-id="da0d4-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="da0d4-115">如果`pbKeyBlob`是 null，所指定的金鑰容器`szKeyContainer`假設為包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="da0d4-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="da0d4-116">[in]大小，以位元組為單位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="da0d4-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="da0d4-117">[out]傳回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="da0d4-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="da0d4-118">`ppbPublicKeyBlob`參數是由 common language runtime 配置並傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="da0d4-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="da0d4-119">呼叫端必須釋放的記憶體使用[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="da0d4-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="da0d4-120">[out]傳回的公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="da0d4-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da0d4-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="da0d4-121">Return Value</span></span>  
 <span data-ttu-id="da0d4-122">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="da0d4-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da0d4-123">備註</span><span class="sxs-lookup"><span data-stu-id="da0d4-123">Remarks</span></span>  
 <span data-ttu-id="da0d4-124">中包含公用金鑰[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="da0d4-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da0d4-125">需求</span><span class="sxs-lookup"><span data-stu-id="da0d4-125">Requirements</span></span>  
 <span data-ttu-id="da0d4-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da0d4-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da0d4-127">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="da0d4-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="da0d4-128">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="da0d4-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da0d4-129">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da0d4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da0d4-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="da0d4-130">See Also</span></span>  
 [<span data-ttu-id="da0d4-131">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="da0d4-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="da0d4-132">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="da0d4-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="da0d4-133">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="da0d4-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
