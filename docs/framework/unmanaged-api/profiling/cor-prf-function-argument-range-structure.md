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
ms.openlocfilehash: 8b3785955ec138bbf898e84aa4deb5ed2a6e6b53
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500945"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="2eadc-102">COR_PRF_FUNCTION_ARGUMENT_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="2eadc-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="2eadc-103">代表記憶體中由左至右連續儲存的函式引數區塊。</span><span class="sxs-lookup"><span data-stu-id="2eadc-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eadc-104">語法</span><span class="sxs-lookup"><span data-stu-id="2eadc-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="2eadc-105">成員</span><span class="sxs-lookup"><span data-stu-id="2eadc-105">Members</span></span>  
  
|<span data-ttu-id="2eadc-106">成員</span><span class="sxs-lookup"><span data-stu-id="2eadc-106">Members</span></span>|<span data-ttu-id="2eadc-107">說明</span><span class="sxs-lookup"><span data-stu-id="2eadc-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="2eadc-108">區塊的起始位址。</span><span class="sxs-lookup"><span data-stu-id="2eadc-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="2eadc-109">連續區塊的長度。</span><span class="sxs-lookup"><span data-stu-id="2eadc-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2eadc-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="2eadc-110">Requirements</span></span>  
 <span data-ttu-id="2eadc-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2eadc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eadc-112">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="2eadc-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2eadc-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2eadc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2eadc-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eadc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eadc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2eadc-115">See also</span></span>

- [<span data-ttu-id="2eadc-116">分析結構</span><span class="sxs-lookup"><span data-stu-id="2eadc-116">Profiling Structures</span></span>](profiling-structures.md)
