---
title: ICorDebugThreadEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
ms.openlocfilehash: ca7668f23671721477c561774bab03279c4c18c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678554"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="4ed78-102">ICorDebugThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="4ed78-102">ICorDebugThreadEnum Interface</span></span>

<span data-ttu-id="4ed78-103">實 ICorDebugEnum 方法並列舉 ICorDebugThread 陣列。</span><span class="sxs-lookup"><span data-stu-id="4ed78-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4ed78-104">方法</span><span class="sxs-lookup"><span data-stu-id="4ed78-104">Methods</span></span>  
  
|<span data-ttu-id="4ed78-105">方法</span><span class="sxs-lookup"><span data-stu-id="4ed78-105">Method</span></span>|<span data-ttu-id="4ed78-106">描述</span><span class="sxs-lookup"><span data-stu-id="4ed78-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4ed78-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="4ed78-107">Next Method</span></span>](icordebugthreadenum-next-method.md)|<span data-ttu-id="4ed78-108">`ICorDebugThread`從目前位置開始，取得列舉的指定實例數目。</span><span class="sxs-lookup"><span data-stu-id="4ed78-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ed78-109">備註</span><span class="sxs-lookup"><span data-stu-id="4ed78-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ed78-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4ed78-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ed78-111">需求</span><span class="sxs-lookup"><span data-stu-id="4ed78-111">Requirements</span></span>  

 <span data-ttu-id="4ed78-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ed78-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ed78-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ed78-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ed78-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ed78-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ed78-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ed78-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ed78-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ed78-116">See also</span></span>

- [<span data-ttu-id="4ed78-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4ed78-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
