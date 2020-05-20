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
ms.openlocfilehash: fbaf45da0902ded8a2f7bf0d470aaed3b5f531aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617122"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="99fba-102">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="99fba-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="99fba-103">取得與指定的進程控制碼相關聯之 common language runtime （CLR）的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="99fba-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="99fba-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="99fba-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99fba-105">語法</span><span class="sxs-lookup"><span data-stu-id="99fba-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99fba-106">參數</span><span class="sxs-lookup"><span data-stu-id="99fba-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="99fba-107">在進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="99fba-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="99fba-108">脫銷一個緩衝區，其中包含成功完成方法時的版本號碼字串。</span><span class="sxs-lookup"><span data-stu-id="99fba-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="99fba-109">在版本緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="99fba-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="99fba-110">脫銷版本號碼字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="99fba-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99fba-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="99fba-111">Return Value</span></span>  
 <span data-ttu-id="99fba-112">這個方法會傳回標準元件物件模型（COM）錯誤碼（如 Winerror.h 中所定義），以及下列值。</span><span class="sxs-lookup"><span data-stu-id="99fba-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="99fba-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="99fba-113">Return code</span></span>|<span data-ttu-id="99fba-114">說明</span><span class="sxs-lookup"><span data-stu-id="99fba-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="99fba-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="99fba-115">S_OK</span></span>|<span data-ttu-id="99fba-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="99fba-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="99fba-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="99fba-117">E_INVALIDARG</span></span>|<span data-ttu-id="99fba-118">`pVersion`是 null 且不 `cchBuffer` 是 null，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="99fba-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="99fba-119">-或-</span><span class="sxs-lookup"><span data-stu-id="99fba-119">-or-</span></span><br /><br /> <span data-ttu-id="99fba-120">`hProcess`不是處理常式的有效控制碼。</span><span class="sxs-lookup"><span data-stu-id="99fba-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="99fba-121">-或-</span><span class="sxs-lookup"><span data-stu-id="99fba-121">-or-</span></span><br /><br /> <span data-ttu-id="99fba-122">未載入 CLR。</span><span class="sxs-lookup"><span data-stu-id="99fba-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="99fba-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="99fba-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="99fba-124">`cchBuffer`為 null 或小於版本字串的長度。</span><span class="sxs-lookup"><span data-stu-id="99fba-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="99fba-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="99fba-125">E_NOTIMPL</span></span>|<span data-ttu-id="99fba-126">這個方法無法在 Microsoft Windows 95、Microsoft Windows 98 或 Microsoft Windows Millennium Edition 作業系統上使用。</span><span class="sxs-lookup"><span data-stu-id="99fba-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99fba-127">需求</span><span class="sxs-lookup"><span data-stu-id="99fba-127">Requirements</span></span>  
 <span data-ttu-id="99fba-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99fba-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99fba-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="99fba-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99fba-130">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="99fba-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99fba-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99fba-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fba-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99fba-132">See also</span></span>

- [<span data-ttu-id="99fba-133">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="99fba-133">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="99fba-134">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="99fba-134">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="99fba-135">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="99fba-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
