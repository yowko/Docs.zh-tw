---
title: GetRequestedRuntimeInfo 函式
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
ms.openlocfilehash: b120b854e1787824808dd64d95b0fa78ba6c9fa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705484"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="9cb12-102">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="9cb12-102">GetRequestedRuntimeInfo Function</span></span>

<span data-ttu-id="9cb12-103">取得應用程式要求的 common language runtime (CLR) 的版本和目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="9cb12-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="9cb12-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="9cb12-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb12-105">語法</span><span class="sxs-lookup"><span data-stu-id="9cb12-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,
    [in]  LPCWSTR  pwszVersion,
    [in]  LPCWSTR  pConfigurationFile,
    [in]  DWORD    startupFlags,
    [in]  DWORD    runtimeInfoFlags,
    [out] LPWSTR   pDirectory,
    [in]  DWORD    dwDirectory,
    [out] DWORD   *dwDirectoryLength,
    [out] LPWSTR   pVersion,
    [in]  DWORD    cchBuffer,
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cb12-106">參數</span><span class="sxs-lookup"><span data-stu-id="9cb12-106">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="9cb12-107">在應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cb12-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="9cb12-108">在字串，指定執行時間的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="9cb12-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="9cb12-109">在與相關聯的設定檔名稱 `pExe` 。</span><span class="sxs-lookup"><span data-stu-id="9cb12-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="9cb12-110">在一或多個 [STARTUP_FLAGS](startup-flags-enumeration.md) 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9cb12-110">[in] One or more of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="9cb12-111">在一或多個 [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9cb12-111">[in] One or more of the [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="9cb12-112">擴展在成功完成時包含執行時間目錄路徑的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9cb12-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="9cb12-113">在目錄緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="9cb12-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="9cb12-114">擴展目錄路徑字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="9cb12-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="9cb12-115">擴展緩衝區，其中包含成功完成時的執行階段版本號碼。</span><span class="sxs-lookup"><span data-stu-id="9cb12-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="9cb12-116">在版本字串緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="9cb12-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="9cb12-117">擴展版本字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="9cb12-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cb12-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="9cb12-118">Return Value</span></span>  

 <span data-ttu-id="9cb12-119">除了下列值以外，這個方法會傳回 (COM) 錯誤碼（如 Winerror.h 中所定義）的標準元件物件模型。</span><span class="sxs-lookup"><span data-stu-id="9cb12-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="9cb12-120">傳回碼</span><span class="sxs-lookup"><span data-stu-id="9cb12-120">Return code</span></span>|<span data-ttu-id="9cb12-121">描述</span><span class="sxs-lookup"><span data-stu-id="9cb12-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9cb12-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cb12-122">S_OK</span></span>|<span data-ttu-id="9cb12-123">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="9cb12-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="9cb12-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9cb12-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9cb12-125">目錄緩衝區不夠大，無法儲存目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="9cb12-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="9cb12-126">- 或 -</span><span class="sxs-lookup"><span data-stu-id="9cb12-126">- or -</span></span><br /><br /> <span data-ttu-id="9cb12-127">版本緩衝區不夠大，無法儲存版本字串。</span><span class="sxs-lookup"><span data-stu-id="9cb12-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cb12-128">備註</span><span class="sxs-lookup"><span data-stu-id="9cb12-128">Remarks</span></span>  

 <span data-ttu-id="9cb12-129">`GetRequestedRuntimeInfo`方法會傳回載入至進程之版本的執行時間資訊，這不一定是電腦上安裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="9cb12-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="9cb12-130">在 .NET Framework 2.0 版中，您可以使用方法來取得最新安裝版本的相關資訊，如下所示 `GetRequestedRuntimeInfo` ：</span><span class="sxs-lookup"><span data-stu-id="9cb12-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="9cb12-131">將 `pExe` 、 `pwszVersion` 和參數指定 `pConfigurationFile` 為 null。</span><span class="sxs-lookup"><span data-stu-id="9cb12-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="9cb12-132">在參數的列舉中指定 RUNTIME_INFO_UPGRADE_VERSION 旗標 `RUNTIME_INFO_FLAGS` `runtimeInfoFlags` 。</span><span class="sxs-lookup"><span data-stu-id="9cb12-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="9cb12-133">`GetRequestedRuntimeInfo`在下列情況下，方法不會傳回最新的 CLR 版本：</span><span class="sxs-lookup"><span data-stu-id="9cb12-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="9cb12-134">指定載入特定 CLR 版本的應用程式佈建檔存在。</span><span class="sxs-lookup"><span data-stu-id="9cb12-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="9cb12-135">請注意，即使您為參數指定 null，.NET Framework 也會使用設定檔案 `pConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="9cb12-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="9cb12-136">呼叫 [CorBindToRuntimeEx](corbindtoruntimeex-function.md) 方法時指定了較早的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="9cb12-136">The [CorBindToRuntimeEx](corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="9cb12-137">針對先前的 CLR 版本編譯的應用程式目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="9cb12-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="9cb12-138">針對 `runtimeInfoFlags` 參數，您一次只能指定列舉的其中一個架構常數 `RUNTIME_INFO_FLAGS` ：</span><span class="sxs-lookup"><span data-stu-id="9cb12-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="9cb12-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="9cb12-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="9cb12-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="9cb12-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="9cb12-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="9cb12-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cb12-142">需求</span><span class="sxs-lookup"><span data-stu-id="9cb12-142">Requirements</span></span>  

 <span data-ttu-id="9cb12-143">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9cb12-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb12-144">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9cb12-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cb12-145">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9cb12-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cb12-146">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb12-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb12-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cb12-147">See also</span></span>

- [<span data-ttu-id="9cb12-148">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="9cb12-148">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="9cb12-149">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="9cb12-149">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="9cb12-150">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="9cb12-150">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
