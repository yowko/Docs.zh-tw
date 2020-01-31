---
title: ICorDebugTypeEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum
helpviewer_keywords:
- ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: 159ccfcf-b37c-4ad9-8e0d-a9a443262472
topic_type:
- apiref
ms.openlocfilehash: ed7bceec9bf6ea0cf69cbb57fff83a91093ba6c4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791202"
---
# <a name="icordebugtypeenum-interface"></a><span data-ttu-id="7429c-102">ICorDebugTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="7429c-102">ICorDebugTypeEnum Interface</span></span>
<span data-ttu-id="7429c-103">會執行 "ICorDebugEnum" 方法，並列舉 "ICorDebugType" 陣列。</span><span class="sxs-lookup"><span data-stu-id="7429c-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugType" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7429c-104">方法</span><span class="sxs-lookup"><span data-stu-id="7429c-104">Methods</span></span>  
  
|<span data-ttu-id="7429c-105">方法</span><span class="sxs-lookup"><span data-stu-id="7429c-105">Method</span></span>|<span data-ttu-id="7429c-106">描述</span><span class="sxs-lookup"><span data-stu-id="7429c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7429c-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="7429c-107">Next Method</span></span>](icordebugtypeenum-next-method.md)|<span data-ttu-id="7429c-108">從列舉中取得指定數目的 `ICorDebugType` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="7429c-108">Gets the specified number of `ICorDebugType` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7429c-109">備註</span><span class="sxs-lookup"><span data-stu-id="7429c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7429c-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7429c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7429c-111">需求</span><span class="sxs-lookup"><span data-stu-id="7429c-111">Requirements</span></span>  
 <span data-ttu-id="7429c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7429c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7429c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7429c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7429c-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7429c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7429c-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7429c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7429c-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="7429c-116">See also</span></span>

- [<span data-ttu-id="7429c-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7429c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
