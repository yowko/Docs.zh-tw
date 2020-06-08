---
title: COR_PRF_STATIC_TYPE 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: 80d72aefc736054afcee152c55e941c0f8f3c6a8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500763"
---
# <a name="cor_prf_static_type-enumeration"></a><span data-ttu-id="9067d-102">COR_PRF_STATIC_TYPE 列舉</span><span class="sxs-lookup"><span data-stu-id="9067d-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="9067d-103">指出欄位是否為靜態，若是靜態，則欄位套用的是靜態品質。</span><span class="sxs-lookup"><span data-stu-id="9067d-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="9067d-104">這些值可以使用位 OR 運算來結合，表示該欄位有多個不同的靜態品質。</span><span class="sxs-lookup"><span data-stu-id="9067d-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9067d-105">語法</span><span class="sxs-lookup"><span data-stu-id="9067d-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="9067d-106">成員</span><span class="sxs-lookup"><span data-stu-id="9067d-106">Members</span></span>  
  
|<span data-ttu-id="9067d-107">成員</span><span class="sxs-lookup"><span data-stu-id="9067d-107">Member</span></span>|<span data-ttu-id="9067d-108">說明</span><span class="sxs-lookup"><span data-stu-id="9067d-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="9067d-109">欄位不是靜態的。</span><span class="sxs-lookup"><span data-stu-id="9067d-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="9067d-110">欄位為 [應用程式域-靜態]。</span><span class="sxs-lookup"><span data-stu-id="9067d-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="9067d-111">此欄位為執行緒靜態。</span><span class="sxs-lookup"><span data-stu-id="9067d-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="9067d-112">欄位為內容靜態。</span><span class="sxs-lookup"><span data-stu-id="9067d-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="9067d-113">此欄位為相對虛擬位址（RVA）-靜態。</span><span class="sxs-lookup"><span data-stu-id="9067d-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9067d-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="9067d-114">Requirements</span></span>  
 <span data-ttu-id="9067d-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9067d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9067d-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9067d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9067d-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9067d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9067d-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9067d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9067d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9067d-119">See also</span></span>

- [<span data-ttu-id="9067d-120">分析列舉</span><span class="sxs-lookup"><span data-stu-id="9067d-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
