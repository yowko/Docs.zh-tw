---
title: "StrongNameHashSize 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 20a0d5fc284dde7b127f1f177a448a95701ac8b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="31b5b-102">StrongNameHashSize 函式</span><span class="sxs-lookup"><span data-stu-id="31b5b-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="31b5b-103">取得所需的雜湊，並使用指定的雜湊演算法的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="31b5b-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="31b5b-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="31b5b-104">This function has been deprecated.</span></span> <span data-ttu-id="31b5b-105">使用[iclrstrongname:: Strongnamehashsize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="31b5b-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31b5b-106">語法</span><span class="sxs-lookup"><span data-stu-id="31b5b-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31b5b-107">參數</span><span class="sxs-lookup"><span data-stu-id="31b5b-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="31b5b-108">[in]雜湊演算法，用來計算的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="31b5b-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="31b5b-109">[out]傳回的緩衝區大小，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="31b5b-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31b5b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="31b5b-110">Return Value</span></span>  
 <span data-ttu-id="31b5b-111">`true`如果成功地完成。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="31b5b-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31b5b-112">備註</span><span class="sxs-lookup"><span data-stu-id="31b5b-112">Remarks</span></span>  
 <span data-ttu-id="31b5b-113">如果`StrongNameHashSize`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="31b5b-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31b5b-114">需求</span><span class="sxs-lookup"><span data-stu-id="31b5b-114">Requirements</span></span>  
 <span data-ttu-id="31b5b-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31b5b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31b5b-116">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="31b5b-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="31b5b-117">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="31b5b-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31b5b-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31b5b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b5b-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="31b5b-119">See Also</span></span>  
 [<span data-ttu-id="31b5b-120">StrongNameHashSize 方法</span><span class="sxs-lookup"><span data-stu-id="31b5b-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)  
 [<span data-ttu-id="31b5b-121">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="31b5b-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
