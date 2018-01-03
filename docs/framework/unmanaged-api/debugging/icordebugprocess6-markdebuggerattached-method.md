---
title: "ICorDebugProcess6::MarkDebuggerAttached 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d3d47f3b5ce6912d5a58f79117b6cd2e05d3ecd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="6e257-102">ICorDebugProcess6::MarkDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="6e257-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="6e257-103">變更偵錯項目的內部狀態，讓 .NET Framework 類別庫中的 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="6e257-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e257-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e257-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e257-105">參數</span><span class="sxs-lookup"><span data-stu-id="6e257-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="6e257-106">如果 `true` 方法應該指出已附加偵錯工具，則為 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6e257-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e257-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6e257-107">Return Value</span></span>  
 <span data-ttu-id="6e257-108">這個方法會傳回下表所列的值。</span><span class="sxs-lookup"><span data-stu-id="6e257-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="6e257-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6e257-109">Return value</span></span>|<span data-ttu-id="6e257-110">描述</span><span class="sxs-lookup"><span data-stu-id="6e257-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="6e257-111">偵錯項目已成功更新。</span><span class="sxs-lookup"><span data-stu-id="6e257-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="6e257-112">尚未載入包含 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法的組件，或遺漏中繼資料等其他一些錯誤導致無法辨認組件。</span><span class="sxs-lookup"><span data-stu-id="6e257-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="6e257-113">這個錯誤很常見而且無害。</span><span class="sxs-lookup"><span data-stu-id="6e257-113">This error is common and benign.</span></span> <span data-ttu-id="6e257-114">當其他組件載入時，您應該再次呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="6e257-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="6e257-115">其他失敗的 `HRESULT` 值。</span><span class="sxs-lookup"><span data-stu-id="6e257-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="6e257-116">可能表示偵錯工具或編譯器元件異常的其他值。</span><span class="sxs-lookup"><span data-stu-id="6e257-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e257-117">備註</span><span class="sxs-lookup"><span data-stu-id="6e257-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e257-118">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="6e257-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e257-119">需求</span><span class="sxs-lookup"><span data-stu-id="6e257-119">Requirements</span></span>  
 <span data-ttu-id="6e257-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e257-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e257-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e257-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e257-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e257-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e257-123">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e257-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e257-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="6e257-124">See Also</span></span>  
 [<span data-ttu-id="6e257-125">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="6e257-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="6e257-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6e257-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
