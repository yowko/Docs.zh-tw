---
title: ICLRStrongName::StrongNameKeyGen 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abeb731ecd66e4412f904b085abcfc7b5b3a3c4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169776"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="fce22-102">ICLRStrongName::StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="fce22-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="fce22-103">建立將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="fce22-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fce22-104">語法</span><span class="sxs-lookup"><span data-stu-id="fce22-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fce22-105">參數</span><span class="sxs-lookup"><span data-stu-id="fce22-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="fce22-106">[in]要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="fce22-106">[in] The requested key container name.</span></span> <span data-ttu-id="fce22-107">`wszKeyContainer` 必須是非空白字串或 null 來產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="fce22-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fce22-108">[in]值，指定是否要保留已註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="fce22-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="fce22-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="fce22-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="fce22-110">0x00000000-時使用`wszKeyContainer`以產生暫時的金鑰容器名稱為 null。</span><span class="sxs-lookup"><span data-stu-id="fce22-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="fce22-111">0x00000001 (`SN_LEAVE_KEY`)-指定應該向左註冊金鑰。</span><span class="sxs-lookup"><span data-stu-id="fce22-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="fce22-112">[out]傳回的 public/private 金鑰組。</span><span class="sxs-lookup"><span data-stu-id="fce22-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="fce22-113">[out]大小，以位元組為單位的`ppbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="fce22-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fce22-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="fce22-114">Return Value</span></span>  
 <span data-ttu-id="fce22-115">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="fce22-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fce22-116">備註</span><span class="sxs-lookup"><span data-stu-id="fce22-116">Remarks</span></span>  
 <span data-ttu-id="fce22-117">[Iclrstrongname:: Strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)方法會建立為 1024年位元金鑰。</span><span class="sxs-lookup"><span data-stu-id="fce22-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="fce22-118">擷取索引鍵之後，您應該呼叫[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="fce22-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fce22-119">需求</span><span class="sxs-lookup"><span data-stu-id="fce22-119">Requirements</span></span>  
 <span data-ttu-id="fce22-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fce22-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fce22-121">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fce22-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fce22-122">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fce22-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fce22-123">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fce22-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce22-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fce22-124">See also</span></span>

- [<span data-ttu-id="fce22-125">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="fce22-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="fce22-126">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="fce22-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
