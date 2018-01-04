---
title: "GetVersionFromProcess 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetVersionFromProcess
helpviewer_keywords: GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db5054ab9b71eb93005fc0315acba82d807487ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="d3ee1-102">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="d3ee1-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="d3ee1-103">取得 common language runtime (CLR) 與指定的處理序控制代碼相關聯的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="d3ee1-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3ee1-105">語法</span><span class="sxs-lookup"><span data-stu-id="d3ee1-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3ee1-106">參數</span><span class="sxs-lookup"><span data-stu-id="d3ee1-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="d3ee1-107">[in]處理程序控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="d3ee1-108">[out]這種緩衝區包含此方法成功完成時的版本號碼字串。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d3ee1-109">[in]版本緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="d3ee1-110">[out]指標的版本號碼字串的長度。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3ee1-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d3ee1-111">Return Value</span></span>  
 <span data-ttu-id="d3ee1-112">這個方法會傳回標準的元件物件模型 (COM) 的錯誤代碼，除了下列的值定義了 WinError.h 中。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="d3ee1-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="d3ee1-113">Return code</span></span>|<span data-ttu-id="d3ee1-114">描述</span><span class="sxs-lookup"><span data-stu-id="d3ee1-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d3ee1-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3ee1-115">S_OK</span></span>|<span data-ttu-id="d3ee1-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="d3ee1-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d3ee1-117">E_INVALIDARG</span></span>|<span data-ttu-id="d3ee1-118">`pVersion`為 null 和`cchBuffer`不是 null，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="d3ee1-119">-或-</span><span class="sxs-lookup"><span data-stu-id="d3ee1-119">-or-</span></span><br /><br /> <span data-ttu-id="d3ee1-120">`hProcess`不是有效的處理常式至處理序。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="d3ee1-121">-或-</span><span class="sxs-lookup"><span data-stu-id="d3ee1-121">-or-</span></span><br /><br /> <span data-ttu-id="d3ee1-122">未載入 CLR。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="d3ee1-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d3ee1-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d3ee1-124">`cchBuffer`為 null 或小於版本字串的長度。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="d3ee1-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d3ee1-125">E_NOTIMPL</span></span>|<span data-ttu-id="d3ee1-126">無法在 Microsoft Windows 95、 Microsoft Windows 98、 或 Microsoft Windows Me 作業系統上使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3ee1-127">需求</span><span class="sxs-lookup"><span data-stu-id="d3ee1-127">Requirements</span></span>  
 <span data-ttu-id="d3ee1-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3ee1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3ee1-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3ee1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3ee1-130">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3ee1-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3ee1-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3ee1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ee1-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="d3ee1-132">See Also</span></span>  
 [<span data-ttu-id="d3ee1-133">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="d3ee1-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="d3ee1-134">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="d3ee1-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="d3ee1-135">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="d3ee1-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
