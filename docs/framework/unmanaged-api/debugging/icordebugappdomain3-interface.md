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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3676cb32ceaf6f241672751f0feafbd3cb83e05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968867"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="b2956-102">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="b2956-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="b2956-103">提供方法, 以取得目前載入應用程式域之 Windows 執行階段類型的 managed 標記法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b2956-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="b2956-104">這個介面是 ICorDebugAppDomain 和 ICorDebugAppDomain2 介面的延伸。</span><span class="sxs-lookup"><span data-stu-id="b2956-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2956-105">方法</span><span class="sxs-lookup"><span data-stu-id="b2956-105">Methods</span></span>  
  
|<span data-ttu-id="b2956-106">方法</span><span class="sxs-lookup"><span data-stu-id="b2956-106">Method</span></span>|<span data-ttu-id="b2956-107">描述</span><span class="sxs-lookup"><span data-stu-id="b2956-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2956-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="b2956-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="b2956-109">取得所有快取 Windows 執行階段類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="b2956-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="b2956-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="b2956-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="b2956-111">根據介面識別碼, 取得應用程式域中快取 Windows 執行階段類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="b2956-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2956-112">備註</span><span class="sxs-lookup"><span data-stu-id="b2956-112">Remarks</span></span>  
 <span data-ttu-id="b2956-113">這個介面適用于偵錯工具搭配的函式評估呼叫`M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`使用。</span><span class="sxs-lookup"><span data-stu-id="b2956-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="b2956-114">當方法抓取 Windows 執行階段 server 物件所支援的介面識別碼時, 偵錯工具可能會使用在這個介面中定義的方法, 將它們對應到與這些介面相對應的 managed 類型。</span><span class="sxs-lookup"><span data-stu-id="b2956-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="b2956-115">若要取得此介面的實例, 請`QueryInterface`在 ICorDebugAppDomain 或 ICorDebugAppDomain2 介面的實例上執行。</span><span class="sxs-lookup"><span data-stu-id="b2956-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2956-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b2956-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2956-117">需求</span><span class="sxs-lookup"><span data-stu-id="b2956-117">Requirements</span></span>  
 <span data-ttu-id="b2956-118">**平台：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="b2956-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="b2956-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2956-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2956-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2956-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2956-121">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2956-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2956-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2956-122">See also</span></span>

- [<span data-ttu-id="b2956-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b2956-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
