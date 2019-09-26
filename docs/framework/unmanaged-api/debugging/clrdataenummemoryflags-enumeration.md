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
ms.openlocfilehash: 67b85917be590bdba7ed3f10972ad39b731dbcdd
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274236"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="a8d86-102">CLRDataEnumMemoryFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="a8d86-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="a8d86-103">指出[ICLRDataEnumMemoryRegions：： EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md)方法的呼叫應包含的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="a8d86-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8d86-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8d86-104">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a8d86-105">成員</span><span class="sxs-lookup"><span data-stu-id="a8d86-105">Members</span></span>  
  
|<span data-ttu-id="a8d86-106">成員</span><span class="sxs-lookup"><span data-stu-id="a8d86-106">Member</span></span>|<span data-ttu-id="a8d86-107">描述</span><span class="sxs-lookup"><span data-stu-id="a8d86-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="a8d86-108">小型傾印，也就是稀疏記憶體傾印。</span><span class="sxs-lookup"><span data-stu-id="a8d86-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="a8d86-109">完整的堆積傾印。</span><span class="sxs-lookup"><span data-stu-id="a8d86-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8d86-110">需求</span><span class="sxs-lookup"><span data-stu-id="a8d86-110">Requirements</span></span>  
 <span data-ttu-id="a8d86-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8d86-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8d86-112">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="a8d86-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a8d86-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8d86-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8d86-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8d86-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d86-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8d86-115">See also</span></span>

- [<span data-ttu-id="a8d86-116">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="a8d86-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
