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
ms.openlocfilehash: c5ac38005410ae6ed9c2f4160e926987791ad604
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421211"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="af5ef-102">ICorPublishAppDomainEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="af5ef-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="af5ef-103">從目前的位置開始，取得目前存在於進程中的指定應用程式域數目。</span><span class="sxs-lookup"><span data-stu-id="af5ef-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af5ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="af5ef-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af5ef-105">參數</span><span class="sxs-lookup"><span data-stu-id="af5ef-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="af5ef-106">在要抓取的元素數目。</span><span class="sxs-lookup"><span data-stu-id="af5ef-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="af5ef-107">脫銷已抓取[ICorPublishAppDomain](icorpublishappdomain-interface.md)物件之陣列的指標，每個物件都代表一個應用程式域。</span><span class="sxs-lookup"><span data-stu-id="af5ef-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="af5ef-108">脫銷實際傳回的應用程式域數的指標。</span><span class="sxs-lookup"><span data-stu-id="af5ef-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="af5ef-109">如果是一個，這個值可能會是 null `celt` 。</span><span class="sxs-lookup"><span data-stu-id="af5ef-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af5ef-110">需求</span><span class="sxs-lookup"><span data-stu-id="af5ef-110">Requirements</span></span>  
 <span data-ttu-id="af5ef-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af5ef-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af5ef-112">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="af5ef-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="af5ef-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af5ef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af5ef-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af5ef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af5ef-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af5ef-115">See also</span></span>

- [<span data-ttu-id="af5ef-116">ICorPublishAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="af5ef-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
