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
ms.openlocfilehash: c8866e98be0dd064138acdf5e0f6fb9c339fb3d2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790640"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="0ce28-102">ICorPublishAppDomainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="0ce28-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="0ce28-103">從目前的位置開始，取得目前存在於進程中的指定應用程式域數目。</span><span class="sxs-lookup"><span data-stu-id="0ce28-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ce28-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ce28-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ce28-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ce28-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0ce28-106">在要抓取的元素數目。</span><span class="sxs-lookup"><span data-stu-id="0ce28-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="0ce28-107">脫銷已抓取[ICorPublishAppDomain](icorpublishappdomain-interface.md)物件之陣列的指標，每個物件都代表一個應用程式域。</span><span class="sxs-lookup"><span data-stu-id="0ce28-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0ce28-108">脫銷實際傳回的應用程式域數的指標。</span><span class="sxs-lookup"><span data-stu-id="0ce28-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="0ce28-109">如果 `celt` 為 null，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="0ce28-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ce28-110">需求</span><span class="sxs-lookup"><span data-stu-id="0ce28-110">Requirements</span></span>  
 <span data-ttu-id="0ce28-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ce28-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ce28-112">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="0ce28-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0ce28-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ce28-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ce28-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ce28-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce28-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ce28-115">See also</span></span>

- [<span data-ttu-id="0ce28-116">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="0ce28-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
