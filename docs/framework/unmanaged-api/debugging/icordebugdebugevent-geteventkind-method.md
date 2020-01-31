---
title: ICorDebugDebugEvent::GetEventKind 方法
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 0c67f8bdce49b4e9200b501aaf00ae293cced7d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783406"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="0c998-102">ICorDebugDebugEvent::GetEventKind 方法</span><span class="sxs-lookup"><span data-stu-id="0c998-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="0c998-103">指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。</span><span class="sxs-lookup"><span data-stu-id="0c998-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c998-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c998-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c998-105">參數</span><span class="sxs-lookup"><span data-stu-id="0c998-105">Parameters</span></span>  
 <span data-ttu-id="0c998-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="0c998-106">pDebugEventKind</span></span>  
 <span data-ttu-id="0c998-107">表示事件種類之[CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md)列舉成員的指標。</span><span class="sxs-lookup"><span data-stu-id="0c998-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c998-108">備註</span><span class="sxs-lookup"><span data-stu-id="0c998-108">Remarks</span></span>  
 <span data-ttu-id="0c998-109">根據 `pDebugEventKind` 的值，您可以呼叫 `QueryInterface` 以取得包含其他資料的更精確偵錯事件介面。</span><span class="sxs-lookup"><span data-stu-id="0c998-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c998-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="0c998-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c998-111">需求</span><span class="sxs-lookup"><span data-stu-id="0c998-111">Requirements</span></span>  
 <span data-ttu-id="0c998-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c998-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c998-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c998-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c998-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c998-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c998-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c998-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c998-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c998-116">See also</span></span>

- [<span data-ttu-id="0c998-117">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="0c998-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="0c998-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0c998-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
