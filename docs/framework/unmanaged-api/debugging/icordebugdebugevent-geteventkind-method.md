---
title: ICorDebugDebugEvent::GetEventKind 方法
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bbc9581db839d9c0a48362eac2108f43665b0fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414852"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="9cc6d-102">ICorDebugDebugEvent::GetEventKind 方法</span><span class="sxs-lookup"><span data-stu-id="9cc6d-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="9cc6d-103">指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。</span><span class="sxs-lookup"><span data-stu-id="9cc6d-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cc6d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9cc6d-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cc6d-105">參數</span><span class="sxs-lookup"><span data-stu-id="9cc6d-105">Parameters</span></span>  
 <span data-ttu-id="9cc6d-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="9cc6d-106">pDebugEventKind</span></span>  
 <span data-ttu-id="9cc6d-107">指標[CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)列舉的成員，表示事件類型。</span><span class="sxs-lookup"><span data-stu-id="9cc6d-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cc6d-108">備註</span><span class="sxs-lookup"><span data-stu-id="9cc6d-108">Remarks</span></span>  
 <span data-ttu-id="9cc6d-109">根據 `pDebugEventKind` 的值，您可以呼叫 `QueryInterface` 以取得包含其他資料的更精確偵錯事件介面。</span><span class="sxs-lookup"><span data-stu-id="9cc6d-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cc6d-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="9cc6d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cc6d-111">需求</span><span class="sxs-lookup"><span data-stu-id="9cc6d-111">Requirements</span></span>  
 <span data-ttu-id="9cc6d-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9cc6d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cc6d-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cc6d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cc6d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cc6d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cc6d-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cc6d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc6d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cc6d-116">See Also</span></span>  
 [<span data-ttu-id="9cc6d-117">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="9cc6d-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="9cc6d-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9cc6d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
