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
ms.openlocfilehash: f40345b09cae164660711b987f62130518736518
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208620"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="50246-102">適用於 Silverlight 的 CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="50246-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>

<span data-ttu-id="50246-103">接受從[CreateVersionStringFromModule](createversionstringfrommodule-function.md)函式傳回的 common language RUNTIME （CLR）版本字串，並傳回對應的偵錯工具介面（通常是[ICorDebug](icordebug-interface.md)）。</span><span class="sxs-lookup"><span data-stu-id="50246-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50246-104">語法</span><span class="sxs-lookup"><span data-stu-id="50246-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50246-105">參數</span><span class="sxs-lookup"><span data-stu-id="50246-105">Parameters</span></span>  

 `szDebuggeeVersion`\
 <span data-ttu-id="50246-106">在目標偵錯工具中 CLR 的版本字串（由[CreateVersionStringFromModule 函數](createversionstringfrommodule-function.md)傳回）。</span><span class="sxs-lookup"><span data-stu-id="50246-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`\
 <span data-ttu-id="50246-107">[out] COM 物件 (`IUnknown`) 指標的指標。</span><span class="sxs-lookup"><span data-stu-id="50246-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="50246-108">這個物件會在傳回之前轉換成[ICorDebug](icordebug-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="50246-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50246-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="50246-109">Return Value</span></span>

 `S_OK`\
 <span data-ttu-id="50246-110">`ppCordb`參考實[ICorDebug 介面](icordebug-interface.md)介面的有效物件。</span><span class="sxs-lookup"><span data-stu-id="50246-110">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 `E_INVALIDARG`\
 <span data-ttu-id="50246-111">`szDebuggeeVersion` 或 `ppCordb` 為 null。</span><span class="sxs-lookup"><span data-stu-id="50246-111">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 `CORDBG_E_DEBUG_COMPONENT_MISSING`\
 <span data-ttu-id="50246-112">找不到 CLR 偵錯所需的元件。</span><span class="sxs-lookup"><span data-stu-id="50246-112">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="50246-113">在與目標 CoreCLR 相同的目錄中找不到_mscordbi.dll_或_mscordaccore.dll。_</span><span class="sxs-lookup"><span data-stu-id="50246-113">Either _mscordbi.dll_ or _mscordaccore.dll_ was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 `CORDBG_E_INCOMPATIBLE_PROTOCOL`\
 <span data-ttu-id="50246-114">mscordbi.dll 或 mscordaccore.dll 的版本與目標 CoreCLR.dll 的版本不同。</span><span class="sxs-lookup"><span data-stu-id="50246-114">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="50246-115">`E_FAIL`（或其他傳回 `E_` 碼） </span><span class="sxs-lookup"><span data-stu-id="50246-115">`E_FAIL` (or other `E_` return codes)</span></span>\
 <span data-ttu-id="50246-116">無法傳回[ICorDebug 介面](icordebug-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="50246-116">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50246-117">備註</span><span class="sxs-lookup"><span data-stu-id="50246-117">Remarks</span></span>

 <span data-ttu-id="50246-118">傳回的介面提供了附加至目標處理序中的 CLR，以及對 CLR 正在執行之 Managed 程式碼進行偵錯的功能。</span><span class="sxs-lookup"><span data-stu-id="50246-118">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50246-119">需求</span><span class="sxs-lookup"><span data-stu-id="50246-119">Requirements</span></span>

 <span data-ttu-id="50246-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50246-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50246-121">**標頭：** dbgshim。h</span><span class="sxs-lookup"><span data-stu-id="50246-121">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="50246-122">連結**庫：** dbgshim</span><span class="sxs-lookup"><span data-stu-id="50246-122">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="50246-123">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="50246-123">**.NET Framework Versions:** 3.5 SP1</span></span>
