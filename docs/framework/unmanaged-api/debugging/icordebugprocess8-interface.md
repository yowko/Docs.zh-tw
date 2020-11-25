---
title: ICorDebugProcess8 介面
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
ms.openlocfilehash: 00c432374eeb82692492b8e6b10472f13bc44d6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732511"
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="60dfd-102">ICorDebugProcess8 介面</span><span class="sxs-lookup"><span data-stu-id="60dfd-102">ICorDebugProcess8 Interface</span></span>

<span data-ttu-id="60dfd-103">[在 .NET Framework 4.6 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="60dfd-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="60dfd-104">以邏輯方式擴充 ICorDebugProcess 介面，以啟用或停用特定類型的 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外狀況回呼。</span><span class="sxs-lookup"><span data-stu-id="60dfd-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60dfd-105">方法</span><span class="sxs-lookup"><span data-stu-id="60dfd-105">Methods</span></span>  
  
|<span data-ttu-id="60dfd-106">方法</span><span class="sxs-lookup"><span data-stu-id="60dfd-106">Method</span></span>|<span data-ttu-id="60dfd-107">描述</span><span class="sxs-lookup"><span data-stu-id="60dfd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60dfd-108">EnableExceptionCallbacksOutsideOfMyCode 方法</span><span class="sxs-lookup"><span data-stu-id="60dfd-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="60dfd-109">啟用或停用特定類型的 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外狀況回呼。</span><span class="sxs-lookup"><span data-stu-id="60dfd-109">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60dfd-110">備註</span><span class="sxs-lookup"><span data-stu-id="60dfd-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60dfd-111">需求</span><span class="sxs-lookup"><span data-stu-id="60dfd-111">Requirements</span></span>  

 <span data-ttu-id="60dfd-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60dfd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60dfd-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60dfd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60dfd-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60dfd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60dfd-115">**.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60dfd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60dfd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60dfd-116">See also</span></span>

- [<span data-ttu-id="60dfd-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="60dfd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="60dfd-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="60dfd-118">Debugging</span></span>](index.md)
