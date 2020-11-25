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
ms.openlocfilehash: 24679118e4255282f7da3ff8be2ce9c08250e181
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732043"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="8e1f3-102">ICLRRuntimeInfo::GetRuntimeDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="8e1f3-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>

<span data-ttu-id="8e1f3-103">取得與此介面相關聯之 common language runtime (CLR) 的安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="8e1f3-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="8e1f3-104">這個方法會取代 .NET Framework 版本2.0、3.0 和3.5 中提供的 [GetCORSystemDirectory](getcorsystemdirectory-function.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="8e1f3-104">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e1f3-105">語法</span><span class="sxs-lookup"><span data-stu-id="8e1f3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e1f3-106">參數</span><span class="sxs-lookup"><span data-stu-id="8e1f3-106">Parameters</span></span>  

 `pwzBuffer`  
 <span data-ttu-id="8e1f3-107">擴展傳回 CLR 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="8e1f3-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="8e1f3-108">安裝路徑是完整的;例如，"c:\windows\microsoft.net\framework\v1.0.3705 \\ "。</span><span class="sxs-lookup"><span data-stu-id="8e1f3-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="8e1f3-109">[in，out]指定的大小， `pwzBuffer` 以避免緩衝區溢位。</span><span class="sxs-lookup"><span data-stu-id="8e1f3-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="8e1f3-110">如果 `pwzBuffer` 是 null，則傳回 `pchBuffer` 所需的大小 `pwzBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="8e1f3-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e1f3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e1f3-111">Return Value</span></span>  

 <span data-ttu-id="8e1f3-112">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="8e1f3-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8e1f3-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e1f3-113">HRESULT</span></span>|<span data-ttu-id="8e1f3-114">描述</span><span class="sxs-lookup"><span data-stu-id="8e1f3-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e1f3-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e1f3-115">S_OK</span></span>|<span data-ttu-id="8e1f3-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="8e1f3-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="8e1f3-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8e1f3-117">E_POINTER</span></span>|<span data-ttu-id="8e1f3-118">`pwzBuffer` 或 `pchBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="8e1f3-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e1f3-119">備註</span><span class="sxs-lookup"><span data-stu-id="8e1f3-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e1f3-120">需求</span><span class="sxs-lookup"><span data-stu-id="8e1f3-120">Requirements</span></span>  

 <span data-ttu-id="8e1f3-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e1f3-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e1f3-122">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="8e1f3-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8e1f3-123">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="8e1f3-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e1f3-124">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e1f3-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e1f3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e1f3-125">See also</span></span>

- [<span data-ttu-id="8e1f3-126">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="8e1f3-126">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="8e1f3-127">裝載</span><span class="sxs-lookup"><span data-stu-id="8e1f3-127">Hosting</span></span>](index.md)
