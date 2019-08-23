---
title: CorDebugRecordFormat 列舉
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6ed7d25593f9dd5d5d01f8c06024dcf8acfcfea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916479"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="b98fb-102">CorDebugRecordFormat 列舉</span><span class="sxs-lookup"><span data-stu-id="b98fb-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="b98fb-103">描述包含原生例外狀況偵錯事件相關資訊之位元組陣列中的資料格式。</span><span class="sxs-lookup"><span data-stu-id="b98fb-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b98fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="b98fb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="b98fb-105">成員</span><span class="sxs-lookup"><span data-stu-id="b98fb-105">Members</span></span>  
  
|<span data-ttu-id="b98fb-106">成員</span><span class="sxs-lookup"><span data-stu-id="b98fb-106">Member</span></span>|<span data-ttu-id="b98fb-107">描述</span><span class="sxs-lookup"><span data-stu-id="b98fb-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="b98fb-108">這份資料是 32 位元 Windows 例外狀況記錄。</span><span class="sxs-lookup"><span data-stu-id="b98fb-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="b98fb-109">這份資料是 64 位元 Windows 例外狀況記錄。</span><span class="sxs-lookup"><span data-stu-id="b98fb-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b98fb-110">備註</span><span class="sxs-lookup"><span data-stu-id="b98fb-110">Remarks</span></span>  
 <span data-ttu-id="b98fb-111">`CorDebugRecordFormat`列舉的成員會傳遞至[DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法, 以指出其`pRecord`引數中的位元組陣列格式。</span><span class="sxs-lookup"><span data-stu-id="b98fb-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b98fb-112">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="b98fb-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b98fb-113">需求</span><span class="sxs-lookup"><span data-stu-id="b98fb-113">Requirements</span></span>  
 <span data-ttu-id="b98fb-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b98fb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b98fb-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b98fb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b98fb-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b98fb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b98fb-117">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b98fb-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98fb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b98fb-118">See also</span></span>

- [<span data-ttu-id="b98fb-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="b98fb-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
