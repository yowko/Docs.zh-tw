---
title: StrongNameKeyGenEx 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 736e537a3f773acbd61dbad013b8dfb7cc429076
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666022"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="e6cf5-102">StrongNameKeyGenEx 函式</span><span class="sxs-lookup"><span data-stu-id="e6cf5-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="e6cf5-103">會產生新公用/私密金鑰組以指定的金鑰大小，用於強式名稱。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="e6cf5-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-104">This function has been deprecated.</span></span> <span data-ttu-id="e6cf5-105">使用[iclrstrongname:: Strongnamekeygenex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6cf5-106">語法</span><span class="sxs-lookup"><span data-stu-id="e6cf5-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6cf5-107">參數</span><span class="sxs-lookup"><span data-stu-id="e6cf5-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="e6cf5-108">[in]要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-108">[in] The requested key container name.</span></span> <span data-ttu-id="e6cf5-109">`wszKeyContainer` 必須是空字串，或為 null 來產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e6cf5-110">[in]指定是否要保留已註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="e6cf5-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="e6cf5-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="e6cf5-112">0x00000000-時使用`wszKeyContainer`以產生暫時的金鑰容器名稱為 null。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="e6cf5-113">0x00000001 (`SN_LEAVE_KEY`)-指定應該向左註冊金鑰。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="e6cf5-114">[in]要求的大小，以位元的金鑰。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="e6cf5-115">[out]傳回的 public/private 金鑰組。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="e6cf5-116">[out]大小，以位元組為單位的`ppbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6cf5-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="e6cf5-117">Return Value</span></span>  
 <span data-ttu-id="e6cf5-118">`true` 如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6cf5-119">備註</span><span class="sxs-lookup"><span data-stu-id="e6cf5-119">Remarks</span></span>  
 <span data-ttu-id="e6cf5-120">.NET framework 1.0 和 1.1 版需要`dwKeySize`簽署組件以強式名稱; 1024 位元的 2.0 版新增 2048年位元金鑰的支援。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="e6cf5-121">擷取索引鍵之後，您應該呼叫[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式來釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="e6cf5-122">如果`StrongNameKeyGenEx`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6cf5-123">需求</span><span class="sxs-lookup"><span data-stu-id="e6cf5-123">Requirements</span></span>  
 <span data-ttu-id="e6cf5-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6cf5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6cf5-125">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e6cf5-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e6cf5-126">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e6cf5-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6cf5-127">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6cf5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6cf5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6cf5-128">See also</span></span>

- [<span data-ttu-id="e6cf5-129">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="e6cf5-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="e6cf5-130">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="e6cf5-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="e6cf5-131">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="e6cf5-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
