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
ms.openlocfilehash: be7d6ce29a9c9c4e3e530df40432b1a4c3b2d389
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136348"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="4cc62-102">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="4cc62-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="4cc62-103">取得指定的應用程式所要求的 common language runtime （CLR）版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4cc62-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="4cc62-104">如果未安裝該版本，會取得所要求版本之前所安裝的最新版本。</span><span class="sxs-lookup"><span data-stu-id="4cc62-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="4cc62-105">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="4cc62-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cc62-106">語法</span><span class="sxs-lookup"><span data-stu-id="4cc62-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cc62-107">參數</span><span class="sxs-lookup"><span data-stu-id="4cc62-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="4cc62-108">在應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="4cc62-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="4cc62-109">脫銷一個緩衝區，其中包含成功完成時的版本號碼字串。</span><span class="sxs-lookup"><span data-stu-id="4cc62-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="4cc62-110">在版本緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="4cc62-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="4cc62-111">脫銷版本號碼字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="4cc62-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cc62-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="4cc62-112">Return Value</span></span>  
 <span data-ttu-id="4cc62-113">這個方法會傳回標準元件物件模型（COM）錯誤碼（如 Winerror.h 中所定義），以及下列值。</span><span class="sxs-lookup"><span data-stu-id="4cc62-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="4cc62-114">傳回碼</span><span class="sxs-lookup"><span data-stu-id="4cc62-114">Return code</span></span>|<span data-ttu-id="4cc62-115">描述</span><span class="sxs-lookup"><span data-stu-id="4cc62-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="4cc62-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="4cc62-116">S_OK</span></span>|<span data-ttu-id="4cc62-117">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="4cc62-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="4cc62-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4cc62-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4cc62-119">版本緩衝區不夠大，無法儲存版本字串。</span><span class="sxs-lookup"><span data-stu-id="4cc62-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="4cc62-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4cc62-120">E_POINTER</span></span>|<span data-ttu-id="4cc62-121">`pdwLength` 為 null。</span><span class="sxs-lookup"><span data-stu-id="4cc62-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4cc62-122">需求</span><span class="sxs-lookup"><span data-stu-id="4cc62-122">Requirements</span></span>  
 <span data-ttu-id="4cc62-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4cc62-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cc62-124">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4cc62-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cc62-125">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="4cc62-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cc62-126">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cc62-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc62-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="4cc62-127">See also</span></span>

- [<span data-ttu-id="4cc62-128">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="4cc62-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="4cc62-129">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="4cc62-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="4cc62-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="4cc62-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
