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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224034"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="fdc9b-102">CLRDataEnumMemoryFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="fdc9b-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="fdc9b-103">指出哪些記憶體區域呼叫[iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)方法應該包含。</span><span class="sxs-lookup"><span data-stu-id="fdc9b-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdc9b-104">語法</span><span class="sxs-lookup"><span data-stu-id="fdc9b-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fdc9b-105">成員</span><span class="sxs-lookup"><span data-stu-id="fdc9b-105">Members</span></span>  
  
|<span data-ttu-id="fdc9b-106">成員</span><span class="sxs-lookup"><span data-stu-id="fdc9b-106">Member</span></span>|<span data-ttu-id="fdc9b-107">描述</span><span class="sxs-lookup"><span data-stu-id="fdc9b-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="fdc9b-108">小型傾印，也就是疏鬆的記憶體傾印。</span><span class="sxs-lookup"><span data-stu-id="fdc9b-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="fdc9b-109">完整的堆積傾印。</span><span class="sxs-lookup"><span data-stu-id="fdc9b-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fdc9b-110">需求</span><span class="sxs-lookup"><span data-stu-id="fdc9b-110">Requirements</span></span>  
 <span data-ttu-id="fdc9b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fdc9b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdc9b-112">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="fdc9b-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="fdc9b-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdc9b-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fdc9b-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="fdc9b-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fdc9b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdc9b-115">See also</span></span>

- [<span data-ttu-id="fdc9b-116">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="fdc9b-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
