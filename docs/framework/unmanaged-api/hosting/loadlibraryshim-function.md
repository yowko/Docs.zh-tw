---
title: LoadLibraryShim 函式
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fe1ba15f8a9f8ee79582158209049c1e502a61d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418651"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="c9216-102">LoadLibraryShim 函式</span><span class="sxs-lookup"><span data-stu-id="c9216-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="c9216-103">載入的 DLL 隨附於.NET Framework 可轉散發套件中指定的版本。</span><span class="sxs-lookup"><span data-stu-id="c9216-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="c9216-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c9216-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="c9216-105">使用[iclrruntimeinfo:: Loadlibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="c9216-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9216-106">語法</span><span class="sxs-lookup"><span data-stu-id="c9216-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9216-107">參數</span><span class="sxs-lookup"><span data-stu-id="c9216-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="c9216-108">[in]零結尾的字串，表示要載入從.NET Framework 程式庫 DLL 的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9216-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="c9216-109">[in]零結尾的字串，表示要載入的 dll 版本。</span><span class="sxs-lookup"><span data-stu-id="c9216-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="c9216-110">如果`szVersion`是 null，選取 載入為指定的 DLL 是小於第 4 版的最新版本的版本。</span><span class="sxs-lookup"><span data-stu-id="c9216-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="c9216-111">如果，亦即忽略所有版本等於或大於第 4 版`szVersion`為 null，但如果已安裝任何版本小於第 4 版，無法載入 DLL。</span><span class="sxs-lookup"><span data-stu-id="c9216-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="c9216-112">這是為了確保安裝[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]不會影響現有的應用程式或元件。</span><span class="sxs-lookup"><span data-stu-id="c9216-112">This is to ensure that installation of the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not affect pre-existing applications or components.</span></span> <span data-ttu-id="c9216-113">請參閱文章[In-proc SxS 並快速開始進行移轉](https://go.microsoft.com/fwlink/?LinkId=200329)CLR 小組的部落格。</span><span class="sxs-lookup"><span data-stu-id="c9216-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="c9216-114">保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="c9216-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="c9216-115">[out]模組的控制代碼指標。</span><span class="sxs-lookup"><span data-stu-id="c9216-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9216-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="c9216-116">Return Value</span></span>  
 <span data-ttu-id="c9216-117">中所定義 WinError.h，除了下列的值，這個方法會傳回標準的元件物件模型 (COM) 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="c9216-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="c9216-118">傳回碼</span><span class="sxs-lookup"><span data-stu-id="c9216-118">Return code</span></span>|<span data-ttu-id="c9216-119">描述</span><span class="sxs-lookup"><span data-stu-id="c9216-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c9216-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9216-120">S_OK</span></span>|<span data-ttu-id="c9216-121">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="c9216-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="c9216-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="c9216-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="c9216-123">正在載入`szDllName`需要的載入 common language runtime (CLR)，以及必要的 CLR 版本無法載入。</span><span class="sxs-lookup"><span data-stu-id="c9216-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9216-124">備註</span><span class="sxs-lookup"><span data-stu-id="c9216-124">Remarks</span></span>  
 <span data-ttu-id="c9216-125">此函式用來載入 Dll 隨附於.NET Framework 可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="c9216-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="c9216-126">它不會載入使用者產生的 Dll。</span><span class="sxs-lookup"><span data-stu-id="c9216-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9216-127">從.NET Framework 2.0 版開始，載入 Fusion.dll 造成載入 CLR。</span><span class="sxs-lookup"><span data-stu-id="c9216-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="c9216-128">這是因為 Fusion.dll 中的函式現在是包裝函式執行階段所提供的實作。</span><span class="sxs-lookup"><span data-stu-id="c9216-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9216-129">需求</span><span class="sxs-lookup"><span data-stu-id="c9216-129">Requirements</span></span>  
 <span data-ttu-id="c9216-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9216-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9216-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9216-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9216-132">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9216-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9216-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9216-133">See Also</span></span>  
 [<span data-ttu-id="c9216-134">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="c9216-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
