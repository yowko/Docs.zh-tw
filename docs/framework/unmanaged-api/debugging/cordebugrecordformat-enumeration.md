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
ms.openlocfilehash: adb13688791cd7d8f467780da1895d4f9fe6e990
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739640"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="de51f-102">CorDebugRecordFormat 列舉</span><span class="sxs-lookup"><span data-stu-id="de51f-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="de51f-103">描述包含原生例外狀況偵錯事件相關資訊之位元組陣列中的資料格式。</span><span class="sxs-lookup"><span data-stu-id="de51f-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de51f-104">語法</span><span class="sxs-lookup"><span data-stu-id="de51f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="de51f-105">成員</span><span class="sxs-lookup"><span data-stu-id="de51f-105">Members</span></span>  
  
|<span data-ttu-id="de51f-106">成員</span><span class="sxs-lookup"><span data-stu-id="de51f-106">Member</span></span>|<span data-ttu-id="de51f-107">說明</span><span class="sxs-lookup"><span data-stu-id="de51f-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="de51f-108">這份資料是 32 位元 Windows 例外狀況記錄。</span><span class="sxs-lookup"><span data-stu-id="de51f-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="de51f-109">這份資料是 64 位元 Windows 例外狀況記錄。</span><span class="sxs-lookup"><span data-stu-id="de51f-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de51f-110">備註</span><span class="sxs-lookup"><span data-stu-id="de51f-110">Remarks</span></span>  
 <span data-ttu-id="de51f-111">成員`CorDebugRecordFormat`列舉會傳遞至[DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法，以表示中的位元組陣列格式其`pRecord`引數。</span><span class="sxs-lookup"><span data-stu-id="de51f-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de51f-112">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="de51f-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de51f-113">需求</span><span class="sxs-lookup"><span data-stu-id="de51f-113">Requirements</span></span>  
 <span data-ttu-id="de51f-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de51f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de51f-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de51f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de51f-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de51f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de51f-117">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de51f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de51f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de51f-118">See also</span></span>

- [<span data-ttu-id="de51f-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="de51f-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
