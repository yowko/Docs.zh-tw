---
title: ICLRRuntimeInfo::LoadLibrary 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
ms.openlocfilehash: 09c80c3a56d86943ebe00e5222bb5452ab44e150
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762171"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="61c9d-102">ICLRRuntimeInfo::LoadLibrary 方法</span><span class="sxs-lookup"><span data-stu-id="61c9d-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="61c9d-103">從[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面所代表的 common language RUNTIME （CLR）載入 .NET Framework 程式庫。</span><span class="sxs-lookup"><span data-stu-id="61c9d-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="61c9d-104">這個方法會取代[LoadLibraryShim](loadlibraryshim-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="61c9d-104">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61c9d-105">語法</span><span class="sxs-lookup"><span data-stu-id="61c9d-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61c9d-106">參數</span><span class="sxs-lookup"><span data-stu-id="61c9d-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="61c9d-107">在要載入之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="61c9d-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="61c9d-108">脫銷載入之元件的控制碼。</span><span class="sxs-lookup"><span data-stu-id="61c9d-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61c9d-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="61c9d-109">Return Value</span></span>  
 <span data-ttu-id="61c9d-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="61c9d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="61c9d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61c9d-111">HRESULT</span></span>|<span data-ttu-id="61c9d-112">Description</span><span class="sxs-lookup"><span data-stu-id="61c9d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61c9d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="61c9d-113">S_OK</span></span>|<span data-ttu-id="61c9d-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="61c9d-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="61c9d-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="61c9d-115">E_POINTER</span></span>|<span data-ttu-id="61c9d-116">`pwzDllName` 或 `phndModule` 為 null。</span><span class="sxs-lookup"><span data-stu-id="61c9d-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="61c9d-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="61c9d-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="61c9d-118">沒有足夠的記憶體可用來處理要求。</span><span class="sxs-lookup"><span data-stu-id="61c9d-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61c9d-119">備註</span><span class="sxs-lookup"><span data-stu-id="61c9d-119">Remarks</span></span>  
 <span data-ttu-id="61c9d-120">這個方法只會載入包含在 .NET Framework 可轉散發套件中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="61c9d-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="61c9d-121">它無法載入使用者產生的元件。</span><span class="sxs-lookup"><span data-stu-id="61c9d-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61c9d-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="61c9d-122">Requirements</span></span>  
 <span data-ttu-id="61c9d-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61c9d-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61c9d-124">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="61c9d-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="61c9d-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="61c9d-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61c9d-126">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61c9d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c9d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61c9d-127">See also</span></span>

- [<span data-ttu-id="61c9d-128">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="61c9d-128">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="61c9d-129">裝載介面</span><span class="sxs-lookup"><span data-stu-id="61c9d-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="61c9d-130">裝載</span><span class="sxs-lookup"><span data-stu-id="61c9d-130">Hosting</span></span>](index.md)
