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
ms.openlocfilehash: 0553d8b07e3a16dc31474b5470ba2dd8ba365cb2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140510"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="a58a9-102">ICorPublishAppDomainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="a58a9-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="a58a9-103">從目前的位置開始，取得目前存在於進程中的指定應用程式域數目。</span><span class="sxs-lookup"><span data-stu-id="a58a9-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a58a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="a58a9-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a58a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="a58a9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a58a9-106">在要抓取的元素數目。</span><span class="sxs-lookup"><span data-stu-id="a58a9-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="a58a9-107">脫銷已抓取[ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)物件之陣列的指標，每個物件都代表一個應用程式域。</span><span class="sxs-lookup"><span data-stu-id="a58a9-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a58a9-108">脫銷實際傳回的應用程式域數的指標。</span><span class="sxs-lookup"><span data-stu-id="a58a9-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="a58a9-109">如果 `celt` 是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="a58a9-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a58a9-110">需求</span><span class="sxs-lookup"><span data-stu-id="a58a9-110">Requirements</span></span>  
 <span data-ttu-id="a58a9-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a58a9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a58a9-112">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="a58a9-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a58a9-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a58a9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a58a9-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a58a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a58a9-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="a58a9-115">See also</span></span>

- [<span data-ttu-id="a58a9-116">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a58a9-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
