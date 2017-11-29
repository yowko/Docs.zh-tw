---
title: "ICorDebugDebugEvent::GetEventKind 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf3296eafb3e3ff933092240f8f353b2b69a89c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="68fc1-102">ICorDebugDebugEvent::GetEventKind 方法</span><span class="sxs-lookup"><span data-stu-id="68fc1-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="68fc1-103">指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。</span><span class="sxs-lookup"><span data-stu-id="68fc1-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68fc1-104">語法</span><span class="sxs-lookup"><span data-stu-id="68fc1-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68fc1-105">參數</span><span class="sxs-lookup"><span data-stu-id="68fc1-105">Parameters</span></span>  
 <span data-ttu-id="68fc1-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="68fc1-106">pDebugEventKind</span></span>  
 <span data-ttu-id="68fc1-107">指標[CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)列舉的成員，表示事件類型。</span><span class="sxs-lookup"><span data-stu-id="68fc1-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68fc1-108">備註</span><span class="sxs-lookup"><span data-stu-id="68fc1-108">Remarks</span></span>  
 <span data-ttu-id="68fc1-109">根據 `pDebugEventKind` 的值，您可以呼叫 `QueryInterface` 以取得包含其他資料的更精確偵錯事件介面。</span><span class="sxs-lookup"><span data-stu-id="68fc1-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68fc1-110">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="68fc1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68fc1-111">需求</span><span class="sxs-lookup"><span data-stu-id="68fc1-111">Requirements</span></span>  
 <span data-ttu-id="68fc1-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68fc1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68fc1-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68fc1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68fc1-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68fc1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68fc1-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68fc1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68fc1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68fc1-116">See Also</span></span>  
 [<span data-ttu-id="68fc1-117">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="68fc1-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="68fc1-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="68fc1-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
