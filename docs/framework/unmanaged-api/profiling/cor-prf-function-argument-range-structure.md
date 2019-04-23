---
title: COR_PRF_FUNCTION_ARGUMENT_RANGE 結構
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dffefedf14d5f219736e429be191021b2de7ddd2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125589"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="3e475-102">COR_PRF_FUNCTION_ARGUMENT_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="3e475-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="3e475-103">代表記憶體中由左至右連續儲存的函式引數區塊。</span><span class="sxs-lookup"><span data-stu-id="3e475-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e475-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e475-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="3e475-105">成員</span><span class="sxs-lookup"><span data-stu-id="3e475-105">Members</span></span>  
  
|<span data-ttu-id="3e475-106">成員</span><span class="sxs-lookup"><span data-stu-id="3e475-106">Members</span></span>|<span data-ttu-id="3e475-107">描述</span><span class="sxs-lookup"><span data-stu-id="3e475-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="3e475-108">區塊的開始位址。</span><span class="sxs-lookup"><span data-stu-id="3e475-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="3e475-109">此連續區塊的長度。</span><span class="sxs-lookup"><span data-stu-id="3e475-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e475-110">需求</span><span class="sxs-lookup"><span data-stu-id="3e475-110">Requirements</span></span>  
 <span data-ttu-id="3e475-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e475-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e475-112">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3e475-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3e475-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e475-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e475-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e475-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e475-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e475-115">See also</span></span>

- [<span data-ttu-id="3e475-116">分析結構</span><span class="sxs-lookup"><span data-stu-id="3e475-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
