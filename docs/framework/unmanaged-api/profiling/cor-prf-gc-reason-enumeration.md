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
ms.openlocfilehash: 13740920e8db5d44b71cd3c324742945c64b3e59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498956"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="56a35-102">COR_PRF_GC_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="56a35-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="56a35-103">指出正在發生之記憶體回收的原因。</span><span class="sxs-lookup"><span data-stu-id="56a35-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56a35-104">語法</span><span class="sxs-lookup"><span data-stu-id="56a35-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="56a35-105">成員</span><span class="sxs-lookup"><span data-stu-id="56a35-105">Members</span></span>  
  
|<span data-ttu-id="56a35-106">成員</span><span class="sxs-lookup"><span data-stu-id="56a35-106">Member</span></span>|<span data-ttu-id="56a35-107">描述</span><span class="sxs-lookup"><span data-stu-id="56a35-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="56a35-108">記憶體回收所引起的<xref:System.GC.Collect%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="56a35-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="56a35-109">未指定原因。</span><span class="sxs-lookup"><span data-stu-id="56a35-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56a35-110">需求</span><span class="sxs-lookup"><span data-stu-id="56a35-110">Requirements</span></span>  
 <span data-ttu-id="56a35-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56a35-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56a35-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="56a35-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56a35-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56a35-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56a35-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56a35-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a35-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56a35-115">See also</span></span>
- [<span data-ttu-id="56a35-116">分析列舉</span><span class="sxs-lookup"><span data-stu-id="56a35-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
