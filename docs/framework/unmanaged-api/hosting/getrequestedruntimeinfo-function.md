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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1290aa864a3f65e549bc26173dcd23648b8dee90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074881"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="63f19-102">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="63f19-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="63f19-103">取得 common language runtime (CLR) 應用程式所要求的版本和目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="63f19-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="63f19-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63f19-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f19-105">語法</span><span class="sxs-lookup"><span data-stu-id="63f19-105">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="63f19-106">參數</span><span class="sxs-lookup"><span data-stu-id="63f19-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="63f19-107">[in]應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="63f19-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="63f19-108">[in]字串，指定執行階段的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="63f19-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="63f19-109">[in]相關聯的組態檔的名稱`pExe`。</span><span class="sxs-lookup"><span data-stu-id="63f19-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="63f19-110">[in]一或多個[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="63f19-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="63f19-111">[in]一或多個[RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="63f19-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="63f19-112">[out]這種緩衝區包含成功完成時，執行階段的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="63f19-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="63f19-113">[in]目錄緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="63f19-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="63f19-114">[out]目錄路徑字串的長度指標。</span><span class="sxs-lookup"><span data-stu-id="63f19-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="63f19-115">[out]這種緩衝區包含成功完成時，執行階段的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="63f19-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="63f19-116">[in]版本字串緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="63f19-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="63f19-117">[out]版本字串的長度指標。</span><span class="sxs-lookup"><span data-stu-id="63f19-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63f19-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="63f19-118">Return Value</span></span>  
 <span data-ttu-id="63f19-119">中所定義 WinError.h，除了下列的值，這個方法會傳回標準的元件物件模型 (COM) 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="63f19-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="63f19-120">傳回碼</span><span class="sxs-lookup"><span data-stu-id="63f19-120">Return code</span></span>|<span data-ttu-id="63f19-121">描述</span><span class="sxs-lookup"><span data-stu-id="63f19-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="63f19-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="63f19-122">S_OK</span></span>|<span data-ttu-id="63f19-123">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="63f19-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="63f19-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="63f19-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="63f19-125">無法夠大，無法儲存的目錄路徑的目錄緩衝區。</span><span class="sxs-lookup"><span data-stu-id="63f19-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="63f19-126">-或-</span><span class="sxs-lookup"><span data-stu-id="63f19-126">- or -</span></span><br /><br /> <span data-ttu-id="63f19-127">版本緩衝區不夠大，無法儲存版本字串。</span><span class="sxs-lookup"><span data-stu-id="63f19-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63f19-128">備註</span><span class="sxs-lookup"><span data-stu-id="63f19-128">Remarks</span></span>  
 <span data-ttu-id="63f19-129">`GetRequestedRuntimeInfo`方法會傳回執行階段載入處理序，而不一定是最新版本的電腦上安裝的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="63f19-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="63f19-130">在.NET Framework 2.0 版中，您可以取得最新的安裝版本的相關資訊，使用`GetRequestedRuntimeInfo`方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="63f19-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
-   <span data-ttu-id="63f19-131">指定`pExe`， `pwszVersion`，和`pConfigurationFile`參數為 null。</span><span class="sxs-lookup"><span data-stu-id="63f19-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
-   <span data-ttu-id="63f19-132">指定在 RUNTIME_INFO_UPGRADE_VERSION 旗標`RUNTIME_INFO_FLAGS`列舉型別供`runtimeInfoFlags`參數。</span><span class="sxs-lookup"><span data-stu-id="63f19-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="63f19-133">`GetRequestedRuntimeInfo`方法不會傳回最新的 CLR 版本，在下列情況：</span><span class="sxs-lookup"><span data-stu-id="63f19-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
-   <span data-ttu-id="63f19-134">指定正在載入特定的 CLR 版本的應用程式組態檔存在。</span><span class="sxs-lookup"><span data-stu-id="63f19-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="63f19-135">請注意 .NET Framework 會使用組態檔，即使您指定 null`pConfigurationFile`參數。</span><span class="sxs-lookup"><span data-stu-id="63f19-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
-   <span data-ttu-id="63f19-136">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)方法受呼叫時指定較早的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="63f19-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
-   <span data-ttu-id="63f19-137">針對較早的 CLR 版本所編譯的應用程式目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="63f19-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="63f19-138">針對`runtimeInfoFlags`參數，您可以指定其中一個架構的常數`RUNTIME_INFO_FLAGS`列舉一次：</span><span class="sxs-lookup"><span data-stu-id="63f19-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
-   <span data-ttu-id="63f19-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="63f19-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="63f19-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="63f19-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="63f19-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="63f19-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63f19-142">需求</span><span class="sxs-lookup"><span data-stu-id="63f19-142">Requirements</span></span>  
 <span data-ttu-id="63f19-143">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63f19-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63f19-144">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63f19-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63f19-145">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63f19-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63f19-146">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63f19-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f19-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63f19-147">See also</span></span>

- [<span data-ttu-id="63f19-148">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="63f19-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="63f19-149">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="63f19-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="63f19-150">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="63f19-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
