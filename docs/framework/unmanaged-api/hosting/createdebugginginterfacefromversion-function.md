---
title: CreateDebuggingInterfaceFromVersion 函式
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: 6f5eec282aec6a2757664023ce8031410e316f10
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501842"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="796fd-102">CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="796fd-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="796fd-103">根據指定的版本資訊建立[ICorDebug](../debugging/icordebug-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="796fd-103">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="796fd-104">此函式在 .NET Framework 4 中已過時。</span><span class="sxs-lookup"><span data-stu-id="796fd-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="796fd-105">相反地，若要取得 common language runtime （CLR）2.0 的介面，請使用[ICLRRuntimeInfo：： GetInterface](iclrruntimeinfo-getinterface-method.md)方法，並指定 CLSID_CLRDebuggingLegacy 的類別識別碼和 IID_ICorDebug 的介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="796fd-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="796fd-106">若要取得 CLR 4 或更新版本的介面，請呼叫[CLRCreateInstance](clrcreateinstance-function.md)函式，並指定 CLSID_CLRDebugging 的類別識別碼和 IID_ICLRDebugging 的介面識別碼。</span><span class="sxs-lookup"><span data-stu-id="796fd-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796fd-107">語法</span><span class="sxs-lookup"><span data-stu-id="796fd-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="796fd-108">參數</span><span class="sxs-lookup"><span data-stu-id="796fd-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="796fd-109">在`ICorDebug`偵錯工具所需的版本。</span><span class="sxs-lookup"><span data-stu-id="796fd-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="796fd-110">如需有效的值，請參閱[CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="796fd-110">See the [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="796fd-111">在與要進行調試的應用程式或進程相關聯的 common language runtime 版本。</span><span class="sxs-lookup"><span data-stu-id="796fd-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="796fd-112">如需有關抓取此值的詳細資訊，請參閱[GetVersionFromProcess](getversionfromprocess-function.md)或[GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md)方法。</span><span class="sxs-lookup"><span data-stu-id="796fd-112">See the [GetVersionFromProcess](getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="796fd-113">脫銷接收物件指標的位置 `ICorDebug` 。</span><span class="sxs-lookup"><span data-stu-id="796fd-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="796fd-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="796fd-114">Return Value</span></span>  
 <span data-ttu-id="796fd-115">除了下列值之外，這個方法會傳回 Winerror.h 檔案中定義的標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="796fd-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="796fd-116">傳回碼</span><span class="sxs-lookup"><span data-stu-id="796fd-116">Return code</span></span>|<span data-ttu-id="796fd-117">說明</span><span class="sxs-lookup"><span data-stu-id="796fd-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="796fd-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="796fd-118">S_OK</span></span>|<span data-ttu-id="796fd-119">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="796fd-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="796fd-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="796fd-120">E_INVALIDARG</span></span>|<span data-ttu-id="796fd-121">`szDebuggeeVersion`或 `ppCordb` 為 null，或版本字串不正確。</span><span class="sxs-lookup"><span data-stu-id="796fd-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="796fd-122">備註</span><span class="sxs-lookup"><span data-stu-id="796fd-122">Remarks</span></span>  
 <span data-ttu-id="796fd-123">`szDebuggeeVersion`參數會對應至相對應的 mscordbi.dll 版本。</span><span class="sxs-lookup"><span data-stu-id="796fd-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="796fd-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="796fd-124">Requirements</span></span>  
 <span data-ttu-id="796fd-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="796fd-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="796fd-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="796fd-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="796fd-127">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="796fd-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="796fd-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="796fd-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796fd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="796fd-129">See also</span></span>

- [<span data-ttu-id="796fd-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="796fd-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
