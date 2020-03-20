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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178146"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="1a074-102">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="1a074-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="1a074-103">獲取有關應用程式請求的通用語言運行時 （CLR） 的版本和目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="1a074-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="1a074-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="1a074-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a074-105">語法</span><span class="sxs-lookup"><span data-stu-id="1a074-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1a074-106">參數</span><span class="sxs-lookup"><span data-stu-id="1a074-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="1a074-107">[在]應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="1a074-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="1a074-108">[在]指定運行時的版本號的字串。</span><span class="sxs-lookup"><span data-stu-id="1a074-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="1a074-109">[在]與`pExe`關聯的設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="1a074-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="1a074-110">[在]一個或多個[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)枚舉值。</span><span class="sxs-lookup"><span data-stu-id="1a074-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="1a074-111">[在]一個或多個[RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)枚舉值。</span><span class="sxs-lookup"><span data-stu-id="1a074-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="1a074-112">[出]一個緩衝區，在成功完成時包含到運行時的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="1a074-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="1a074-113">[在]目錄緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="1a074-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="1a074-114">[出]指向目錄路徑字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="1a074-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="1a074-115">[出]一個緩衝區，在成功完成時包含運行時的版本號。</span><span class="sxs-lookup"><span data-stu-id="1a074-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="1a074-116">[在]版本字串緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="1a074-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="1a074-117">[出]指向版本字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="1a074-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a074-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="1a074-118">Return Value</span></span>  
 <span data-ttu-id="1a074-119">此方法返回 WinError.h 中定義的標準元件物件模型 （COM） 錯誤代碼，以及以下值。</span><span class="sxs-lookup"><span data-stu-id="1a074-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="1a074-120">傳回碼</span><span class="sxs-lookup"><span data-stu-id="1a074-120">Return code</span></span>|<span data-ttu-id="1a074-121">描述</span><span class="sxs-lookup"><span data-stu-id="1a074-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="1a074-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a074-122">S_OK</span></span>|<span data-ttu-id="1a074-123">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="1a074-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="1a074-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="1a074-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="1a074-125">目錄緩衝區不夠大，無法存儲目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="1a074-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="1a074-126">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1a074-126">- or -</span></span><br /><br /> <span data-ttu-id="1a074-127">版本緩衝區不夠大，無法存儲版本字串。</span><span class="sxs-lookup"><span data-stu-id="1a074-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a074-128">備註</span><span class="sxs-lookup"><span data-stu-id="1a074-128">Remarks</span></span>  
 <span data-ttu-id="1a074-129">該方法`GetRequestedRuntimeInfo`返回有關載入到進程中的版本的運行時資訊，這不一定是電腦上安裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="1a074-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="1a074-130">在 .NET 框架版本 2.0 中，可以使用如下`GetRequestedRuntimeInfo`方法獲取有關最新安裝版本的資訊：</span><span class="sxs-lookup"><span data-stu-id="1a074-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="1a074-131">將`pExe`和`pwszVersion`參數`pConfigurationFile`指定為 null。</span><span class="sxs-lookup"><span data-stu-id="1a074-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="1a074-132">在`runtimeInfoFlags`參數的枚舉中`RUNTIME_INFO_FLAGS`指定RUNTIME_INFO_UPGRADE_VERSION標誌。</span><span class="sxs-lookup"><span data-stu-id="1a074-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="1a074-133">在`GetRequestedRuntimeInfo`以下情況下，該方法不會返回最新的 CLR 版本：</span><span class="sxs-lookup"><span data-stu-id="1a074-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="1a074-134">存在指定載入特定 CLR 版本的應用程式佈建檔。</span><span class="sxs-lookup"><span data-stu-id="1a074-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="1a074-135">請注意，即使為`pConfigurationFile`參數指定 null，.NET 框架也會使用設定檔。</span><span class="sxs-lookup"><span data-stu-id="1a074-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="1a074-136">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)方法稱為指定較早的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="1a074-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="1a074-137">為早期 CLR 版本編譯的應用程式當前正在運行。</span><span class="sxs-lookup"><span data-stu-id="1a074-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="1a074-138">對於參數`runtimeInfoFlags`，一次只能指定枚舉的`RUNTIME_INFO_FLAGS`一個體系結構常量：</span><span class="sxs-lookup"><span data-stu-id="1a074-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="1a074-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="1a074-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="1a074-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="1a074-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="1a074-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="1a074-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a074-142">需求</span><span class="sxs-lookup"><span data-stu-id="1a074-142">Requirements</span></span>  
 <span data-ttu-id="1a074-143">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1a074-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a074-144">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1a074-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a074-145">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a074-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a074-146">**.NET 框架版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a074-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a074-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a074-147">See also</span></span>

- [<span data-ttu-id="1a074-148">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="1a074-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="1a074-149">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="1a074-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="1a074-150">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="1a074-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
