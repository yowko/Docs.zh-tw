---
title: COR_PRF_CLAUSE_TYPE 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
ms.openlocfilehash: 94230cbad95ff0a5d4234c27aa5d1d56ac5be9bb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428407"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="b9eb2-102">COR_PRF_CLAUSE_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="b9eb2-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="b9eb2-103">指出剛輸入或留下的程式碼的 exception 子句類型。</span><span class="sxs-lookup"><span data-stu-id="b9eb2-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9eb2-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9eb2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="b9eb2-105">Members</span><span class="sxs-lookup"><span data-stu-id="b9eb2-105">Members</span></span>  
  
|<span data-ttu-id="b9eb2-106">成員</span><span class="sxs-lookup"><span data-stu-id="b9eb2-106">Member</span></span>|<span data-ttu-id="b9eb2-107">描述</span><span class="sxs-lookup"><span data-stu-id="b9eb2-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="b9eb2-108">The exception clause is not valid.</span><span class="sxs-lookup"><span data-stu-id="b9eb2-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="b9eb2-109">The exception clause is a filter expression.</span><span class="sxs-lookup"><span data-stu-id="b9eb2-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="b9eb2-110">The exception clause is a `catch` statement.</span><span class="sxs-lookup"><span data-stu-id="b9eb2-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="b9eb2-111">The exception clause is a `finally` statement.</span><span class="sxs-lookup"><span data-stu-id="b9eb2-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9eb2-112">需求</span><span class="sxs-lookup"><span data-stu-id="b9eb2-112">Requirements</span></span>  
 <span data-ttu-id="b9eb2-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9eb2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9eb2-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9eb2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9eb2-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9eb2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9eb2-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9eb2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9eb2-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9eb2-117">See also</span></span>

- [<span data-ttu-id="b9eb2-118">分析列舉</span><span class="sxs-lookup"><span data-stu-id="b9eb2-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
