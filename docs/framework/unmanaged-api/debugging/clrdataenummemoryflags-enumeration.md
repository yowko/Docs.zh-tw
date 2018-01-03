---
title: "CLRDataEnumMemoryFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRDataEnumMemoryFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLRDataEnumMemoryFlags
helpviewer_keywords: CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88e8ca340c8512156606f10236c779daf96c3156
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="dff78-102">CLRDataEnumMemoryFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="dff78-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="dff78-103">指出哪些記憶體區域呼叫[iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)方法應該包含。</span><span class="sxs-lookup"><span data-stu-id="dff78-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff78-104">語法</span><span class="sxs-lookup"><span data-stu-id="dff78-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="dff78-105">成員</span><span class="sxs-lookup"><span data-stu-id="dff78-105">Members</span></span>  
  
|<span data-ttu-id="dff78-106">成員</span><span class="sxs-lookup"><span data-stu-id="dff78-106">Member</span></span>|<span data-ttu-id="dff78-107">描述</span><span class="sxs-lookup"><span data-stu-id="dff78-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="dff78-108">小型傾印，也就是疏鬆的記憶體傾印。</span><span class="sxs-lookup"><span data-stu-id="dff78-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="dff78-109">完整的堆積傾印。</span><span class="sxs-lookup"><span data-stu-id="dff78-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dff78-110">需求</span><span class="sxs-lookup"><span data-stu-id="dff78-110">Requirements</span></span>  
 <span data-ttu-id="dff78-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dff78-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dff78-112">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="dff78-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="dff78-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dff78-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dff78-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dff78-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dff78-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="dff78-115">See Also</span></span>  
 [<span data-ttu-id="dff78-116">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="dff78-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
