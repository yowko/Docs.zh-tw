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
ms.openlocfilehash: b3a22d7b32eb258263d373ae91b3fb7fbc9aae99
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696384"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="fbeea-102">CorDebugRecordFormat 列舉</span><span class="sxs-lookup"><span data-stu-id="fbeea-102">CorDebugRecordFormat Enumeration</span></span>

<span data-ttu-id="fbeea-103">描述包含原生例外狀況偵錯事件相關資訊之位元組陣列中的資料格式。</span><span class="sxs-lookup"><span data-stu-id="fbeea-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbeea-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbeea-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="fbeea-105">成員</span><span class="sxs-lookup"><span data-stu-id="fbeea-105">Members</span></span>  
  
|<span data-ttu-id="fbeea-106">member</span><span class="sxs-lookup"><span data-stu-id="fbeea-106">Member</span></span>|<span data-ttu-id="fbeea-107">描述</span><span class="sxs-lookup"><span data-stu-id="fbeea-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="fbeea-108">這份資料是 32 位元 Windows 例外狀況記錄。</span><span class="sxs-lookup"><span data-stu-id="fbeea-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="fbeea-109">這份資料是 64 位元 Windows 例外狀況記錄。</span><span class="sxs-lookup"><span data-stu-id="fbeea-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbeea-110">備註</span><span class="sxs-lookup"><span data-stu-id="fbeea-110">Remarks</span></span>  

 <span data-ttu-id="fbeea-111">列舉的成員 `CorDebugRecordFormat` 會傳遞至 [DecodeEvent](icordebugprocess6-decodeevent-method.md) 方法，以在其引數中指出位元組陣列的格式 `pRecord` 。</span><span class="sxs-lookup"><span data-stu-id="fbeea-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbeea-112">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="fbeea-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbeea-113">需求</span><span class="sxs-lookup"><span data-stu-id="fbeea-113">Requirements</span></span>  

 <span data-ttu-id="fbeea-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fbeea-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbeea-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbeea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbeea-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbeea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbeea-117">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbeea-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbeea-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbeea-118">See also</span></span>

- [<span data-ttu-id="fbeea-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="fbeea-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
