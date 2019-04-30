---
title: CLRDataEnumMemoryFlags 列舉
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80ea3afef4aee51760e3a2ce6a2b895bca4a6ec5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961352"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="8d4b6-102">CLRDataEnumMemoryFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="8d4b6-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="8d4b6-103">指出哪些記憶體區域呼叫[iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)方法應該包含。</span><span class="sxs-lookup"><span data-stu-id="8d4b6-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d4b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d4b6-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8d4b6-105">成員</span><span class="sxs-lookup"><span data-stu-id="8d4b6-105">Members</span></span>  
  
|<span data-ttu-id="8d4b6-106">成員</span><span class="sxs-lookup"><span data-stu-id="8d4b6-106">Member</span></span>|<span data-ttu-id="8d4b6-107">描述</span><span class="sxs-lookup"><span data-stu-id="8d4b6-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="8d4b6-108">小型傾印，也就是疏鬆的記憶體傾印。</span><span class="sxs-lookup"><span data-stu-id="8d4b6-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="8d4b6-109">完整的堆積傾印。</span><span class="sxs-lookup"><span data-stu-id="8d4b6-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d4b6-110">需求</span><span class="sxs-lookup"><span data-stu-id="8d4b6-110">Requirements</span></span>  
 <span data-ttu-id="8d4b6-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d4b6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d4b6-112">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="8d4b6-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8d4b6-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d4b6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d4b6-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d4b6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4b6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d4b6-115">See also</span></span>

- [<span data-ttu-id="8d4b6-116">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="8d4b6-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
