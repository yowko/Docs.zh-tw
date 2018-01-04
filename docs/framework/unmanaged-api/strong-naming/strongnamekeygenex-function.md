---
title: "StrongNameKeyGenEx 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyGenEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyGenEx
helpviewer_keywords: StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae564f7c4e8333e33b2f2f6229034c3a1396a687
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="64df9-102">StrongNameKeyGenEx 函式</span><span class="sxs-lookup"><span data-stu-id="64df9-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="64df9-103">會產生新的公用/私用金鑰組與指定的金鑰大小，強式名稱使用。</span><span class="sxs-lookup"><span data-stu-id="64df9-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="64df9-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="64df9-104">This function has been deprecated.</span></span> <span data-ttu-id="64df9-105">使用[iclrstrongname:: Strongnamekeygenex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="64df9-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64df9-106">語法</span><span class="sxs-lookup"><span data-stu-id="64df9-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64df9-107">參數</span><span class="sxs-lookup"><span data-stu-id="64df9-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="64df9-108">[in]要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="64df9-108">[in] The requested key container name.</span></span> <span data-ttu-id="64df9-109">`wszKeyContainer`必須是非空白字串，或 null 以產生暫時的名稱。</span><span class="sxs-lookup"><span data-stu-id="64df9-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="64df9-110">[in]指定是否要保留已註冊的鍵。</span><span class="sxs-lookup"><span data-stu-id="64df9-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="64df9-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="64df9-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="64df9-112">0x00000000-時使用`wszKeyContainer`以產生暫時的金鑰容器名稱為 null。</span><span class="sxs-lookup"><span data-stu-id="64df9-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="64df9-113">0x00000001 (`SN_LEAVE_KEY`)-指定應該向左登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="64df9-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="64df9-114">[in]要求的金鑰，以位元大小。</span><span class="sxs-lookup"><span data-stu-id="64df9-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="64df9-115">[out]傳回的 public/private 金鑰組。</span><span class="sxs-lookup"><span data-stu-id="64df9-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="64df9-116">[out]大小，以位元組為單位的`ppbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="64df9-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64df9-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="64df9-117">Return Value</span></span>  
 <span data-ttu-id="64df9-118">`true`如果成功地完成。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="64df9-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64df9-119">備註</span><span class="sxs-lookup"><span data-stu-id="64df9-119">Remarks</span></span>  
 <span data-ttu-id="64df9-120">需要.NET framework 1.0 和 1.1 版`dwKeySize`1024 個位元簽署為強式名稱; 組件版本 2.0 加入 2048年位元金鑰的支援。</span><span class="sxs-lookup"><span data-stu-id="64df9-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="64df9-121">擷取索引鍵之後，您應該呼叫[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="64df9-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="64df9-122">如果`StrongNameKeyGenEx`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="64df9-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64df9-123">需求</span><span class="sxs-lookup"><span data-stu-id="64df9-123">Requirements</span></span>  
 <span data-ttu-id="64df9-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64df9-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64df9-125">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="64df9-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="64df9-126">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="64df9-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64df9-127">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64df9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64df9-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="64df9-128">See Also</span></span>  
 [<span data-ttu-id="64df9-129">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="64df9-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="64df9-130">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="64df9-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="64df9-131">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="64df9-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
