---
title: ICLRRuntimeInfo::GetRuntimeDirectory 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f366e736c90ffd8cf588af3a6e5f6240426b9980
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434521"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="1b838-102">ICLRRuntimeInfo::GetRuntimeDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="1b838-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="1b838-103">取得 common language runtime (CLR) 此介面相關聯的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="1b838-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="1b838-104">這個方法會取代[GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) .NET framework 2.0、 3.0 和 3.5 中所提供的函式。</span><span class="sxs-lookup"><span data-stu-id="1b838-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b838-105">語法</span><span class="sxs-lookup"><span data-stu-id="1b838-105">Syntax</span></span>  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b838-106">參數</span><span class="sxs-lookup"><span data-stu-id="1b838-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="1b838-107">[out]傳回 CLR 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="1b838-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="1b838-108">安裝路徑是完整名稱。例如，"c:\windows\microsoft.net\framework\v1.0.3705\\"。</span><span class="sxs-lookup"><span data-stu-id="1b838-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="1b838-109">[in、 out]指定的大小`pwzBuffer`以避免緩衝區滿溢。</span><span class="sxs-lookup"><span data-stu-id="1b838-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="1b838-110">如果`pwzBuffer`為 null，`pchBuffer`傳回的所需的大小`pwzBuffer`。</span><span class="sxs-lookup"><span data-stu-id="1b838-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b838-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="1b838-111">Return Value</span></span>  
 <span data-ttu-id="1b838-112">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="1b838-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1b838-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b838-113">HRESULT</span></span>|<span data-ttu-id="1b838-114">描述</span><span class="sxs-lookup"><span data-stu-id="1b838-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b838-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b838-115">S_OK</span></span>|<span data-ttu-id="1b838-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="1b838-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="1b838-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1b838-117">E_POINTER</span></span>|<span data-ttu-id="1b838-118">`pwzBuffer` 或 `pchBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="1b838-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b838-119">備註</span><span class="sxs-lookup"><span data-stu-id="1b838-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b838-120">需求</span><span class="sxs-lookup"><span data-stu-id="1b838-120">Requirements</span></span>  
 <span data-ttu-id="1b838-121">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b838-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b838-122">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1b838-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1b838-123">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1b838-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b838-124">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b838-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b838-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b838-125">See Also</span></span>  
 [<span data-ttu-id="1b838-126">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="1b838-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="1b838-127">裝載</span><span class="sxs-lookup"><span data-stu-id="1b838-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
