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
ms.openlocfilehash: a1b02bb74a61e64a3ed9875fcf88e018de9f6317
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041434"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="8f0a4-102">ICLRDebuggingLibraryProvider::ProvideLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="8f0a4-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="8f0a4-103">取得程式庫提供者回呼介面, 允許視需要尋找並載入 common language runtime (CLR) 版本特定的偵錯工具程式庫。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f0a4-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f0a4-104">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="8f0a4-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f0a4-105">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="8f0a4-106">在所要求的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-106">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="8f0a4-107">在儲存在 PE 檔案之 COFF 檔案標頭中的日期時間戳記。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="8f0a4-108">在儲存在 PE 檔案之 COFF 選擇性檔案標頭中的欄位。`SizeOfImage`</span><span class="sxs-lookup"><span data-stu-id="8f0a4-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="8f0a4-109">脫銷要求之模組的控制碼。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-109">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="8f0a4-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="8f0a4-110">Return Value</span></span>

<span data-ttu-id="8f0a4-111">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="8f0a4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f0a4-112">HRESULT</span></span>|<span data-ttu-id="8f0a4-113">描述</span><span class="sxs-lookup"><span data-stu-id="8f0a4-113">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="8f0a4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f0a4-114">S_OK</span></span>|<span data-ttu-id="8f0a4-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-115">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="8f0a4-116">例外狀況</span><span class="sxs-lookup"><span data-stu-id="8f0a4-116">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="8f0a4-117">備註</span><span class="sxs-lookup"><span data-stu-id="8f0a4-117">Remarks</span></span>

<span data-ttu-id="8f0a4-118">`ProvideLibrary`可讓偵錯工具提供用來偵測特定 CLR 檔案 (例如 mscordbi.dll 和 mscordacwks) 所需的模組。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="8f0a4-119">模組控制碼必須保持有效, 直到呼叫[ICLRDebugging:: CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)方法指出它們可能被釋放為止, 此時呼叫端會負責釋放控制碼。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="8f0a4-120">偵錯工具可能會使用任何可用的方法來尋找或購買偵錯工具模組。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-120">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f0a4-121">這項功能可讓 API 呼叫端提供包含可執行檔的模組, 以及可能的惡意程式碼。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="8f0a4-122">做為安全性預防措施, 呼叫端不應該`ProvideLibrary`使用來散發不願意自行執行的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="8f0a4-123">如果在已發行的程式庫 (例如 mscordbi.dll 或 mscordacwks) 中發現嚴重的安全性問題, 則可以修補填充碼來辨識檔案的錯誤版本。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="8f0a4-124">填充碼接著可以發出已修補之檔案版本的要求, 並在回應任何要求時, 拒絕不正確的版本。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="8f0a4-125">只有在使用者已修補新版本的填充碼時, 才會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="8f0a4-126">未修補的版本將會保持易受攻擊。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-126">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="8f0a4-127">需求</span><span class="sxs-lookup"><span data-stu-id="8f0a4-127">Requirements</span></span>

<span data-ttu-id="8f0a4-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f0a4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="8f0a4-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f0a4-129">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="8f0a4-130">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f0a4-130">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="8f0a4-131">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f0a4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8f0a4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f0a4-132">See also</span></span>

- [<span data-ttu-id="8f0a4-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8f0a4-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8f0a4-134">偵錯</span><span class="sxs-lookup"><span data-stu-id="8f0a4-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
