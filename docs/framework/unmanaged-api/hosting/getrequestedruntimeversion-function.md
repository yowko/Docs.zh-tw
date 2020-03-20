---
title: GetRequestedRuntimeVersion 函式
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 6be0bc5d08f612dcb8ed7d256711e0c4367b9274
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178143"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="c6894-102">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="c6894-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="c6894-103">獲取指定應用程式請求的通用語言運行時 （CLR） 的版本號。</span><span class="sxs-lookup"><span data-stu-id="c6894-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="c6894-104">如果未安裝該版本，請獲取在請求的版本之前安裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="c6894-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="c6894-105">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="c6894-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6894-106">語法</span><span class="sxs-lookup"><span data-stu-id="c6894-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6894-107">參數</span><span class="sxs-lookup"><span data-stu-id="c6894-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="c6894-108">[在]應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6894-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="c6894-109">[出]成功完成後包含版本號字串的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c6894-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c6894-110">[在]版本緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="c6894-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="c6894-111">[出]指向版本號字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="c6894-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6894-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="c6894-112">Return Value</span></span>  
 <span data-ttu-id="c6894-113">此方法返回 WinError.h 中定義的標準元件物件模型 （COM） 錯誤代碼，以及以下值。</span><span class="sxs-lookup"><span data-stu-id="c6894-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="c6894-114">傳回碼</span><span class="sxs-lookup"><span data-stu-id="c6894-114">Return code</span></span>|<span data-ttu-id="c6894-115">描述</span><span class="sxs-lookup"><span data-stu-id="c6894-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c6894-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6894-116">S_OK</span></span>|<span data-ttu-id="c6894-117">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="c6894-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="c6894-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c6894-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c6894-119">版本緩衝區不夠大，無法存儲版本字串。</span><span class="sxs-lookup"><span data-stu-id="c6894-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="c6894-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c6894-120">E_POINTER</span></span>|<span data-ttu-id="c6894-121">`pdwLength` 為 null。</span><span class="sxs-lookup"><span data-stu-id="c6894-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6894-122">需求</span><span class="sxs-lookup"><span data-stu-id="c6894-122">Requirements</span></span>  
 <span data-ttu-id="c6894-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6894-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6894-124">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6894-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6894-125">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6894-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6894-126">**.NET 框架版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6894-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6894-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6894-127">See also</span></span>

- [<span data-ttu-id="c6894-128">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="c6894-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="c6894-129">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="c6894-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="c6894-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="c6894-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
