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
ms.openlocfilehash: 76c033b11f3212241827d74f4fe18ee881f20b64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127042"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="00786-102">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="00786-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="00786-103">取得與指定的進程控制碼相關聯之 common language runtime （CLR）的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="00786-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="00786-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="00786-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00786-105">語法</span><span class="sxs-lookup"><span data-stu-id="00786-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00786-106">參數</span><span class="sxs-lookup"><span data-stu-id="00786-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="00786-107">在進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="00786-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="00786-108">脫銷一個緩衝區，其中包含成功完成方法時的版本號碼字串。</span><span class="sxs-lookup"><span data-stu-id="00786-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="00786-109">在版本緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="00786-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="00786-110">脫銷版本號碼字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="00786-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00786-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="00786-111">Return Value</span></span>  
 <span data-ttu-id="00786-112">這個方法會傳回標準元件物件模型（COM）錯誤碼（如 Winerror.h 中所定義），以及下列值。</span><span class="sxs-lookup"><span data-stu-id="00786-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="00786-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="00786-113">Return code</span></span>|<span data-ttu-id="00786-114">描述</span><span class="sxs-lookup"><span data-stu-id="00786-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="00786-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="00786-115">S_OK</span></span>|<span data-ttu-id="00786-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="00786-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="00786-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="00786-117">E_INVALIDARG</span></span>|<span data-ttu-id="00786-118">`pVersion` 為 null，且 `cchBuffer` 不是 null，或反之亦然。</span><span class="sxs-lookup"><span data-stu-id="00786-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="00786-119">-或-</span><span class="sxs-lookup"><span data-stu-id="00786-119">-or-</span></span><br /><br /> <span data-ttu-id="00786-120">`hProcess` 不是有效的進程控制碼。</span><span class="sxs-lookup"><span data-stu-id="00786-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="00786-121">-或-</span><span class="sxs-lookup"><span data-stu-id="00786-121">-or-</span></span><br /><br /> <span data-ttu-id="00786-122">未載入 CLR。</span><span class="sxs-lookup"><span data-stu-id="00786-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="00786-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="00786-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="00786-124">`cchBuffer` 為 null 或小於版本字串的長度。</span><span class="sxs-lookup"><span data-stu-id="00786-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="00786-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="00786-125">E_NOTIMPL</span></span>|<span data-ttu-id="00786-126">這個方法無法在 Microsoft Windows 95、Microsoft Windows 98 或 Microsoft Windows Millennium Edition 作業系統上使用。</span><span class="sxs-lookup"><span data-stu-id="00786-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00786-127">需求</span><span class="sxs-lookup"><span data-stu-id="00786-127">Requirements</span></span>  
 <span data-ttu-id="00786-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00786-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00786-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="00786-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00786-130">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="00786-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00786-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00786-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00786-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="00786-132">See also</span></span>

- [<span data-ttu-id="00786-133">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="00786-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="00786-134">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="00786-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="00786-135">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="00786-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
