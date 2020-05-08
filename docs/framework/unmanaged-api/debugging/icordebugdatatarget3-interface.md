---
title: ICorDebugDataTarget3 介面
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 57ef9b567d57c77c523ca6daefcf80b1d7de66d1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976404"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="59c7b-102">ICorDebugDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="59c7b-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="59c7b-103">以邏輯方式擴充[ICorDebugDataTarget](icordebugdatatarget-interface.md)介面，以提供已載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="59c7b-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="59c7b-104">方法</span><span class="sxs-lookup"><span data-stu-id="59c7b-104">Method</span></span>  
  
|<span data-ttu-id="59c7b-105">方法</span><span class="sxs-lookup"><span data-stu-id="59c7b-105">Method</span></span>|<span data-ttu-id="59c7b-106">描述</span><span class="sxs-lookup"><span data-stu-id="59c7b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59c7b-107">GetLoadedModules 方法</span><span class="sxs-lookup"><span data-stu-id="59c7b-107">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="59c7b-108">取得到目前為止已載入的模組清單。</span><span class="sxs-lookup"><span data-stu-id="59c7b-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59c7b-109">備註</span><span class="sxs-lookup"><span data-stu-id="59c7b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59c7b-110">這個介面僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="59c7b-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="59c7b-111">如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。</span><span class="sxs-lookup"><span data-stu-id="59c7b-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59c7b-112">需求</span><span class="sxs-lookup"><span data-stu-id="59c7b-112">Requirements</span></span>  
 <span data-ttu-id="59c7b-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59c7b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59c7b-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59c7b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59c7b-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59c7b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59c7b-116">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59c7b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c7b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59c7b-117">See also</span></span>

- [<span data-ttu-id="59c7b-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="59c7b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="59c7b-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="59c7b-119">Debugging</span></span>](index.md)
