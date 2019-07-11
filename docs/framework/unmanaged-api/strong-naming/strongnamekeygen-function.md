---
title: StrongNameKeyGen 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74445b03e78ff68426f60c3e306d9151d0ba288a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781000"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="75e10-102">StrongNameKeyGen 函式</span><span class="sxs-lookup"><span data-stu-id="75e10-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="75e10-103">建立將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="75e10-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="75e10-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="75e10-104">This function has been deprecated.</span></span> <span data-ttu-id="75e10-105">使用[iclrstrongname:: Strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="75e10-105">Use the [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75e10-106">語法</span><span class="sxs-lookup"><span data-stu-id="75e10-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75e10-107">參數</span><span class="sxs-lookup"><span data-stu-id="75e10-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="75e10-108">[in]要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="75e10-108">[in] The requested key container name.</span></span> <span data-ttu-id="75e10-109">`wszKeyContainer` 必須是空字串，或為 null 來產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="75e10-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="75e10-110">[in]指定是否要保留已註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="75e10-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="75e10-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="75e10-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="75e10-112">0x00000000-時使用`wszKeyContainer`以產生暫時的金鑰容器名稱為 null。</span><span class="sxs-lookup"><span data-stu-id="75e10-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="75e10-113">0x00000001 (`SN_LEAVE_KEY`)-指定應該向左註冊金鑰。</span><span class="sxs-lookup"><span data-stu-id="75e10-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="75e10-114">[out]傳回的 public/private 金鑰組。</span><span class="sxs-lookup"><span data-stu-id="75e10-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="75e10-115">[out]大小，以位元組為單位的`ppbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="75e10-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75e10-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="75e10-116">Return Value</span></span>  
 <span data-ttu-id="75e10-117">`true` 如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="75e10-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75e10-118">備註</span><span class="sxs-lookup"><span data-stu-id="75e10-118">Remarks</span></span>  
 <span data-ttu-id="75e10-119">`StrongNameKeyGen`函式會建立為 1024年位元金鑰。</span><span class="sxs-lookup"><span data-stu-id="75e10-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="75e10-120">擷取索引鍵之後，您應該呼叫[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式來釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="75e10-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="75e10-121">如果`StrongNameKeyGen`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="75e10-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75e10-122">需求</span><span class="sxs-lookup"><span data-stu-id="75e10-122">Requirements</span></span>  
 <span data-ttu-id="75e10-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75e10-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75e10-124">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="75e10-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="75e10-125">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="75e10-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75e10-126">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75e10-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e10-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75e10-127">See also</span></span>

- [<span data-ttu-id="75e10-128">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="75e10-128">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="75e10-129">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="75e10-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="75e10-130">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="75e10-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
