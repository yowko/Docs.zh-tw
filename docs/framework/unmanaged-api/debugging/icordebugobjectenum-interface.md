---
title: ICorDebugObjectEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1faa78150659b4397cd4174583b607e1f7841b8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943353"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="77aab-102">ICorDebugObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="77aab-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="77aab-103">會執行 ICorDebugEnum 方法, 並依其相對虛擬位址 (Rva) 來列舉物件陣列。</span><span class="sxs-lookup"><span data-stu-id="77aab-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77aab-104">方法</span><span class="sxs-lookup"><span data-stu-id="77aab-104">Methods</span></span>  
  
|<span data-ttu-id="77aab-105">方法</span><span class="sxs-lookup"><span data-stu-id="77aab-105">Method</span></span>|<span data-ttu-id="77aab-106">說明</span><span class="sxs-lookup"><span data-stu-id="77aab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77aab-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="77aab-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="77aab-108">從目前的位置開始, 取得列舉中指定數目之物件的 Rva。</span><span class="sxs-lookup"><span data-stu-id="77aab-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77aab-109">備註</span><span class="sxs-lookup"><span data-stu-id="77aab-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77aab-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="77aab-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77aab-111">需求</span><span class="sxs-lookup"><span data-stu-id="77aab-111">Requirements</span></span>  
 <span data-ttu-id="77aab-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77aab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77aab-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77aab-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77aab-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77aab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77aab-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77aab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77aab-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77aab-116">See also</span></span>

- [<span data-ttu-id="77aab-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="77aab-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
