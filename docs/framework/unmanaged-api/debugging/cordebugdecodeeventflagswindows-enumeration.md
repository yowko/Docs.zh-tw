---
title: "CorDebugDecodeEventFlagsWindows 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugDecodeEventFlagsWindows
api_location: mscordbi.dll
api_type: COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: facde76ec24d90795de7dfb70bfe5772a6f21531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="1ff25-102">CorDebugDecodeEventFlagsWindows 列舉</span><span class="sxs-lookup"><span data-stu-id="1ff25-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="1ff25-103">提供 Windows 平台上之偵錯事件的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="1ff25-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff25-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ff25-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="1ff25-105">成員</span><span class="sxs-lookup"><span data-stu-id="1ff25-105">Members</span></span>  
  
|<span data-ttu-id="1ff25-106">成員</span><span class="sxs-lookup"><span data-stu-id="1ff25-106">Member</span></span>|<span data-ttu-id="1ff25-107">描述</span><span class="sxs-lookup"><span data-stu-id="1ff25-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="1ff25-108">表示偵錯事件是第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1ff25-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ff25-109">備註</span><span class="sxs-lookup"><span data-stu-id="1ff25-109">Remarks</span></span>  
 <span data-ttu-id="1ff25-110">[Icordebugprocess6:: Decodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法包含`dwFlags`參數提供偵錯事件相關的其他資訊，而且其值相依於目標架構。</span><span class="sxs-lookup"><span data-stu-id="1ff25-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="1ff25-111">`CorDebugDecodeEventFlagsWindows` 列舉可搭配 Windows 平台上的偵錯事件使用。</span><span class="sxs-lookup"><span data-stu-id="1ff25-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ff25-112">這個列舉僅適用於 .NET 原生偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="1ff25-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ff25-113">需求</span><span class="sxs-lookup"><span data-stu-id="1ff25-113">Requirements</span></span>  
 <span data-ttu-id="1ff25-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ff25-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ff25-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ff25-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ff25-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ff25-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ff25-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ff25-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff25-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ff25-118">See Also</span></span>  
 [<span data-ttu-id="1ff25-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="1ff25-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
