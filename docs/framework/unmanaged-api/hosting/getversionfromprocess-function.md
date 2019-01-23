---
title: GetVersionFromProcess 函式
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 843236243563ce3dff82726aaab05845fa295b9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518133"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="4a877-102">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="4a877-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="4a877-103">取得 common language runtime (CLR) 與指定的處理序控制代碼相關聯的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4a877-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="4a877-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4a877-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a877-105">語法</span><span class="sxs-lookup"><span data-stu-id="4a877-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a877-106">參數</span><span class="sxs-lookup"><span data-stu-id="4a877-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="4a877-107">[in]處理序控制代碼。</span><span class="sxs-lookup"><span data-stu-id="4a877-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="4a877-108">[out]這種緩衝區包含此方法成功完成時的版本號碼字串。</span><span class="sxs-lookup"><span data-stu-id="4a877-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="4a877-109">[in]版本緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="4a877-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="4a877-110">[out]版本號碼的字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="4a877-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a877-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4a877-111">Return Value</span></span>  
 <span data-ttu-id="4a877-112">中所定義 WinError.h，除了下列的值，這個方法會傳回標準的元件物件模型 (COM) 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="4a877-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="4a877-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="4a877-113">Return code</span></span>|<span data-ttu-id="4a877-114">描述</span><span class="sxs-lookup"><span data-stu-id="4a877-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="4a877-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a877-115">S_OK</span></span>|<span data-ttu-id="4a877-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="4a877-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="4a877-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4a877-117">E_INVALIDARG</span></span>|<span data-ttu-id="4a877-118">`pVersion` 為 null 及`cchBuffer`不是 null，或反之亦然。</span><span class="sxs-lookup"><span data-stu-id="4a877-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="4a877-119">-或-</span><span class="sxs-lookup"><span data-stu-id="4a877-119">-or-</span></span><br /><br /> <span data-ttu-id="4a877-120">`hProcess` 不是有效的控制代碼至處理序。</span><span class="sxs-lookup"><span data-stu-id="4a877-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="4a877-121">-或-</span><span class="sxs-lookup"><span data-stu-id="4a877-121">-or-</span></span><br /><br /> <span data-ttu-id="4a877-122">無法載入 CLR。</span><span class="sxs-lookup"><span data-stu-id="4a877-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="4a877-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4a877-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4a877-124">`cchBuffer` 為 null 或版本字串的長度大於或等於。</span><span class="sxs-lookup"><span data-stu-id="4a877-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="4a877-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4a877-125">E_NOTIMPL</span></span>|<span data-ttu-id="4a877-126">這個方法並不適用於 Microsoft Windows 95、 Microsoft Windows 98 或 Microsoft Windows Millennium Edition 作業系統。</span><span class="sxs-lookup"><span data-stu-id="4a877-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a877-127">需求</span><span class="sxs-lookup"><span data-stu-id="4a877-127">Requirements</span></span>  
 <span data-ttu-id="4a877-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a877-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a877-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a877-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a877-130">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a877-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a877-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a877-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a877-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a877-132">See also</span></span>
- [<span data-ttu-id="4a877-133">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="4a877-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="4a877-134">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="4a877-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="4a877-135">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="4a877-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
