---
title: ICLRRuntimeInfo::GetProcAddress 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: 028cfd51a713d8598598566a5b1edcf3fc70ecfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732056"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="23d6c-102">ICLRRuntimeInfo::GetProcAddress 方法</span><span class="sxs-lookup"><span data-stu-id="23d6c-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>

<span data-ttu-id="23d6c-103">取得從 common language runtime 匯出的指定函式的位址，該函式是與這個介面相關聯 (CLR) 。</span><span class="sxs-lookup"><span data-stu-id="23d6c-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="23d6c-104">這個方法會取代 [GetRealProcAddress](getrealprocaddress-function.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="23d6c-104">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d6c-105">語法</span><span class="sxs-lookup"><span data-stu-id="23d6c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23d6c-106">參數</span><span class="sxs-lookup"><span data-stu-id="23d6c-106">Parameters</span></span>  

 `pszProcName`  
 <span data-ttu-id="23d6c-107">在匯出函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="23d6c-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="23d6c-108">擴展匯出函式的位址。</span><span class="sxs-lookup"><span data-stu-id="23d6c-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23d6c-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="23d6c-109">Return Value</span></span>  

 <span data-ttu-id="23d6c-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="23d6c-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="23d6c-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23d6c-111">HRESULT</span></span>|<span data-ttu-id="23d6c-112">描述</span><span class="sxs-lookup"><span data-stu-id="23d6c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23d6c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="23d6c-113">S_OK</span></span>|<span data-ttu-id="23d6c-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="23d6c-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="23d6c-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="23d6c-115">E_POINTER</span></span>|<span data-ttu-id="23d6c-116">`pszProcName` 或 `ppProc` 為 null。</span><span class="sxs-lookup"><span data-stu-id="23d6c-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="23d6c-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="23d6c-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="23d6c-118">指定的函數不是匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="23d6c-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23d6c-119">備註</span><span class="sxs-lookup"><span data-stu-id="23d6c-119">Remarks</span></span>  

 <span data-ttu-id="23d6c-120">這個方法會使 CLR 載入但未初始化。</span><span class="sxs-lookup"><span data-stu-id="23d6c-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23d6c-121">需求</span><span class="sxs-lookup"><span data-stu-id="23d6c-121">Requirements</span></span>  

 <span data-ttu-id="23d6c-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23d6c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23d6c-123">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="23d6c-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="23d6c-124">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="23d6c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23d6c-125">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23d6c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d6c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23d6c-126">See also</span></span>

- [<span data-ttu-id="23d6c-127">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="23d6c-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="23d6c-128">裝載介面</span><span class="sxs-lookup"><span data-stu-id="23d6c-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="23d6c-129">裝載</span><span class="sxs-lookup"><span data-stu-id="23d6c-129">Hosting</span></span>](index.md)
