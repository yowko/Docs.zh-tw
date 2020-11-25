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
ms.openlocfilehash: 9a82162023fa05e85fc9bbeb16961f2aafd9a4ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729794"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="7ed46-102">CLRDataEnumMemoryFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="7ed46-102">CLRDataEnumMemoryFlags Enumeration</span></span>

<span data-ttu-id="7ed46-103">指出呼叫 [ICLRDataEnumMemoryRegions：： EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) 方法應該包含的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="7ed46-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ed46-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ed46-104">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="7ed46-105">成員</span><span class="sxs-lookup"><span data-stu-id="7ed46-105">Members</span></span>  
  
|<span data-ttu-id="7ed46-106">member</span><span class="sxs-lookup"><span data-stu-id="7ed46-106">Member</span></span>|<span data-ttu-id="7ed46-107">描述</span><span class="sxs-lookup"><span data-stu-id="7ed46-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="7ed46-108">小型傾印，也就是稀疏記憶體傾印。</span><span class="sxs-lookup"><span data-stu-id="7ed46-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="7ed46-109">完整堆積傾印。</span><span class="sxs-lookup"><span data-stu-id="7ed46-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ed46-110">需求</span><span class="sxs-lookup"><span data-stu-id="7ed46-110">Requirements</span></span>  

 <span data-ttu-id="7ed46-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ed46-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ed46-112">**標頭：** ClrData .idl、ClrData。h</span><span class="sxs-lookup"><span data-stu-id="7ed46-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7ed46-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ed46-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ed46-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ed46-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed46-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed46-115">See also</span></span>

- [<span data-ttu-id="7ed46-116">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="7ed46-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
