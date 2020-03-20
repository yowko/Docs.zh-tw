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
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178122"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="c36e8-102">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="c36e8-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="c36e8-103">獲取與指定進程控制碼關聯的通用語言運行時 （CLR） 的版本號。</span><span class="sxs-lookup"><span data-stu-id="c36e8-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="c36e8-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="c36e8-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c36e8-105">語法</span><span class="sxs-lookup"><span data-stu-id="c36e8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c36e8-106">參數</span><span class="sxs-lookup"><span data-stu-id="c36e8-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="c36e8-107">[在]進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="c36e8-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="c36e8-108">[出]在成功完成方法後包含版本號字串的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c36e8-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c36e8-109">[在]版本緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="c36e8-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="c36e8-110">[出]指向版本號字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="c36e8-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c36e8-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="c36e8-111">Return Value</span></span>  
 <span data-ttu-id="c36e8-112">此方法返回 WinError.h 中定義的標準元件物件模型 （COM） 錯誤代碼，以及以下值。</span><span class="sxs-lookup"><span data-stu-id="c36e8-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="c36e8-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="c36e8-113">Return code</span></span>|<span data-ttu-id="c36e8-114">描述</span><span class="sxs-lookup"><span data-stu-id="c36e8-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c36e8-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="c36e8-115">S_OK</span></span>|<span data-ttu-id="c36e8-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="c36e8-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="c36e8-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c36e8-117">E_INVALIDARG</span></span>|<span data-ttu-id="c36e8-118">`pVersion`為空，`cchBuffer`不為空，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="c36e8-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="c36e8-119">-或-</span><span class="sxs-lookup"><span data-stu-id="c36e8-119">-or-</span></span><br /><br /> <span data-ttu-id="c36e8-120">`hProcess`不是進程的有效控制碼。</span><span class="sxs-lookup"><span data-stu-id="c36e8-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="c36e8-121">-或-</span><span class="sxs-lookup"><span data-stu-id="c36e8-121">-or-</span></span><br /><br /> <span data-ttu-id="c36e8-122">未載入 CLR。</span><span class="sxs-lookup"><span data-stu-id="c36e8-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="c36e8-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c36e8-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c36e8-124">`cchBuffer`為空或小於版本字串的長度。</span><span class="sxs-lookup"><span data-stu-id="c36e8-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="c36e8-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c36e8-125">E_NOTIMPL</span></span>|<span data-ttu-id="c36e8-126">此方法在 Microsoft Windows 95、微軟 Windows 98 或 Microsoft Windows 千年版作業系統上不可用。</span><span class="sxs-lookup"><span data-stu-id="c36e8-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c36e8-127">需求</span><span class="sxs-lookup"><span data-stu-id="c36e8-127">Requirements</span></span>  
 <span data-ttu-id="c36e8-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c36e8-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c36e8-129">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c36e8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c36e8-130">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c36e8-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c36e8-131">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c36e8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c36e8-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c36e8-132">See also</span></span>

- [<span data-ttu-id="c36e8-133">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="c36e8-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="c36e8-134">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="c36e8-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="c36e8-135">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="c36e8-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
