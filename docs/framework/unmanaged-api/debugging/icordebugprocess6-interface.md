---
title: ICorDebugProcess6 介面
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d180d57431e34d872ff077e6bc597175029688e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962711"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="f2ad9-102">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="f2ad9-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="f2ad9-103">以邏輯方式擴充 ICorDebugProcess 介面以啟用功能, 例如解碼在原生例外狀況的 debug 事件和虛擬模組分割中編碼的 managed 偵錯工具事件。</span><span class="sxs-lookup"><span data-stu-id="f2ad9-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2ad9-104">方法</span><span class="sxs-lookup"><span data-stu-id="f2ad9-104">Methods</span></span>  
  
|<span data-ttu-id="f2ad9-105">方法</span><span class="sxs-lookup"><span data-stu-id="f2ad9-105">Method</span></span>|<span data-ttu-id="f2ad9-106">描述</span><span class="sxs-lookup"><span data-stu-id="f2ad9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2ad9-107">DecodeEvent 方法</span><span class="sxs-lookup"><span data-stu-id="f2ad9-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="f2ad9-108">對已封裝在特殊設計之原生例外狀況偵錯事件承載中的 Managed 偵錯事件進行解碼。</span><span class="sxs-lookup"><span data-stu-id="f2ad9-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="f2ad9-109">EnableVirtualModuleSplitting 方法</span><span class="sxs-lookup"><span data-stu-id="f2ad9-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="f2ad9-110">啟用或停用虛擬模組分割。</span><span class="sxs-lookup"><span data-stu-id="f2ad9-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="f2ad9-111">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="f2ad9-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="f2ad9-112">取得特定程式碼位址之 Managed 程式碼的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f2ad9-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="f2ad9-113">GetExportStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="f2ad9-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="f2ad9-114">提供執行階段匯出函式的相關資訊，以協助逐步執行 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2ad9-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="f2ad9-115">MarkDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="f2ad9-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="f2ad9-116">變更偵錯項目的內部狀態，讓 .NET Framework 類別庫中的 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="f2ad9-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="f2ad9-117">ProcessStateChanged 方法</span><span class="sxs-lookup"><span data-stu-id="f2ad9-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="f2ad9-118">通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)進程正在執行。</span><span class="sxs-lookup"><span data-stu-id="f2ad9-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2ad9-119">備註</span><span class="sxs-lookup"><span data-stu-id="f2ad9-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2ad9-120">這個介面僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="f2ad9-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="f2ad9-121">嘗試在 .NET 原生之外的 ICorDebug 案例中呼叫 `QueryInterface` 以擷取介面指標，會傳回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="f2ad9-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2ad9-122">需求</span><span class="sxs-lookup"><span data-stu-id="f2ad9-122">Requirements</span></span>  
 <span data-ttu-id="f2ad9-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2ad9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2ad9-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2ad9-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2ad9-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2ad9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2ad9-126">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2ad9-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ad9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2ad9-127">See also</span></span>

- [<span data-ttu-id="f2ad9-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f2ad9-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f2ad9-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="f2ad9-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
