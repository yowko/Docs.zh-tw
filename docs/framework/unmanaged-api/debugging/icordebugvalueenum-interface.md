---
title: ICorDebugValueEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum
helpviewer_keywords:
- ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: 88989482-a09f-4bd0-9adb-16f47b0291fd
topic_type:
- apiref
ms.openlocfilehash: e3934cbce76df3997fa07d8fa3a99bd8ddab09a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684339"
---
# <a name="icordebugvalueenum-interface"></a><span data-ttu-id="ff409-102">ICorDebugValueEnum 介面</span><span class="sxs-lookup"><span data-stu-id="ff409-102">ICorDebugValueEnum Interface</span></span>

<span data-ttu-id="ff409-103">實作為 "ICorDebugEnum" 方法，並列舉 "ICorDebugValue" 陣列。</span><span class="sxs-lookup"><span data-stu-id="ff409-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugValue" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff409-104">方法</span><span class="sxs-lookup"><span data-stu-id="ff409-104">Methods</span></span>  
  
|<span data-ttu-id="ff409-105">方法</span><span class="sxs-lookup"><span data-stu-id="ff409-105">Method</span></span>|<span data-ttu-id="ff409-106">描述</span><span class="sxs-lookup"><span data-stu-id="ff409-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff409-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="ff409-107">Next Method</span></span>](icordebugvalueenum-next-method.md)|<span data-ttu-id="ff409-108">`ICorDebugValue`從目前位置開始，取得列舉的指定實例數目。</span><span class="sxs-lookup"><span data-stu-id="ff409-108">Gets the specified number of `ICorDebugValue` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff409-109">備註</span><span class="sxs-lookup"><span data-stu-id="ff409-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff409-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="ff409-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff409-111">需求</span><span class="sxs-lookup"><span data-stu-id="ff409-111">Requirements</span></span>  

 <span data-ttu-id="ff409-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff409-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff409-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff409-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff409-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff409-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff409-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff409-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff409-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff409-116">See also</span></span>

- [<span data-ttu-id="ff409-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ff409-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
