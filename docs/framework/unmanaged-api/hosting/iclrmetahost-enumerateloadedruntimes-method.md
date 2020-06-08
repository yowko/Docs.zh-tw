---
title: ICLRMetaHost::EnumerateLoadedRuntimes 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 7b09bb9c3abcb23997bfd412c3ea939404e583c1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504169"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="cd3bd-102">ICLRMetaHost::EnumerateLoadedRuntimes 方法</span><span class="sxs-lookup"><span data-stu-id="cd3bd-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="cd3bd-103">傳回列舉，其中包含在給定進程中載入之每個 common language runtime （CLR）版本的有效[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面指標。</span><span class="sxs-lookup"><span data-stu-id="cd3bd-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="cd3bd-104">這個方法會取代[GetVersionFromProcess](getversionfromprocess-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="cd3bd-104">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd3bd-105">語法</span><span class="sxs-lookup"><span data-stu-id="cd3bd-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd3bd-106">參數</span><span class="sxs-lookup"><span data-stu-id="cd3bd-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="cd3bd-107">在要檢查載入的執行時間之進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="cd3bd-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="cd3bd-108">脫銷<xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>對應至處理常式所載入的每個 CLR 之[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面的列舉。</span><span class="sxs-lookup"><span data-stu-id="cd3bd-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd3bd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="cd3bd-109">Return Value</span></span>  
 <span data-ttu-id="cd3bd-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd3bd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cd3bd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd3bd-111">HRESULT</span></span>|<span data-ttu-id="cd3bd-112">說明</span><span class="sxs-lookup"><span data-stu-id="cd3bd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd3bd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd3bd-113">S_OK</span></span>|<span data-ttu-id="cd3bd-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="cd3bd-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="cd3bd-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="cd3bd-115">E_POINTER</span></span>|<span data-ttu-id="cd3bd-116">`ppEnumerator` 為 null。</span><span class="sxs-lookup"><span data-stu-id="cd3bd-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd3bd-117">備註</span><span class="sxs-lookup"><span data-stu-id="cd3bd-117">Remarks</span></span>  
 <span data-ttu-id="cd3bd-118">這個方法會列出所有載入的執行時間，即使它們是使用已被取代的函式（例如[CorBindToRuntime](corbindtoruntime-function.md)）載入也是一樣。</span><span class="sxs-lookup"><span data-stu-id="cd3bd-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd3bd-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="cd3bd-119">Requirements</span></span>  
 <span data-ttu-id="cd3bd-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd3bd-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd3bd-121">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="cd3bd-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cd3bd-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cd3bd-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd3bd-123">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd3bd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd3bd-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd3bd-124">See also</span></span>

- [<span data-ttu-id="cd3bd-125">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="cd3bd-125">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="cd3bd-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="cd3bd-126">Hosting</span></span>](index.md)
