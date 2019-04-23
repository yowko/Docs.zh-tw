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
ms.openlocfilehash: 0144539987f14bed83bfc9eab2f5ca26d2a609ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157726"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="35fdb-102">ICorDebugObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="35fdb-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="35fdb-103">實作 ICorDebugEnum 方法，並列舉物件的陣列的相對虛擬位址 (Rva)。</span><span class="sxs-lookup"><span data-stu-id="35fdb-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35fdb-104">方法</span><span class="sxs-lookup"><span data-stu-id="35fdb-104">Methods</span></span>  
  
|<span data-ttu-id="35fdb-105">方法</span><span class="sxs-lookup"><span data-stu-id="35fdb-105">Method</span></span>|<span data-ttu-id="35fdb-106">描述</span><span class="sxs-lookup"><span data-stu-id="35fdb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35fdb-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="35fdb-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="35fdb-108">從列舉型別，從目前位置開始，取得指定的物件數目的 Rva。</span><span class="sxs-lookup"><span data-stu-id="35fdb-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35fdb-109">備註</span><span class="sxs-lookup"><span data-stu-id="35fdb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35fdb-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="35fdb-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35fdb-111">需求</span><span class="sxs-lookup"><span data-stu-id="35fdb-111">Requirements</span></span>  
 <span data-ttu-id="35fdb-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35fdb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35fdb-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35fdb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35fdb-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35fdb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35fdb-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35fdb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35fdb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35fdb-116">See also</span></span>

- [<span data-ttu-id="35fdb-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="35fdb-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
