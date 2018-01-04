---
title: "LoadLibraryShim 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LoadLibraryShim
helpviewer_keywords: LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b8fe8413d0eff332e60508a083f03574e58d7bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="a42b6-102">LoadLibraryShim 函式</span><span class="sxs-lookup"><span data-stu-id="a42b6-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="a42b6-103">載入 DLL 隨附於.NET Framework 可轉散發套件中的指定的版本。</span><span class="sxs-lookup"><span data-stu-id="a42b6-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="a42b6-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a42b6-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="a42b6-105">使用[iclrruntimeinfo:: Loadlibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="a42b6-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a42b6-106">語法</span><span class="sxs-lookup"><span data-stu-id="a42b6-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a42b6-107">參數</span><span class="sxs-lookup"><span data-stu-id="a42b6-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="a42b6-108">[in]零結尾的字串，表示要從.NET Framework 程式庫載入 DLL 的名稱。</span><span class="sxs-lookup"><span data-stu-id="a42b6-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="a42b6-109">[in]零結尾的字串，表示要載入的 dll 版本。</span><span class="sxs-lookup"><span data-stu-id="a42b6-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="a42b6-110">如果`szVersion`是 null，選取為載入指定之 dll 小於第 4 版的最新版本的版本。</span><span class="sxs-lookup"><span data-stu-id="a42b6-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="a42b6-111">如果，亦即，忽略所有的版本等於或大於第 4 版`szVersion`為 null，但如果安裝沒有版本小於第 4 版，則無法載入 DLL。</span><span class="sxs-lookup"><span data-stu-id="a42b6-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="a42b6-112">這是為了確保安裝[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]不會影響現有的應用程式或元件。</span><span class="sxs-lookup"><span data-stu-id="a42b6-112">This is to ensure that installation of the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not affect pre-existing applications or components.</span></span> <span data-ttu-id="a42b6-113">請參閱文章[同處理序 SxS 和移轉快速入門](http://go.microsoft.com/fwlink/?LinkId=200329)CLR team 部落格中。</span><span class="sxs-lookup"><span data-stu-id="a42b6-113">See the entry [In-Proc SxS and Migration Quick Start](http://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="a42b6-114">保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="a42b6-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="a42b6-115">[out]模組的控制代碼指標。</span><span class="sxs-lookup"><span data-stu-id="a42b6-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a42b6-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="a42b6-116">Return Value</span></span>  
 <span data-ttu-id="a42b6-117">這個方法會傳回標準的元件物件模型 (COM) 的錯誤代碼，除了下列的值定義了 WinError.h 中。</span><span class="sxs-lookup"><span data-stu-id="a42b6-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a42b6-118">傳回碼</span><span class="sxs-lookup"><span data-stu-id="a42b6-118">Return code</span></span>|<span data-ttu-id="a42b6-119">描述</span><span class="sxs-lookup"><span data-stu-id="a42b6-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a42b6-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="a42b6-120">S_OK</span></span>|<span data-ttu-id="a42b6-121">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="a42b6-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="a42b6-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="a42b6-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="a42b6-123">載入`szDllName`需要的載入，無法載入 common language runtime (CLR)，以及必要的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="a42b6-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a42b6-124">備註</span><span class="sxs-lookup"><span data-stu-id="a42b6-124">Remarks</span></span>  
 <span data-ttu-id="a42b6-125">此函式用來載入 Dll 隨附的.NET Framework 可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="a42b6-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="a42b6-126">它不會載入使用者產生的 Dll。</span><span class="sxs-lookup"><span data-stu-id="a42b6-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a42b6-127">從.NET Framework 2.0 版開始，載入 Fusion.dll 會造成載入 CLR。</span><span class="sxs-lookup"><span data-stu-id="a42b6-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="a42b6-128">這是因為 Fusion.dll 中的函式現在是包裝函式的實作所提供的執行階段。</span><span class="sxs-lookup"><span data-stu-id="a42b6-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a42b6-129">需求</span><span class="sxs-lookup"><span data-stu-id="a42b6-129">Requirements</span></span>  
 <span data-ttu-id="a42b6-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a42b6-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a42b6-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a42b6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a42b6-132">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a42b6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a42b6-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="a42b6-133">See Also</span></span>  
 [<span data-ttu-id="a42b6-134">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="a42b6-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
