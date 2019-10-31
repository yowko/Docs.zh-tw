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
ms.openlocfilehash: 8fc2abd0728115edbbfae42958d8013029523ed1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111368"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="40fcb-102">ICLRDebuggingLibraryProvider::ProvideLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="40fcb-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="40fcb-103">取得程式庫提供者回呼介面，允許視需要尋找並載入 common language runtime （CLR）版本特定的偵錯工具程式庫。</span><span class="sxs-lookup"><span data-stu-id="40fcb-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="40fcb-104">語法</span><span class="sxs-lookup"><span data-stu-id="40fcb-104">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="40fcb-105">參數</span><span class="sxs-lookup"><span data-stu-id="40fcb-105">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="40fcb-106">在所要求的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="40fcb-106">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="40fcb-107">在儲存在 PE 檔案之 COFF 檔案標頭中的日期時間戳記。</span><span class="sxs-lookup"><span data-stu-id="40fcb-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="40fcb-108">在[`SizeOfImage`] 欄位儲存在 PE 檔案的 COFF 選擇性檔案標頭中。</span><span class="sxs-lookup"><span data-stu-id="40fcb-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="40fcb-109">脫銷要求之模組的控制碼。</span><span class="sxs-lookup"><span data-stu-id="40fcb-109">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="40fcb-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="40fcb-110">Return Value</span></span>

<span data-ttu-id="40fcb-111">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="40fcb-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="40fcb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40fcb-112">HRESULT</span></span>|<span data-ttu-id="40fcb-113">描述</span><span class="sxs-lookup"><span data-stu-id="40fcb-113">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="40fcb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="40fcb-114">S_OK</span></span>|<span data-ttu-id="40fcb-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="40fcb-115">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="40fcb-116">例外狀況</span><span class="sxs-lookup"><span data-stu-id="40fcb-116">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="40fcb-117">備註</span><span class="sxs-lookup"><span data-stu-id="40fcb-117">Remarks</span></span>

<span data-ttu-id="40fcb-118">`ProvideLibrary` 可讓偵錯工具提供用來偵測特定 CLR 檔案（例如 mscordbi.dll 和 mscordacwks）所需的模組。</span><span class="sxs-lookup"><span data-stu-id="40fcb-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="40fcb-119">模組控制碼必須保持有效，直到呼叫[ICLRDebugging：： CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)方法指出它們可能被釋放為止，此時呼叫端會負責釋放控制碼。</span><span class="sxs-lookup"><span data-stu-id="40fcb-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="40fcb-120">偵錯工具可能會使用任何可用的方法來尋找或購買偵錯工具模組。</span><span class="sxs-lookup"><span data-stu-id="40fcb-120">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40fcb-121">這項功能可讓 API 呼叫端提供包含可執行檔的模組，以及可能的惡意程式碼。</span><span class="sxs-lookup"><span data-stu-id="40fcb-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="40fcb-122">作為安全性預防措施，呼叫端不應該使用 `ProvideLibrary` 來散發不願意自行執行的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="40fcb-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="40fcb-123">如果在已發行的程式庫（例如 mscordbi.dll 或 mscordacwks）中發現嚴重的安全性問題，則可以修補填充碼來辨識檔案的錯誤版本。</span><span class="sxs-lookup"><span data-stu-id="40fcb-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="40fcb-124">填充碼接著可以發出已修補之檔案版本的要求，並在回應任何要求時，拒絕不正確的版本。</span><span class="sxs-lookup"><span data-stu-id="40fcb-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="40fcb-125">只有在使用者已修補新版本的填充碼時，才會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="40fcb-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="40fcb-126">未修補的版本將會保持易受攻擊。</span><span class="sxs-lookup"><span data-stu-id="40fcb-126">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="40fcb-127">需求</span><span class="sxs-lookup"><span data-stu-id="40fcb-127">Requirements</span></span>

<span data-ttu-id="40fcb-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="40fcb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="40fcb-129">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40fcb-129">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="40fcb-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40fcb-130">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="40fcb-131">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40fcb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="40fcb-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="40fcb-132">See also</span></span>

- [<span data-ttu-id="40fcb-133">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="40fcb-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="40fcb-134">偵錯</span><span class="sxs-lookup"><span data-stu-id="40fcb-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
