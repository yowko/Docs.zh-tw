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
ms.openlocfilehash: a308017dc80dd973cbf108ba9df824193775f5ff
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501049"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="ac3aa-102">COR_PRF_CLAUSE_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="ac3aa-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="ac3aa-103">指出剛輸入或留下的程式碼的 exception 子句類型。</span><span class="sxs-lookup"><span data-stu-id="ac3aa-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac3aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac3aa-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="ac3aa-105">成員</span><span class="sxs-lookup"><span data-stu-id="ac3aa-105">Members</span></span>  
  
|<span data-ttu-id="ac3aa-106">成員</span><span class="sxs-lookup"><span data-stu-id="ac3aa-106">Member</span></span>|<span data-ttu-id="ac3aa-107">說明</span><span class="sxs-lookup"><span data-stu-id="ac3aa-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="ac3aa-108">例外狀況子句無效。</span><span class="sxs-lookup"><span data-stu-id="ac3aa-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="ac3aa-109">Exception 子句是一個篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="ac3aa-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="ac3aa-110">Exception 子句是 `catch` 語句。</span><span class="sxs-lookup"><span data-stu-id="ac3aa-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="ac3aa-111">Exception 子句是 `finally` 語句。</span><span class="sxs-lookup"><span data-stu-id="ac3aa-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac3aa-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="ac3aa-112">Requirements</span></span>  
 <span data-ttu-id="ac3aa-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac3aa-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac3aa-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac3aa-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac3aa-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac3aa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac3aa-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac3aa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac3aa-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac3aa-117">See also</span></span>

- [<span data-ttu-id="ac3aa-118">分析列舉</span><span class="sxs-lookup"><span data-stu-id="ac3aa-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
