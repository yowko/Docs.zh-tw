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
ms.openlocfilehash: b68fbc713374642c9f55d49ee51a88c5785cf4b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727870"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="da963-102">CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="da963-102">CreateDebuggingInterfaceFromVersion Function</span></span>

<span data-ttu-id="da963-103">根據指定的版本資訊建立 [ICorDebug](../debugging/icordebug-interface.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="da963-103">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="da963-104">這項功能在 .NET Framework 4 中已淘汰。</span><span class="sxs-lookup"><span data-stu-id="da963-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="da963-105">相反地，若要取得 common language runtime (CLR) 2.0 的介面，請使用 [ICLRRuntimeInfo：： GetInterface](iclrruntimeinfo-getinterface-method.md) 方法，並指定 [類別識別碼 CLSID_CLRDebuggingLegacy] 和 [介面識別碼] IID_ICorDebug。</span><span class="sxs-lookup"><span data-stu-id="da963-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="da963-106">若要取得 CLR 4 或更新版本的介面，請呼叫 [CLRCreateInstance](clrcreateinstance-function.md) 函式，並指定 CLSID_CLRDebugging 的類別識別碼和介面識別碼 IID_ICLRDebugging。</span><span class="sxs-lookup"><span data-stu-id="da963-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da963-107">語法</span><span class="sxs-lookup"><span data-stu-id="da963-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da963-108">參數</span><span class="sxs-lookup"><span data-stu-id="da963-108">Parameters</span></span>  

 `iDebuggerVersion`  
 <span data-ttu-id="da963-109">在 `ICorDebug` 偵錯工具所預期的版本。</span><span class="sxs-lookup"><span data-stu-id="da963-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="da963-110">如需有效的值，請參閱 [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) 列舉。</span><span class="sxs-lookup"><span data-stu-id="da963-110">See the [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="da963-111">在與要進行調試的應用程式或進程相關聯的 common language runtime 版本。</span><span class="sxs-lookup"><span data-stu-id="da963-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="da963-112">如需有關如何取得此值的詳細資訊，請參閱 [GetVersionFromProcess](getversionfromprocess-function.md) 或 [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="da963-112">See the [GetVersionFromProcess](getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="da963-113">擴展接收物件指標的位置 `ICorDebug` 。</span><span class="sxs-lookup"><span data-stu-id="da963-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da963-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="da963-114">Return Value</span></span>  

 <span data-ttu-id="da963-115">除了下列值以外，這個方法會傳回 Winerror.h .h 檔案中所定義的標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="da963-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="da963-116">傳回碼</span><span class="sxs-lookup"><span data-stu-id="da963-116">Return code</span></span>|<span data-ttu-id="da963-117">描述</span><span class="sxs-lookup"><span data-stu-id="da963-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="da963-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="da963-118">S_OK</span></span>|<span data-ttu-id="da963-119">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="da963-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="da963-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="da963-120">E_INVALIDARG</span></span>|<span data-ttu-id="da963-121">`szDebuggeeVersion` 或 `ppCordb` 為 null，或版本字串不正確。</span><span class="sxs-lookup"><span data-stu-id="da963-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da963-122">備註</span><span class="sxs-lookup"><span data-stu-id="da963-122">Remarks</span></span>  

 <span data-ttu-id="da963-123">`szDebuggeeVersion`參數會對應到 MSCorDbi.dll 的對應版本。</span><span class="sxs-lookup"><span data-stu-id="da963-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da963-124">需求</span><span class="sxs-lookup"><span data-stu-id="da963-124">Requirements</span></span>  

 <span data-ttu-id="da963-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da963-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da963-126">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="da963-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da963-127">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da963-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da963-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da963-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da963-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da963-129">See also</span></span>

- [<span data-ttu-id="da963-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="da963-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
