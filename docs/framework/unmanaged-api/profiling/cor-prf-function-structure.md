---
title: COR_PRF_FUNCTION 結構
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 098aaca8ec318b08c87e30c2a9558b7e64494a4c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581990"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="cface-102">COR_PRF_FUNCTION 結構</span><span class="sxs-lookup"><span data-stu-id="cface-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="cface-103">將其 ID 與其重新編譯版本的 ID 合併在一起，以提供函式的唯一表示法。</span><span class="sxs-lookup"><span data-stu-id="cface-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cface-104">語法</span><span class="sxs-lookup"><span data-stu-id="cface-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="cface-105">成員</span><span class="sxs-lookup"><span data-stu-id="cface-105">Members</span></span>  
  
|<span data-ttu-id="cface-106">成員</span><span class="sxs-lookup"><span data-stu-id="cface-106">Member</span></span>|<span data-ttu-id="cface-107">描述</span><span class="sxs-lookup"><span data-stu-id="cface-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="cface-108">函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cface-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="cface-109">重新編譯的函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cface-109">The ID of the recompiled function.</span></span> <span data-ttu-id="cface-110">值為 0 （零） 表示的函式的原始版本。</span><span class="sxs-lookup"><span data-stu-id="cface-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cface-111">備註</span><span class="sxs-lookup"><span data-stu-id="cface-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cface-112">需求</span><span class="sxs-lookup"><span data-stu-id="cface-112">Requirements</span></span>  
 <span data-ttu-id="cface-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cface-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cface-114">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="cface-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="cface-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cface-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cface-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cface-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cface-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cface-117">See also</span></span>
- [<span data-ttu-id="cface-118">分析結構</span><span class="sxs-lookup"><span data-stu-id="cface-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
