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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: daf97f25b1adc30b173fcd81812a4b197915cdd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196940"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="88414-102">COR_PRF_GC_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="88414-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="88414-103">指出正在發生之記憶體回收的原因。</span><span class="sxs-lookup"><span data-stu-id="88414-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88414-104">語法</span><span class="sxs-lookup"><span data-stu-id="88414-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="88414-105">成員</span><span class="sxs-lookup"><span data-stu-id="88414-105">Members</span></span>  
  
|<span data-ttu-id="88414-106">成員</span><span class="sxs-lookup"><span data-stu-id="88414-106">Member</span></span>|<span data-ttu-id="88414-107">描述</span><span class="sxs-lookup"><span data-stu-id="88414-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="88414-108">記憶體回收所引起的<xref:System.GC.Collect%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="88414-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="88414-109">未指定原因。</span><span class="sxs-lookup"><span data-stu-id="88414-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88414-110">需求</span><span class="sxs-lookup"><span data-stu-id="88414-110">Requirements</span></span>  
 <span data-ttu-id="88414-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88414-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88414-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="88414-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="88414-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88414-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="88414-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="88414-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="88414-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88414-115">See also</span></span>

- [<span data-ttu-id="88414-116">分析列舉</span><span class="sxs-lookup"><span data-stu-id="88414-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
