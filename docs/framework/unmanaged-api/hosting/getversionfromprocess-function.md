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
ms.openlocfilehash: da0d159da6eef7745c1fa7f7320d5e1355f6e413
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721877"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="a4805-102">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="a4805-102">GetVersionFromProcess Function</span></span>

<span data-ttu-id="a4805-103">取得與所指定進程控制碼相關聯之 common language runtime (CLR) 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a4805-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="a4805-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="a4805-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4805-105">語法</span><span class="sxs-lookup"><span data-stu-id="a4805-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4805-106">參數</span><span class="sxs-lookup"><span data-stu-id="a4805-106">Parameters</span></span>  

 `hProcess`  
 <span data-ttu-id="a4805-107">在進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="a4805-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="a4805-108">擴展在成功完成方法時包含版本號碼字串的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a4805-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a4805-109">在版本緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="a4805-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="a4805-110">擴展版本號碼字串的長度指標。</span><span class="sxs-lookup"><span data-stu-id="a4805-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4805-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="a4805-111">Return Value</span></span>  

 <span data-ttu-id="a4805-112">除了下列值以外，這個方法會傳回 (COM) 錯誤碼（如 Winerror.h 中所定義）的標準元件物件模型。</span><span class="sxs-lookup"><span data-stu-id="a4805-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a4805-113">傳回碼</span><span class="sxs-lookup"><span data-stu-id="a4805-113">Return code</span></span>|<span data-ttu-id="a4805-114">描述</span><span class="sxs-lookup"><span data-stu-id="a4805-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a4805-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4805-115">S_OK</span></span>|<span data-ttu-id="a4805-116">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="a4805-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="a4805-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a4805-117">E_INVALIDARG</span></span>|<span data-ttu-id="a4805-118">`pVersion` 為 null 且不 `cchBuffer` 是 null，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a4805-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="a4805-119">-或-</span><span class="sxs-lookup"><span data-stu-id="a4805-119">-or-</span></span><br /><br /> <span data-ttu-id="a4805-120">`hProcess` 不是有效的進程控制碼。</span><span class="sxs-lookup"><span data-stu-id="a4805-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="a4805-121">-或-</span><span class="sxs-lookup"><span data-stu-id="a4805-121">-or-</span></span><br /><br /> <span data-ttu-id="a4805-122">CLR 尚未載入。</span><span class="sxs-lookup"><span data-stu-id="a4805-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="a4805-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a4805-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a4805-124">`cchBuffer` 為 null 或小於版本字串的長度。</span><span class="sxs-lookup"><span data-stu-id="a4805-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="a4805-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a4805-125">E_NOTIMPL</span></span>|<span data-ttu-id="a4805-126">Microsoft Windows 95、Microsoft Windows 98 或 Microsoft Windows Millennium Edition 作業系統上無法使用此方法。</span><span class="sxs-lookup"><span data-stu-id="a4805-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4805-127">需求</span><span class="sxs-lookup"><span data-stu-id="a4805-127">Requirements</span></span>  

 <span data-ttu-id="a4805-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4805-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4805-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a4805-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4805-130">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4805-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4805-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4805-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4805-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4805-132">See also</span></span>

- [<span data-ttu-id="a4805-133">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="a4805-133">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="a4805-134">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="a4805-134">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="a4805-135">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="a4805-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
