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
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176444"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="228c0-102">CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="228c0-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="228c0-103">根據指定的版本資訊創建[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="228c0-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="228c0-104">此功能在 .NET 框架 4 中已過時。</span><span class="sxs-lookup"><span data-stu-id="228c0-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="228c0-105">相反，要獲取通用語言運行時 （CLR） 2.0 的介面，請使用[ICLRRuntimeinfo：getInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法，並指定類識別碼CLSID_CLRDebuggingLegacy和介面識別碼IID_ICorDebug。</span><span class="sxs-lookup"><span data-stu-id="228c0-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="228c0-106">要獲取 CLR 4 或更高版本的介面，請調用[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函數，並指定類識別碼CLSID_CLRDebugging和介面識別碼IID_ICLRDebugging。</span><span class="sxs-lookup"><span data-stu-id="228c0-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="228c0-107">語法</span><span class="sxs-lookup"><span data-stu-id="228c0-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="228c0-108">參數</span><span class="sxs-lookup"><span data-stu-id="228c0-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="228c0-109">[在]`ICorDebug`調試器預期的版本。</span><span class="sxs-lookup"><span data-stu-id="228c0-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="228c0-110">有關有效值，請參閱[CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)枚舉。</span><span class="sxs-lookup"><span data-stu-id="228c0-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="228c0-111">[在]與要調試的應用程式或進程關聯的通用語言執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="228c0-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="228c0-112">有關檢索此值的資訊，請參閱[獲取從進程](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)獲取版本或[獲取請求執行階段版本](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)的方法。</span><span class="sxs-lookup"><span data-stu-id="228c0-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="228c0-113">[出]接收指向`ICorDebug`物件的指標的位置。</span><span class="sxs-lookup"><span data-stu-id="228c0-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="228c0-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="228c0-114">Return Value</span></span>  
 <span data-ttu-id="228c0-115">此方法返回 WinError.h 檔中定義的標準 COM 錯誤代碼以及以下值。</span><span class="sxs-lookup"><span data-stu-id="228c0-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="228c0-116">傳回碼</span><span class="sxs-lookup"><span data-stu-id="228c0-116">Return code</span></span>|<span data-ttu-id="228c0-117">描述</span><span class="sxs-lookup"><span data-stu-id="228c0-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="228c0-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="228c0-118">S_OK</span></span>|<span data-ttu-id="228c0-119">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="228c0-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="228c0-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="228c0-120">E_INVALIDARG</span></span>|<span data-ttu-id="228c0-121">`szDebuggeeVersion`或`ppCordb`為 null，或者版本字串不正確。</span><span class="sxs-lookup"><span data-stu-id="228c0-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="228c0-122">備註</span><span class="sxs-lookup"><span data-stu-id="228c0-122">Remarks</span></span>  
 <span data-ttu-id="228c0-123">參數`szDebuggeeVersion`映射到相應的 MSCorDbi.dll 版本。</span><span class="sxs-lookup"><span data-stu-id="228c0-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="228c0-124">需求</span><span class="sxs-lookup"><span data-stu-id="228c0-124">Requirements</span></span>  
 <span data-ttu-id="228c0-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="228c0-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="228c0-126">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="228c0-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="228c0-127">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="228c0-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="228c0-128">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="228c0-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228c0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="228c0-129">See also</span></span>

- [<span data-ttu-id="228c0-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="228c0-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
