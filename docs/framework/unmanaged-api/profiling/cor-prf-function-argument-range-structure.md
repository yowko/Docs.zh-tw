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
ms.openlocfilehash: ddd8e86b119a3c19417306dee056e435a4f5d07a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537903"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="096da-102">COR_PRF_FUNCTION_ARGUMENT_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="096da-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="096da-103">代表記憶體中由左至右連續儲存的函式引數區塊。</span><span class="sxs-lookup"><span data-stu-id="096da-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096da-104">語法</span><span class="sxs-lookup"><span data-stu-id="096da-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="096da-105">成員</span><span class="sxs-lookup"><span data-stu-id="096da-105">Members</span></span>  
  
|<span data-ttu-id="096da-106">成員</span><span class="sxs-lookup"><span data-stu-id="096da-106">Members</span></span>|<span data-ttu-id="096da-107">描述</span><span class="sxs-lookup"><span data-stu-id="096da-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="096da-108">區塊的開始位址。</span><span class="sxs-lookup"><span data-stu-id="096da-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="096da-109">此連續區塊的長度。</span><span class="sxs-lookup"><span data-stu-id="096da-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="096da-110">需求</span><span class="sxs-lookup"><span data-stu-id="096da-110">Requirements</span></span>  
 <span data-ttu-id="096da-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="096da-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="096da-112">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="096da-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="096da-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="096da-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="096da-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="096da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="096da-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="096da-115">See also</span></span>
- [<span data-ttu-id="096da-116">分析結構</span><span class="sxs-lookup"><span data-stu-id="096da-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
