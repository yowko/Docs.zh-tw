---
title: "COR_PRF_FUNCTION 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FUNCTION
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FUNCTION
helpviewer_keywords: COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 15ef81f07438a7cc18f7a131ee8cf9c50c47eb6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunction-structure"></a><span data-ttu-id="898fc-102">COR_PRF_FUNCTION 結構</span><span class="sxs-lookup"><span data-stu-id="898fc-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="898fc-103">將其 ID 與其重新編譯版本的 ID 合併在一起，以提供函式的唯一表示法。</span><span class="sxs-lookup"><span data-stu-id="898fc-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="898fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="898fc-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="898fc-105">成員</span><span class="sxs-lookup"><span data-stu-id="898fc-105">Members</span></span>  
  
|<span data-ttu-id="898fc-106">成員</span><span class="sxs-lookup"><span data-stu-id="898fc-106">Member</span></span>|<span data-ttu-id="898fc-107">描述</span><span class="sxs-lookup"><span data-stu-id="898fc-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="898fc-108">函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="898fc-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="898fc-109">重新編譯函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="898fc-109">The ID of the recompiled function.</span></span> <span data-ttu-id="898fc-110">值為 0 （零） 表示函式的原始版本。</span><span class="sxs-lookup"><span data-stu-id="898fc-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="898fc-111">備註</span><span class="sxs-lookup"><span data-stu-id="898fc-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="898fc-112">需求</span><span class="sxs-lookup"><span data-stu-id="898fc-112">Requirements</span></span>  
 <span data-ttu-id="898fc-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="898fc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="898fc-114">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="898fc-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="898fc-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="898fc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="898fc-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="898fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="898fc-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="898fc-117">See Also</span></span>  
 [<span data-ttu-id="898fc-118">分析結構</span><span class="sxs-lookup"><span data-stu-id="898fc-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
