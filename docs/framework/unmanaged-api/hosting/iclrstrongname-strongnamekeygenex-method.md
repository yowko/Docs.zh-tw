---
title: ICLRStrongName::StrongNameKeyGenEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b04f51040e32aa38fbd84c46e1a3b55af7ec0a7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497453"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="38504-102">ICLRStrongName::StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="38504-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="38504-103">會產生新公用/私密金鑰組以指定的金鑰大小，用於強式名稱。</span><span class="sxs-lookup"><span data-stu-id="38504-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38504-104">語法</span><span class="sxs-lookup"><span data-stu-id="38504-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38504-105">參數</span><span class="sxs-lookup"><span data-stu-id="38504-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="38504-106">[in]要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="38504-106">[in] The requested key container name.</span></span> <span data-ttu-id="38504-107">`wszKeyContainer` 必須是非空白字串或 null 來產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="38504-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="38504-108">[in]值，指定是否要保留已註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="38504-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="38504-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="38504-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="38504-110">0x00000000-時使用`wszKeyContainer`以產生暫時的金鑰容器名稱為 null。</span><span class="sxs-lookup"><span data-stu-id="38504-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="38504-111">0x00000001 (`SN_LEAVE_KEY`)-指定應該向左註冊金鑰。</span><span class="sxs-lookup"><span data-stu-id="38504-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="38504-112">[in]要求的大小，以位元的金鑰。</span><span class="sxs-lookup"><span data-stu-id="38504-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="38504-113">[out]傳回的 public/private 金鑰組。</span><span class="sxs-lookup"><span data-stu-id="38504-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="38504-114">[out]大小，以位元組為單位的`ppbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="38504-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38504-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="38504-115">Return Value</span></span>  
 <span data-ttu-id="38504-116">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="38504-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38504-117">備註</span><span class="sxs-lookup"><span data-stu-id="38504-117">Remarks</span></span>  
 <span data-ttu-id="38504-118">.NET framework 1.0 和 1.1 版需要`dwKeySize`簽署組件以強式名稱; 1024 位元的 2.0 版新增 2048年位元金鑰的支援。</span><span class="sxs-lookup"><span data-stu-id="38504-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="38504-119">擷取索引鍵之後，您應該呼叫[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="38504-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38504-120">需求</span><span class="sxs-lookup"><span data-stu-id="38504-120">Requirements</span></span>  
 <span data-ttu-id="38504-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38504-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38504-122">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="38504-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="38504-123">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="38504-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38504-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38504-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38504-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38504-125">See also</span></span>
- [<span data-ttu-id="38504-126">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="38504-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="38504-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="38504-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
