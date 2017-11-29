---
title: "COR_PRF_GC_REASON 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_REASON
helpviewer_keywords: COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a5797c3e629bc87caf40b187bba47bc1cffbfdf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="16c67-102">COR_PRF_GC_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="16c67-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="16c67-103">指出正在發生之記憶體回收的原因。</span><span class="sxs-lookup"><span data-stu-id="16c67-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16c67-104">語法</span><span class="sxs-lookup"><span data-stu-id="16c67-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="16c67-105">成員</span><span class="sxs-lookup"><span data-stu-id="16c67-105">Members</span></span>  
  
|<span data-ttu-id="16c67-106">成員</span><span class="sxs-lookup"><span data-stu-id="16c67-106">Member</span></span>|<span data-ttu-id="16c67-107">說明</span><span class="sxs-lookup"><span data-stu-id="16c67-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="16c67-108">記憶體回收所引起的<xref:System.GC.Collect%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="16c67-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="16c67-109">未指定原因。</span><span class="sxs-lookup"><span data-stu-id="16c67-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16c67-110">需求</span><span class="sxs-lookup"><span data-stu-id="16c67-110">Requirements</span></span>  
 <span data-ttu-id="16c67-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16c67-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c67-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="16c67-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="16c67-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16c67-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16c67-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c67-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c67-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16c67-115">See Also</span></span>  
 [<span data-ttu-id="16c67-116">分析列舉</span><span class="sxs-lookup"><span data-stu-id="16c67-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
