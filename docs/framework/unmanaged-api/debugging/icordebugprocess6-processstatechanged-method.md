---
title: "ICorDebugProcess6::ProcessStateChanged 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e5aad3e95668525fe607bf4e90b4e05b2b58cad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="e9232-102">ICorDebugProcess6::ProcessStateChanged 方法</span><span class="sxs-lookup"><span data-stu-id="e9232-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="e9232-103">通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)處理序正在執行。</span><span class="sxs-lookup"><span data-stu-id="e9232-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9232-104">語法</span><span class="sxs-lookup"><span data-stu-id="e9232-104">Syntax</span></span>  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9232-105">參數</span><span class="sxs-lookup"><span data-stu-id="e9232-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="e9232-106">[in]成員[ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)列舉</span><span class="sxs-lookup"><span data-stu-id="e9232-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9232-107">備註</span><span class="sxs-lookup"><span data-stu-id="e9232-107">Remarks</span></span>  
 <span data-ttu-id="e9232-108">偵錯工具呼叫此方法來通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)處理序正在執行。</span><span class="sxs-lookup"><span data-stu-id="e9232-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9232-109">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="e9232-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9232-110">需求</span><span class="sxs-lookup"><span data-stu-id="e9232-110">Requirements</span></span>  
 <span data-ttu-id="e9232-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9232-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9232-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9232-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9232-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9232-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9232-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9232-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9232-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9232-115">See Also</span></span>  
 [<span data-ttu-id="e9232-116">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="e9232-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="e9232-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e9232-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
