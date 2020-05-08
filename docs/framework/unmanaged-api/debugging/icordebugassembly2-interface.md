---
title: ICorDebugAssembly2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2
helpviewer_keywords:
- ICorDebugAssembly2 interface [.NET Framework debugging]
ms.assetid: c0766e29-e573-4f9a-a928-167d1de5aa7e
topic_type:
- apiref
ms.openlocfilehash: 23b38f86cd81fb0161e50b60b40bed0ba0b423b2
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894875"
---
# <a name="icordebugassembly2-interface"></a><span data-ttu-id="10332-102">ICorDebugAssembly2 介面</span><span class="sxs-lookup"><span data-stu-id="10332-102">ICorDebugAssembly2 Interface</span></span>

<span data-ttu-id="10332-103">表示組件。</span><span class="sxs-lookup"><span data-stu-id="10332-103">Represents an assembly.</span></span> <span data-ttu-id="10332-104">這個介面是 ICorDebugAssembly 介面的延伸。</span><span class="sxs-lookup"><span data-stu-id="10332-104">This interface is an extension of the ICorDebugAssembly interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10332-105">方法</span><span class="sxs-lookup"><span data-stu-id="10332-105">Methods</span></span>  
  
|<span data-ttu-id="10332-106">方法</span><span class="sxs-lookup"><span data-stu-id="10332-106">Method</span></span>|<span data-ttu-id="10332-107">描述</span><span class="sxs-lookup"><span data-stu-id="10332-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10332-108">IsFullyTrusted 方法</span><span class="sxs-lookup"><span data-stu-id="10332-108">IsFullyTrusted Method</span></span>](icordebugassembly2-isfullytrusted-method.md)|<span data-ttu-id="10332-109">取得值，指出執行時間安全性系統是否已授與元件完全信任。</span><span class="sxs-lookup"><span data-stu-id="10332-109">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10332-110">備註</span><span class="sxs-lookup"><span data-stu-id="10332-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10332-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="10332-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10332-112">需求</span><span class="sxs-lookup"><span data-stu-id="10332-112">Requirements</span></span>  
 <span data-ttu-id="10332-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10332-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10332-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10332-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10332-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10332-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10332-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10332-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10332-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10332-117">See also</span></span>

- [<span data-ttu-id="10332-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="10332-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
