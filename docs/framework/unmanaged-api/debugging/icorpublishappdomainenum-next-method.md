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
ms.openlocfilehash: 6f7f400c51ded0b98c0c2286cb6f90bbd77e47d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178403"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="6f41b-102">ICorPublishAppDomainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="6f41b-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="6f41b-103">從當前位置開始獲取進程中當前存在的指定數量的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="6f41b-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f41b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f41b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f41b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f41b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6f41b-106">[在]要檢索的元素數。</span><span class="sxs-lookup"><span data-stu-id="6f41b-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="6f41b-107">[出]指向檢索到[的 ICorPublishAppDomain](icorpublishappdomain-interface.md)物件的陣列的指標，每個物件都表示一個應用程式域。</span><span class="sxs-lookup"><span data-stu-id="6f41b-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6f41b-108">[出]指向實際返回的應用程式域數的指標。</span><span class="sxs-lookup"><span data-stu-id="6f41b-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="6f41b-109">此值可以是 null（如果是`celt`1）。</span><span class="sxs-lookup"><span data-stu-id="6f41b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f41b-110">需求</span><span class="sxs-lookup"><span data-stu-id="6f41b-110">Requirements</span></span>  
 <span data-ttu-id="6f41b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f41b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f41b-112">**標題：** 科爾普布.idl， 科爾普布.h</span><span class="sxs-lookup"><span data-stu-id="6f41b-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6f41b-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f41b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f41b-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f41b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f41b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f41b-115">See also</span></span>

- [<span data-ttu-id="6f41b-116">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="6f41b-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
