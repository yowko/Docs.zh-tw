---
title: ICorDebugProcess6::MarkDebuggerAttached 方法
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c818b196f3252138f2a9c601b04f1d7a6727bc6b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912746"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="ed6c1-102">ICorDebugProcess6::MarkDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="ed6c1-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="ed6c1-103">變更偵錯項目的內部狀態，讓 .NET Framework 類別庫中的 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed6c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed6c1-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed6c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed6c1-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="ed6c1-106">如果 `true` 方法應該指出已附加偵錯工具，則為 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed6c1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ed6c1-107">Return Value</span></span>  
 <span data-ttu-id="ed6c1-108">這個方法會傳回下表所列的值。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="ed6c1-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ed6c1-109">Return value</span></span>|<span data-ttu-id="ed6c1-110">說明</span><span class="sxs-lookup"><span data-stu-id="ed6c1-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="ed6c1-111">偵錯項目已成功更新。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="ed6c1-112">尚未載入包含 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法的組件，或遺漏中繼資料等其他一些錯誤導致無法辨認組件。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="ed6c1-113">這個錯誤很常見而且無害。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-113">This error is common and benign.</span></span> <span data-ttu-id="ed6c1-114">當其他組件載入時，您應該再次呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="ed6c1-115">其他失敗的 `HRESULT` 值。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="ed6c1-116">可能表示偵錯工具或編譯器元件異常的其他值。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed6c1-117">備註</span><span class="sxs-lookup"><span data-stu-id="ed6c1-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed6c1-118">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed6c1-119">需求</span><span class="sxs-lookup"><span data-stu-id="ed6c1-119">Requirements</span></span>  
 <span data-ttu-id="ed6c1-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed6c1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed6c1-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed6c1-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed6c1-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed6c1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed6c1-123">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed6c1-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed6c1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed6c1-124">See also</span></span>

- [<span data-ttu-id="ed6c1-125">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="ed6c1-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="ed6c1-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ed6c1-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
