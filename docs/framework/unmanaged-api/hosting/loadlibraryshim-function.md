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
ms.openlocfilehash: 9ab44ce8f51620d83084d1dd16e98b2b310feb76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968943"
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="02402-102">LoadLibraryShim 函式</span><span class="sxs-lookup"><span data-stu-id="02402-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="02402-103">載入包含在 .NET Framework 可轉散發套件中的指定 DLL 版本。</span><span class="sxs-lookup"><span data-stu-id="02402-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="02402-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="02402-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="02402-105">請改用[ICLRRuntimeInfo:: LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="02402-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02402-106">語法</span><span class="sxs-lookup"><span data-stu-id="02402-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02402-107">參數</span><span class="sxs-lookup"><span data-stu-id="02402-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="02402-108">在以零結束的字串, 表示要從 .NET Framework 程式庫載入的 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="02402-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="02402-109">在以零結束的字串, 表示要載入之 DLL 的版本。</span><span class="sxs-lookup"><span data-stu-id="02402-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="02402-110">如果`szVersion`為 null, 則選取要載入的版本是最新版本的指定 DLL, 小於第4版。</span><span class="sxs-lookup"><span data-stu-id="02402-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="02402-111">也就是說, 如果`szVersion`為 null, 則會忽略等於或大於第4版的所有版本, 如果未安裝低於第4版的版本, 則無法載入 DLL。</span><span class="sxs-lookup"><span data-stu-id="02402-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="02402-112">這是為了確保 .NET Framework 4 的安裝不會影響既有的應用程式或元件。</span><span class="sxs-lookup"><span data-stu-id="02402-112">This is to ensure that installation of the .NET Framework 4 does not affect pre-existing applications or components.</span></span> <span data-ttu-id="02402-113">請參閱 CLR team blog 中的進入[進程內 SxS 和遷移快速](https://go.microsoft.com/fwlink/?LinkId=200329)入門。</span><span class="sxs-lookup"><span data-stu-id="02402-113">See the entry [In-Proc SxS and Migration Quick Start](https://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="02402-114">保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="02402-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="02402-115">脫銷模組控制碼的指標。</span><span class="sxs-lookup"><span data-stu-id="02402-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02402-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="02402-116">Return Value</span></span>  
 <span data-ttu-id="02402-117">這個方法會傳回標準元件物件模型 (COM) 錯誤碼 (如 Winerror.h 中所定義), 以及下列值。</span><span class="sxs-lookup"><span data-stu-id="02402-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="02402-118">傳回碼</span><span class="sxs-lookup"><span data-stu-id="02402-118">Return code</span></span>|<span data-ttu-id="02402-119">描述</span><span class="sxs-lookup"><span data-stu-id="02402-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="02402-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="02402-120">S_OK</span></span>|<span data-ttu-id="02402-121">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="02402-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="02402-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="02402-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="02402-123">載入`szDllName`需要載入 common language runtime (CLR), 而且無法載入必要的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="02402-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02402-124">備註</span><span class="sxs-lookup"><span data-stu-id="02402-124">Remarks</span></span>  
 <span data-ttu-id="02402-125">此函式是用來載入包含在 .NET Framework 可轉散發套件中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="02402-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="02402-126">它不會載入使用者產生的 Dll。</span><span class="sxs-lookup"><span data-stu-id="02402-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02402-127">從 .NET Framework 版本2.0 開始, 載入融合 .dll 會導致載入 CLR。</span><span class="sxs-lookup"><span data-stu-id="02402-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="02402-128">這是因為融合 .dll 中的函式現在是執行時間所提供的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="02402-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02402-129">需求</span><span class="sxs-lookup"><span data-stu-id="02402-129">Requirements</span></span>  
 <span data-ttu-id="02402-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02402-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02402-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="02402-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02402-132">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02402-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02402-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02402-133">See also</span></span>

- [<span data-ttu-id="02402-134">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="02402-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
