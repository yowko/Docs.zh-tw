---
title: ICorDebugAppDomain3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
ms.openlocfilehash: 644457edbf5035f6d946e1c83ff0053fb118288e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698230"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="aea97-102">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="aea97-102">ICorDebugAppDomain3 Interface</span></span>

<span data-ttu-id="aea97-103">提供方法，以取得目前在應用程式域中載入 Windows 執行階段類型之 managed 表示的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="aea97-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="aea97-104">此介面是 ICorDebugAppDomain 和 ICorDebugAppDomain2 介面的延伸。</span><span class="sxs-lookup"><span data-stu-id="aea97-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aea97-105">方法</span><span class="sxs-lookup"><span data-stu-id="aea97-105">Methods</span></span>  
  
|<span data-ttu-id="aea97-106">方法</span><span class="sxs-lookup"><span data-stu-id="aea97-106">Method</span></span>|<span data-ttu-id="aea97-107">描述</span><span class="sxs-lookup"><span data-stu-id="aea97-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aea97-108">ICorDebugAppDomain3：： GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="aea97-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="aea97-109">取得所有快取 Windows 執行階段類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="aea97-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="aea97-110">ICorDebugAppDomain3：： GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="aea97-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="aea97-111">根據其介面識別碼，取得應用程式域中快取 Windows 執行階段類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="aea97-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aea97-112">備註</span><span class="sxs-lookup"><span data-stu-id="aea97-112">Remarks</span></span>  

 <span data-ttu-id="aea97-113">這個介面的目的是要由偵錯工具與的函式評估呼叫一起使用 `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)` 。</span><span class="sxs-lookup"><span data-stu-id="aea97-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="aea97-114">當方法抓取 Windows 執行階段 server 物件所支援的介面識別碼時，偵錯工具可能會使用此介面中定義的方法，將它們對應至對應至這些介面的 managed 類型。</span><span class="sxs-lookup"><span data-stu-id="aea97-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="aea97-115">若要取出這個介面的實例，請 `QueryInterface` 在 ICorDebugAppDomain 或 ICorDebugAppDomain2 介面的實例上執行。</span><span class="sxs-lookup"><span data-stu-id="aea97-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aea97-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="aea97-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aea97-117">需求</span><span class="sxs-lookup"><span data-stu-id="aea97-117">Requirements</span></span>  

 <span data-ttu-id="aea97-118">**平臺：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="aea97-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="aea97-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aea97-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aea97-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aea97-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aea97-121">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aea97-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea97-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aea97-122">See also</span></span>

- [<span data-ttu-id="aea97-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="aea97-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
