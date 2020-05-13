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
ms.openlocfilehash: 0594caf53a889d51ea78e2ee9d6fff4d30f7cff2
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205284"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="4a93e-102">ICorDebugObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="4a93e-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="4a93e-103">會執行 ICorDebugEnum 方法，並依其相對虛擬位址（Rva）來列舉物件陣列。</span><span class="sxs-lookup"><span data-stu-id="4a93e-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a93e-104">方法</span><span class="sxs-lookup"><span data-stu-id="4a93e-104">Methods</span></span>  
  
|<span data-ttu-id="4a93e-105">方法</span><span class="sxs-lookup"><span data-stu-id="4a93e-105">Method</span></span>|<span data-ttu-id="4a93e-106">描述</span><span class="sxs-lookup"><span data-stu-id="4a93e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a93e-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="4a93e-107">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="4a93e-108">從目前的位置開始，取得列舉中指定數目之物件的 Rva。</span><span class="sxs-lookup"><span data-stu-id="4a93e-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a93e-109">備註</span><span class="sxs-lookup"><span data-stu-id="4a93e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a93e-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4a93e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a93e-111">需求</span><span class="sxs-lookup"><span data-stu-id="4a93e-111">Requirements</span></span>  
 <span data-ttu-id="4a93e-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a93e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a93e-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a93e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a93e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a93e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a93e-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a93e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a93e-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="4a93e-116">See also</span></span>

- [<span data-ttu-id="4a93e-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4a93e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
