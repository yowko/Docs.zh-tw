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
ms.openlocfilehash: cd1d9e768698115bee22e35699b044e0c3526d2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136316"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="b253b-102">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="b253b-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="b253b-103">取得應用程式所要求之 common language runtime （CLR）的版本和目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="b253b-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="b253b-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="b253b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b253b-105">語法</span><span class="sxs-lookup"><span data-stu-id="b253b-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b253b-106">參數</span><span class="sxs-lookup"><span data-stu-id="b253b-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="b253b-107">在應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="b253b-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="b253b-108">在指定執行時間版本號碼的字串。</span><span class="sxs-lookup"><span data-stu-id="b253b-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="b253b-109">在與 `pExe`相關聯之設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="b253b-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="b253b-110">在一或多個[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="b253b-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="b253b-111">在一或多個[RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="b253b-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="b253b-112">脫銷一個緩衝區，其中包含成功完成時，執行時間的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="b253b-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="b253b-113">在目錄緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="b253b-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="b253b-114">脫銷目錄路徑字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="b253b-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="b253b-115">脫銷包含成功完成時，執行時間版本號碼的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b253b-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="b253b-116">在版本字串緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="b253b-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="b253b-117">脫銷版本字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="b253b-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b253b-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="b253b-118">Return Value</span></span>  
 <span data-ttu-id="b253b-119">這個方法會傳回標準元件物件模型（COM）錯誤碼（如 Winerror.h 中所定義），以及下列值。</span><span class="sxs-lookup"><span data-stu-id="b253b-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="b253b-120">傳回碼</span><span class="sxs-lookup"><span data-stu-id="b253b-120">Return code</span></span>|<span data-ttu-id="b253b-121">描述</span><span class="sxs-lookup"><span data-stu-id="b253b-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b253b-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="b253b-122">S_OK</span></span>|<span data-ttu-id="b253b-123">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="b253b-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="b253b-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b253b-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b253b-125">目錄緩衝區不夠大，無法儲存目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="b253b-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="b253b-126">-或-</span><span class="sxs-lookup"><span data-stu-id="b253b-126">- or -</span></span><br /><br /> <span data-ttu-id="b253b-127">版本緩衝區不夠大，無法儲存版本字串。</span><span class="sxs-lookup"><span data-stu-id="b253b-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b253b-128">備註</span><span class="sxs-lookup"><span data-stu-id="b253b-128">Remarks</span></span>  
 <span data-ttu-id="b253b-129">`GetRequestedRuntimeInfo` 方法會傳回載入進程中之版本的相關執行時間資訊，這不一定是電腦上所安裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="b253b-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="b253b-130">在 .NET Framework 版本2.0 中，您可以使用 `GetRequestedRuntimeInfo` 方法來取得最新已安裝版本的相關資訊，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b253b-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="b253b-131">將 `pExe`、`pwszVersion`和 `pConfigurationFile` 參數指定為 null。</span><span class="sxs-lookup"><span data-stu-id="b253b-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="b253b-132">在 `RUNTIME_INFO_FLAGS` 列舉中指定 `runtimeInfoFlags` 參數的 RUNTIME_INFO_UPGRADE_VERSION 旗標。</span><span class="sxs-lookup"><span data-stu-id="b253b-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="b253b-133">在下列情況下，`GetRequestedRuntimeInfo` 方法不會傳回最新的 CLR 版本：</span><span class="sxs-lookup"><span data-stu-id="b253b-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="b253b-134">指定載入特定 CLR 版本的應用程式佈建檔已存在。</span><span class="sxs-lookup"><span data-stu-id="b253b-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="b253b-135">請注意，即使您為 `pConfigurationFile` 參數指定 null，.NET Framework 還是會使用設定檔。</span><span class="sxs-lookup"><span data-stu-id="b253b-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="b253b-136">呼叫[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)方法時，指定了較早的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="b253b-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="b253b-137">已針對舊版 CLR 版本編譯的應用程式目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="b253b-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="b253b-138">針對 `runtimeInfoFlags` 參數，您一次只能指定一個 `RUNTIME_INFO_FLAGS` 列舉的架構常數：</span><span class="sxs-lookup"><span data-stu-id="b253b-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="b253b-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="b253b-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="b253b-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="b253b-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="b253b-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="b253b-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b253b-142">需求</span><span class="sxs-lookup"><span data-stu-id="b253b-142">Requirements</span></span>  
 <span data-ttu-id="b253b-143">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b253b-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b253b-144">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b253b-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b253b-145">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="b253b-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b253b-146">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b253b-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b253b-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="b253b-147">See also</span></span>

- [<span data-ttu-id="b253b-148">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="b253b-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="b253b-149">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="b253b-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="b253b-150">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="b253b-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
