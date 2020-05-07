---
title: ICorDebugAssemblyEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum
helpviewer_keywords:
- ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: 891ceb43-5161-421e-a0bf-299962fd7efd
topic_type:
- apiref
ms.openlocfilehash: 988637956b1176235618bf8f4aee7ecec9ce1187
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894840"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="9a010-102">ICorDebugAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9a010-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="9a010-103">會執行 ICorDebugEnum 方法並列舉 ICorDebugAssembly 陣列。</span><span class="sxs-lookup"><span data-stu-id="9a010-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a010-104">方法</span><span class="sxs-lookup"><span data-stu-id="9a010-104">Methods</span></span>  
  
|<span data-ttu-id="9a010-105">方法</span><span class="sxs-lookup"><span data-stu-id="9a010-105">Method</span></span>|<span data-ttu-id="9a010-106">描述</span><span class="sxs-lookup"><span data-stu-id="9a010-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a010-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="9a010-107">Next Method</span></span>](icordebugassemblyenum-next-method.md)|<span data-ttu-id="9a010-108">從目前位置開始， `ICorDebugAssembly`取得列舉中指定的實例數目。</span><span class="sxs-lookup"><span data-stu-id="9a010-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a010-109">備註</span><span class="sxs-lookup"><span data-stu-id="9a010-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a010-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="9a010-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a010-111">需求</span><span class="sxs-lookup"><span data-stu-id="9a010-111">Requirements</span></span>  
 <span data-ttu-id="9a010-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a010-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a010-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a010-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a010-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a010-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a010-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a010-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a010-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a010-116">See also</span></span>

- [<span data-ttu-id="9a010-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9a010-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
