---
title: ICLRDebuggingLibraryProvider::ProvideLibrary 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f5d44b6497e971e6d1ed030c043b91b88c070b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697796"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="5a831-102">ICLRDebuggingLibraryProvider::ProvideLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="5a831-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>
<span data-ttu-id="5a831-103">取得程式庫提供者回呼介面，可讓 common language runtime (CLR) 版本特定偵錯程式庫尋找並載入需求。</span><span class="sxs-lookup"><span data-stu-id="5a831-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a831-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a831-104">Syntax</span></span>  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a831-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a831-105">Parameters</span></span>  
 `pwszFilename`  
 <span data-ttu-id="5a831-106">[in]所要求的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="5a831-106">[in] The name of the module being requested.</span></span>  
  
 `dwTimestamp`  
 <span data-ttu-id="5a831-107">[in]COFF 檔案標頭的 PE 檔中儲存的日期時間戳記。</span><span class="sxs-lookup"><span data-stu-id="5a831-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="5a831-108">[in]`SizeOfImage` COFF 選用的檔案標頭的 PE 檔中儲存的欄位。</span><span class="sxs-lookup"><span data-stu-id="5a831-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>  
  
 `hModule`  
 <span data-ttu-id="5a831-109">[out]要求的模組控制代碼。</span><span class="sxs-lookup"><span data-stu-id="5a831-109">[out] The handle to the requested module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a831-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="5a831-110">Return Value</span></span>  
 <span data-ttu-id="5a831-111">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="5a831-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5a831-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a831-112">HRESULT</span></span>|<span data-ttu-id="5a831-113">描述</span><span class="sxs-lookup"><span data-stu-id="5a831-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a831-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a831-114">S_OK</span></span>|<span data-ttu-id="5a831-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="5a831-115">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="5a831-116">例外狀況</span><span class="sxs-lookup"><span data-stu-id="5a831-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a831-117">備註</span><span class="sxs-lookup"><span data-stu-id="5a831-117">Remarks</span></span>  
 <span data-ttu-id="5a831-118">`ProvideLibrary` 可讓偵錯工具提供所需的偵錯特定的 CLR 檔案，例如 mscordbi.dll 和 mscordacwks.dll 的模組。</span><span class="sxs-lookup"><span data-stu-id="5a831-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="5a831-119">模組控制代碼必須保持有效，直到呼叫[iclrdebugging:: Canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)方法表示它們可能會釋出，此時必須負責呼叫者釋放控制代碼。</span><span class="sxs-lookup"><span data-stu-id="5a831-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>  
  
 <span data-ttu-id="5a831-120">偵錯工具可以使用任何可用的方式，來找出或購買的偵錯的模組。</span><span class="sxs-lookup"><span data-stu-id="5a831-120">The debugger may use any available means to locate or procure the debugging module.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a831-121">這項功能可讓 API 呼叫端，以提供包含可執行檔，並可能是惡意的程式碼的模組。</span><span class="sxs-lookup"><span data-stu-id="5a831-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="5a831-122">為了安全起見，呼叫端不應該使用`ProvideLibrary`散發不願意執行本身的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a831-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>  
>   
>  <span data-ttu-id="5a831-123">如果已發行的文件庫，例如 mscordbi.dll 或 mscordacwks.dll 中, 探索到嚴重的安全性問題可辨識不正確的版本檔案的修補填充碼。</span><span class="sxs-lookup"><span data-stu-id="5a831-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="5a831-124">填充碼然後發出要求的修補檔案的版本，並拒絕不正確的版本，如果提供以回應任何要求。</span><span class="sxs-lookup"><span data-stu-id="5a831-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="5a831-125">這可能是只有當使用者有新的版本，填充碼修正的項目。</span><span class="sxs-lookup"><span data-stu-id="5a831-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="5a831-126">未更新的版本仍易受攻擊。</span><span class="sxs-lookup"><span data-stu-id="5a831-126">Unpatched versions will remain vulnerable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a831-127">需求</span><span class="sxs-lookup"><span data-stu-id="5a831-127">Requirements</span></span>  
 <span data-ttu-id="5a831-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a831-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a831-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a831-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a831-130">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a831-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a831-131">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a831-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a831-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a831-132">See also</span></span>

- [<span data-ttu-id="5a831-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5a831-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5a831-134">偵錯</span><span class="sxs-lookup"><span data-stu-id="5a831-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
