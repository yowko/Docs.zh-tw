---
title: ICorDebugModuleEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: 08d16393a04888cd3f1a03fa209a1fceac28520b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724750"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="4abaa-102">ICorDebugModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="4abaa-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="4abaa-103">會實 ICorDebugEnum 方法，並列舉 ICorDebugModule 陣列。</span><span class="sxs-lookup"><span data-stu-id="4abaa-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4abaa-104">方法</span><span class="sxs-lookup"><span data-stu-id="4abaa-104">Methods</span></span>  
  
|<span data-ttu-id="4abaa-105">方法</span><span class="sxs-lookup"><span data-stu-id="4abaa-105">Method</span></span>|<span data-ttu-id="4abaa-106">描述</span><span class="sxs-lookup"><span data-stu-id="4abaa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4abaa-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="4abaa-107">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="4abaa-108">`ICorDebugModule`從目前位置開始，取得列舉的指定實例數目。</span><span class="sxs-lookup"><span data-stu-id="4abaa-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4abaa-109">備註</span><span class="sxs-lookup"><span data-stu-id="4abaa-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4abaa-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4abaa-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4abaa-111">需求</span><span class="sxs-lookup"><span data-stu-id="4abaa-111">Requirements</span></span>  

 <span data-ttu-id="4abaa-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4abaa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4abaa-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4abaa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4abaa-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4abaa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4abaa-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4abaa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4abaa-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4abaa-116">See also</span></span>

- [<span data-ttu-id="4abaa-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4abaa-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
