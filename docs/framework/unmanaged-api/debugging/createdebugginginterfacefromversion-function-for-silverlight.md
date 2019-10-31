---
title: 適用於 Silverlight 的 CreateDebuggingInterfaceFromVersion 函式
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: 438af9f191f48a86207c3b343ba428eef2c1fabc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132195"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="670b6-102">適用於 Silverlight 的 CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="670b6-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="670b6-103">接受從[CreateVersionStringFromModule](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)函式傳回的 common language RUNTIME （CLR）版本字串，並傳回對應的偵錯工具介面（通常是[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)）。</span><span class="sxs-lookup"><span data-stu-id="670b6-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="670b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="670b6-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="670b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="670b6-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="670b6-106">在目標偵錯工具中 CLR 的版本字串（由[CreateVersionStringFromModule 函數](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)傳回）。</span><span class="sxs-lookup"><span data-stu-id="670b6-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="670b6-107">[out] COM 物件 (`IUnknown`) 指標的指標。</span><span class="sxs-lookup"><span data-stu-id="670b6-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="670b6-108">這個物件會在傳回之前轉換成[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="670b6-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="670b6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="670b6-109">Return Value</span></span>  
 <span data-ttu-id="670b6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="670b6-110">S_OK</span></span>  
 <span data-ttu-id="670b6-111">`ppCordb` 會參考實[ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)介面的有效物件。</span><span class="sxs-lookup"><span data-stu-id="670b6-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="670b6-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="670b6-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="670b6-113">`szDebuggeeVersion` 或 `ppCordb` 為 null。</span><span class="sxs-lookup"><span data-stu-id="670b6-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="670b6-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="670b6-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="670b6-115">找不到 CLR 偵錯所需的元件。</span><span class="sxs-lookup"><span data-stu-id="670b6-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="670b6-116">這表示在目標 CoreCLR.dll 所在的相同目錄中找不到 mscordbi.dll 或 mscordaccore.dll。</span><span class="sxs-lookup"><span data-stu-id="670b6-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="670b6-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="670b6-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="670b6-118">mscordbi.dll 或 mscordaccore.dll 的版本與目標 CoreCLR.dll 的版本不同。</span><span class="sxs-lookup"><span data-stu-id="670b6-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="670b6-119">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="670b6-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="670b6-120">無法傳回[ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="670b6-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="670b6-121">備註</span><span class="sxs-lookup"><span data-stu-id="670b6-121">Remarks</span></span>  
 <span data-ttu-id="670b6-122">傳回的介面提供了附加至目標處理序中的 CLR，以及對 CLR 正在執行之 Managed 程式碼進行偵錯的功能。</span><span class="sxs-lookup"><span data-stu-id="670b6-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="670b6-123">需求</span><span class="sxs-lookup"><span data-stu-id="670b6-123">Requirements</span></span>  
 <span data-ttu-id="670b6-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="670b6-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="670b6-125">**標頭：** dbgshim。h</span><span class="sxs-lookup"><span data-stu-id="670b6-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="670b6-126">連結**庫：** dbgshim</span><span class="sxs-lookup"><span data-stu-id="670b6-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="670b6-127">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="670b6-127">**.NET Framework Versions:** 3.5 SP1</span></span>
