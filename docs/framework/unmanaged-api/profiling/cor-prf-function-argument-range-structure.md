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
ms.openlocfilehash: c0c0679dac84089577a2698ed8b0b5497a1a81e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753898"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="23f9e-102">COR_PRF_FUNCTION_ARGUMENT_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="23f9e-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="23f9e-103">代表記憶體中由左至右連續儲存的函式引數區塊。</span><span class="sxs-lookup"><span data-stu-id="23f9e-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f9e-104">語法</span><span class="sxs-lookup"><span data-stu-id="23f9e-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="23f9e-105">成員</span><span class="sxs-lookup"><span data-stu-id="23f9e-105">Members</span></span>  
  
|<span data-ttu-id="23f9e-106">成員</span><span class="sxs-lookup"><span data-stu-id="23f9e-106">Members</span></span>|<span data-ttu-id="23f9e-107">說明</span><span class="sxs-lookup"><span data-stu-id="23f9e-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="23f9e-108">區塊的開始位址。</span><span class="sxs-lookup"><span data-stu-id="23f9e-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="23f9e-109">此連續區塊的長度。</span><span class="sxs-lookup"><span data-stu-id="23f9e-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23f9e-110">需求</span><span class="sxs-lookup"><span data-stu-id="23f9e-110">Requirements</span></span>  
 <span data-ttu-id="23f9e-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23f9e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f9e-112">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="23f9e-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="23f9e-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23f9e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23f9e-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f9e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f9e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23f9e-115">See also</span></span>

- [<span data-ttu-id="23f9e-116">分析結構</span><span class="sxs-lookup"><span data-stu-id="23f9e-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
