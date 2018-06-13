---
title: CorDebugMappingResult 列舉
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca3f5a6af6ea19ec81af3f6ac0a028440f80d56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407955"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="fd570-102">CorDebugMappingResult 列舉</span><span class="sxs-lookup"><span data-stu-id="fd570-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="fd570-103">提供如何取得指令指標 (IP) 值的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fd570-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd570-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd570-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="fd570-105">成員</span><span class="sxs-lookup"><span data-stu-id="fd570-105">Members</span></span>  
  
|<span data-ttu-id="fd570-106">成員</span><span class="sxs-lookup"><span data-stu-id="fd570-106">Member</span></span>|<span data-ttu-id="fd570-107">描述</span><span class="sxs-lookup"><span data-stu-id="fd570-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="fd570-108">原生程式碼是在初構中，因此 IP 值為 0。</span><span class="sxs-lookup"><span data-stu-id="fd570-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="fd570-109">原生程式碼處於終解中，因此 IP 值是方法的最後一個指令的位址。</span><span class="sxs-lookup"><span data-stu-id="fd570-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="fd570-110">沒有對應的資訊可用方法，因此 IP 值為 0。</span><span class="sxs-lookup"><span data-stu-id="fd570-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="fd570-111">雖然沒有方法的對應資訊，但是目前的位址無法對應至 Microsoft intermediate language (MSIL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="fd570-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="fd570-112">IP 的值為 0。</span><span class="sxs-lookup"><span data-stu-id="fd570-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="fd570-113">方法會對應至 MSIL 程式碼完全或是框架有解譯，因此 IP 值正確無誤。</span><span class="sxs-lookup"><span data-stu-id="fd570-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="fd570-114">已成功對應方法，但 IP 值可能只是近似。</span><span class="sxs-lookup"><span data-stu-id="fd570-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd570-115">備註</span><span class="sxs-lookup"><span data-stu-id="fd570-115">Remarks</span></span>  
 <span data-ttu-id="fd570-116">您可以使用[icordebugilframe:: Getip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)方法，以取得指令指標的值。</span><span class="sxs-lookup"><span data-stu-id="fd570-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd570-117">需求</span><span class="sxs-lookup"><span data-stu-id="fd570-117">Requirements</span></span>  
 <span data-ttu-id="fd570-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd570-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd570-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd570-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd570-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd570-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd570-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd570-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd570-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd570-122">See Also</span></span>  
 [<span data-ttu-id="fd570-123">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="fd570-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
