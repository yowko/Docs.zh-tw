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
ms.openlocfilehash: e23dfb86c2129a02a0ca95de8c89d8294e97ad81
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136842"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="8d0f8-102">CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="8d0f8-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="8d0f8-103">根據指定的版本資訊建立[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="8d0f8-104">此函式在 .NET Framework 4 中已過時。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="8d0f8-105">相反地，若要取得 common language runtime （CLR）2.0 的介面，請使用[ICLRRuntimeInfo：： GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法，並指定類別識別碼 CLSID_CLRDebuggingLegacy 和介面識別碼 IID_ICorDebug。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="8d0f8-106">若要取得 CLR 4 或更新版本的介面，請呼叫[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函數，並指定類別識別碼 CLSID_CLRDebugging 和介面識別碼 IID_ICLRDebugging。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d0f8-107">語法</span><span class="sxs-lookup"><span data-stu-id="8d0f8-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d0f8-108">參數</span><span class="sxs-lookup"><span data-stu-id="8d0f8-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="8d0f8-109">在偵錯工具所需的 `ICorDebug` 版本。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="8d0f8-110">如需有效的值，請參閱[CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="8d0f8-111">在與要進行調試的應用程式或進程相關聯的 common language runtime 版本。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="8d0f8-112">如需有關抓取此值的詳細資訊，請參閱[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)或[GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="8d0f8-113">脫銷接收 `ICorDebug` 物件之指標的位置。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d0f8-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="8d0f8-114">Return Value</span></span>  
 <span data-ttu-id="8d0f8-115">除了下列值之外，這個方法會傳回 Winerror.h 檔案中定義的標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="8d0f8-116">傳回碼</span><span class="sxs-lookup"><span data-stu-id="8d0f8-116">Return code</span></span>|<span data-ttu-id="8d0f8-117">描述</span><span class="sxs-lookup"><span data-stu-id="8d0f8-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8d0f8-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d0f8-118">S_OK</span></span>|<span data-ttu-id="8d0f8-119">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="8d0f8-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8d0f8-120">E_INVALIDARG</span></span>|<span data-ttu-id="8d0f8-121">`szDebuggeeVersion` 或 `ppCordb` 為 null，或版本字串不正確。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d0f8-122">備註</span><span class="sxs-lookup"><span data-stu-id="8d0f8-122">Remarks</span></span>  
 <span data-ttu-id="8d0f8-123">`szDebuggeeVersion` 參數會對應至相對應的 Mscordbi.dll 版本。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d0f8-124">需求</span><span class="sxs-lookup"><span data-stu-id="8d0f8-124">Requirements</span></span>  
 <span data-ttu-id="8d0f8-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0f8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d0f8-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8d0f8-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d0f8-127">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="8d0f8-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d0f8-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d0f8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0f8-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d0f8-129">See also</span></span>

- [<span data-ttu-id="8d0f8-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="8d0f8-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
