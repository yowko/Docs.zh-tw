---
title: ICorPublishAppDomainEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1492c9eac9d647c2b71c47cf758265152783d991
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54673879"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="f833d-102">ICorPublishAppDomainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="f833d-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="f833d-103">取得指定的數目的目前存在的應用程式定義域在過程中，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="f833d-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f833d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f833d-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f833d-105">參數</span><span class="sxs-lookup"><span data-stu-id="f833d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f833d-106">[in]要擷取的元素數目。</span><span class="sxs-lookup"><span data-stu-id="f833d-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="f833d-107">[out]擷取陣列的指標[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)每一個都代表應用程式定義域的物件。</span><span class="sxs-lookup"><span data-stu-id="f833d-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f833d-108">[out]指標的實際傳回的應用程式定義域數目。</span><span class="sxs-lookup"><span data-stu-id="f833d-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="f833d-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="f833d-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f833d-110">需求</span><span class="sxs-lookup"><span data-stu-id="f833d-110">Requirements</span></span>  
 <span data-ttu-id="f833d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f833d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f833d-112">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f833d-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f833d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f833d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f833d-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f833d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f833d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f833d-115">See also</span></span>
- [<span data-ttu-id="f833d-116">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f833d-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
