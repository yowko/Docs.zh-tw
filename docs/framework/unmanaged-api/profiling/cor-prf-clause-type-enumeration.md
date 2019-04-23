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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 861f4c18f4c5151dc7215d300775928b88f018aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090624"
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="7b281-102">COR_PRF_CLAUSE_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="7b281-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="7b281-103">指出剛輸入或留下的程式碼的 exception 子句類型。</span><span class="sxs-lookup"><span data-stu-id="7b281-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b281-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b281-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="7b281-105">成員</span><span class="sxs-lookup"><span data-stu-id="7b281-105">Members</span></span>  
  
|<span data-ttu-id="7b281-106">成員</span><span class="sxs-lookup"><span data-stu-id="7b281-106">Member</span></span>|<span data-ttu-id="7b281-107">描述</span><span class="sxs-lookup"><span data-stu-id="7b281-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="7b281-108">例外狀況子句無效。</span><span class="sxs-lookup"><span data-stu-id="7b281-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="7b281-109">例外狀況子句是篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="7b281-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="7b281-110">例外狀況子句是`catch`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7b281-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="7b281-111">例外狀況子句是`finally`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7b281-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b281-112">需求</span><span class="sxs-lookup"><span data-stu-id="7b281-112">Requirements</span></span>  
 <span data-ttu-id="7b281-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b281-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b281-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b281-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b281-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b281-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b281-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b281-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b281-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b281-117">See also</span></span>

- [<span data-ttu-id="7b281-118">分析列舉</span><span class="sxs-lookup"><span data-stu-id="7b281-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
