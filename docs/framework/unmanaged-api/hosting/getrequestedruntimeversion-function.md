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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ee737f4c6d34e77996f5ba08ce4d84132a99238
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207327"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="78925-102">GetRequestedRuntimeVersion 函式</span><span class="sxs-lookup"><span data-stu-id="78925-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="78925-103">取得 common language runtime (CLR) 所指定的應用程式要求的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="78925-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="78925-104">如果未安裝該版本，取得要求的版本之前已安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="78925-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="78925-105">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="78925-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78925-106">語法</span><span class="sxs-lookup"><span data-stu-id="78925-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78925-107">參數</span><span class="sxs-lookup"><span data-stu-id="78925-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="78925-108">[in]應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="78925-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="78925-109">[out]這種緩衝區包含成功完成時的版本號碼字串。</span><span class="sxs-lookup"><span data-stu-id="78925-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="78925-110">[in]版本緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="78925-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="78925-111">[out]版本號碼的字串長度的指標。</span><span class="sxs-lookup"><span data-stu-id="78925-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78925-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="78925-112">Return Value</span></span>  
 <span data-ttu-id="78925-113">中所定義 WinError.h，除了下列的值，這個方法會傳回標準的元件物件模型 (COM) 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="78925-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="78925-114">傳回碼</span><span class="sxs-lookup"><span data-stu-id="78925-114">Return code</span></span>|<span data-ttu-id="78925-115">描述</span><span class="sxs-lookup"><span data-stu-id="78925-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="78925-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="78925-116">S_OK</span></span>|<span data-ttu-id="78925-117">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="78925-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="78925-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="78925-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="78925-119">版本緩衝區不夠大，無法儲存版本字串。</span><span class="sxs-lookup"><span data-stu-id="78925-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="78925-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="78925-120">E_POINTER</span></span>|`pdwLength` <span data-ttu-id="78925-121">為 null。</span><span class="sxs-lookup"><span data-stu-id="78925-121">is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78925-122">需求</span><span class="sxs-lookup"><span data-stu-id="78925-122">Requirements</span></span>  
 <span data-ttu-id="78925-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78925-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78925-124">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78925-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78925-125">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78925-125">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="78925-126">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="78925-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="78925-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78925-127">See also</span></span>

- [<span data-ttu-id="78925-128">GetRequestedRuntimeInfo 函式</span><span class="sxs-lookup"><span data-stu-id="78925-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="78925-129">GetVersionFromProcess 函式</span><span class="sxs-lookup"><span data-stu-id="78925-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="78925-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="78925-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
