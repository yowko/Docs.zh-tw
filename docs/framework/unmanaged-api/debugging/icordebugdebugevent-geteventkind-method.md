---
title: ICorDebugDebugEvent::GetEventKind 方法
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 7876dc6ec5ecee52b64e54e1c42533f8348e4dc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713674"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="b828e-102">ICorDebugDebugEvent::GetEventKind 方法</span><span class="sxs-lookup"><span data-stu-id="b828e-102">ICorDebugDebugEvent::GetEventKind Method</span></span>

<span data-ttu-id="b828e-103">指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。</span><span class="sxs-lookup"><span data-stu-id="b828e-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b828e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b828e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b828e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b828e-105">Parameters</span></span>  

 <span data-ttu-id="b828e-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="b828e-106">pDebugEventKind</span></span>  
 <span data-ttu-id="b828e-107">[CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md)列舉成員的指標，指出事件的類型。</span><span class="sxs-lookup"><span data-stu-id="b828e-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b828e-108">備註</span><span class="sxs-lookup"><span data-stu-id="b828e-108">Remarks</span></span>  

 <span data-ttu-id="b828e-109">根據 `pDebugEventKind` 的值，您可以呼叫 `QueryInterface` 以取得包含其他資料的更精確偵錯事件介面。</span><span class="sxs-lookup"><span data-stu-id="b828e-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b828e-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="b828e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b828e-111">需求</span><span class="sxs-lookup"><span data-stu-id="b828e-111">Requirements</span></span>  

 <span data-ttu-id="b828e-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b828e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b828e-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b828e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b828e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b828e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b828e-115">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b828e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b828e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b828e-116">See also</span></span>

- [<span data-ttu-id="b828e-117">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="b828e-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="b828e-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b828e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
