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
ms.openlocfilehash: edf5d61baae28a82aff0d0bd32d1d900085ac375
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867317"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="a4899-102">COR_PRF_CLAUSE_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="a4899-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="a4899-103">指出剛輸入或留下的程式碼的 exception 子句類型。</span><span class="sxs-lookup"><span data-stu-id="a4899-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4899-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4899-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="a4899-105">Members</span><span class="sxs-lookup"><span data-stu-id="a4899-105">Members</span></span>  
  
|<span data-ttu-id="a4899-106">成員</span><span class="sxs-lookup"><span data-stu-id="a4899-106">Member</span></span>|<span data-ttu-id="a4899-107">描述</span><span class="sxs-lookup"><span data-stu-id="a4899-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="a4899-108">例外狀況子句無效。</span><span class="sxs-lookup"><span data-stu-id="a4899-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="a4899-109">Exception 子句是一個篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="a4899-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="a4899-110">Exception 子句是 `catch` 語句。</span><span class="sxs-lookup"><span data-stu-id="a4899-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="a4899-111">Exception 子句是 `finally` 語句。</span><span class="sxs-lookup"><span data-stu-id="a4899-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4899-112">需求</span><span class="sxs-lookup"><span data-stu-id="a4899-112">Requirements</span></span>  
 <span data-ttu-id="a4899-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4899-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4899-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4899-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a4899-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4899-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4899-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4899-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4899-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a4899-117">See also</span></span>

- [<span data-ttu-id="a4899-118">分析列舉</span><span class="sxs-lookup"><span data-stu-id="a4899-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
