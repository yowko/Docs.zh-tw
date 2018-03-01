---
title: "ICLRDebuggingLibraryProvider::ProvideLibrary 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf6860a616312504e3d23177734cb532405bd714
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="62614-102">ICLRDebuggingLibraryProvider::ProvideLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="62614-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>
<span data-ttu-id="62614-103">取得程式庫提供者回呼介面，common language runtime (CLR) 版本特定偵錯程式庫找到並載入需求。</span><span class="sxs-lookup"><span data-stu-id="62614-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62614-104">語法</span><span class="sxs-lookup"><span data-stu-id="62614-104">Syntax</span></span>  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62614-105">參數</span><span class="sxs-lookup"><span data-stu-id="62614-105">Parameters</span></span>  
 `pwszFilename`  
 <span data-ttu-id="62614-106">[in]所要求的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="62614-106">[in] The name of the module being requested .</span></span>  
  
 `dwTimestamp`  
 <span data-ttu-id="62614-107">[in]日期時間戳記儲存在 PE 檔的 COFF 檔案標頭。</span><span class="sxs-lookup"><span data-stu-id="62614-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="62614-108">[in]`SizeOfImage` COFF 選用的檔案標頭的 PE 檔中儲存的欄位。</span><span class="sxs-lookup"><span data-stu-id="62614-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>  
  
 `hModule`  
 <span data-ttu-id="62614-109">[out]要求的模組控制代碼。</span><span class="sxs-lookup"><span data-stu-id="62614-109">[out] The handle to the requested module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62614-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="62614-110">Return Value</span></span>  
 <span data-ttu-id="62614-111">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="62614-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="62614-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62614-112">HRESULT</span></span>|<span data-ttu-id="62614-113">描述</span><span class="sxs-lookup"><span data-stu-id="62614-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62614-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="62614-114">S_OK</span></span>|<span data-ttu-id="62614-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="62614-115">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="62614-116">例外狀況</span><span class="sxs-lookup"><span data-stu-id="62614-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62614-117">備註</span><span class="sxs-lookup"><span data-stu-id="62614-117">Remarks</span></span>  
 <span data-ttu-id="62614-118">`ProvideLibrary`可讓偵錯工具，以提供所需的偵錯特定的 CLR 檔案，例如 mscordbi.dll 與 mscordacwks.dll 的模組。</span><span class="sxs-lookup"><span data-stu-id="62614-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="62614-119">模組控制代碼必須維持有效，直到呼叫[iclrdebugging:: Canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)方法表示可能會釋放，此時必須負責呼叫者釋放控制代碼。</span><span class="sxs-lookup"><span data-stu-id="62614-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>  
  
 <span data-ttu-id="62614-120">偵錯工具可以使用任何可用的方法來找出或採購偵錯模組。</span><span class="sxs-lookup"><span data-stu-id="62614-120">The debugger may use any available means to locate or procure the debugging module.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="62614-121">這項功能可讓應用程式開發介面呼叫者提供包含可執行檔，且可能是惡意程式碼模組。</span><span class="sxs-lookup"><span data-stu-id="62614-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="62614-122">基於安全性考量，呼叫端不應該使用`ProvideLibrary`散發不願意執行本身的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="62614-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>  
>   
>  <span data-ttu-id="62614-123">如果已發行的程式庫，例如 mscordbi.dll 或 mscordacwks.dll，發現嚴重的安全性問題以辨識不正確的檔案版本修補填充碼。</span><span class="sxs-lookup"><span data-stu-id="62614-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="62614-124">填充碼然後發出要求的修補檔案的版本，並拒絕不正確的版本，如果回應任何要求中提供。</span><span class="sxs-lookup"><span data-stu-id="62614-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="62614-125">只有當使用者已經修補至新版的填充碼，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="62614-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="62614-126">未更新的版本仍會有弱點。</span><span class="sxs-lookup"><span data-stu-id="62614-126">Unpatched versions will remain vulnerable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62614-127">需求</span><span class="sxs-lookup"><span data-stu-id="62614-127">Requirements</span></span>  
 <span data-ttu-id="62614-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62614-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62614-129">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62614-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62614-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62614-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62614-131">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62614-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62614-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="62614-132">See Also</span></span>  
 [<span data-ttu-id="62614-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="62614-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="62614-134">偵錯</span><span class="sxs-lookup"><span data-stu-id="62614-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
