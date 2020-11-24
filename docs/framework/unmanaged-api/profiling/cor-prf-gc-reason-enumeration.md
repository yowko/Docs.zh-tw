---
title: COR_PRF_GC_REASON 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
ms.openlocfilehash: f41f00a9699d6fc135ca3b9c0b4b470ca0359279
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682376"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="b39cd-102">COR_PRF_GC_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="b39cd-102">COR_PRF_GC_REASON Enumeration</span></span>

<span data-ttu-id="b39cd-103">指出正在發生之記憶體回收的原因。</span><span class="sxs-lookup"><span data-stu-id="b39cd-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b39cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="b39cd-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="b39cd-105">成員</span><span class="sxs-lookup"><span data-stu-id="b39cd-105">Members</span></span>  
  
|<span data-ttu-id="b39cd-106">member</span><span class="sxs-lookup"><span data-stu-id="b39cd-106">Member</span></span>|<span data-ttu-id="b39cd-107">描述</span><span class="sxs-lookup"><span data-stu-id="b39cd-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="b39cd-108">垃圾收集是由方法所引發 <xref:System.GC.Collect%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b39cd-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="b39cd-109">未指定原因。</span><span class="sxs-lookup"><span data-stu-id="b39cd-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b39cd-110">需求</span><span class="sxs-lookup"><span data-stu-id="b39cd-110">Requirements</span></span>  

 <span data-ttu-id="b39cd-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b39cd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b39cd-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b39cd-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b39cd-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b39cd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b39cd-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b39cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b39cd-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b39cd-115">See also</span></span>

- [<span data-ttu-id="b39cd-116">分析列舉</span><span class="sxs-lookup"><span data-stu-id="b39cd-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
