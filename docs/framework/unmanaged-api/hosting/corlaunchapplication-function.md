---
title: "CorLaunchApplication 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type: COM
f1_keywords: CorLaunchApplication
helpviewer_keywords: CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf4392f7b30a5faa1cb01e24f9262260d9c6e93a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="067d2-102">CorLaunchApplication 函式</span><span class="sxs-lookup"><span data-stu-id="067d2-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="067d2-103">啟動指定的網路路徑，使用指定的資訊清單和其他應用程式資料在應用程式。</span><span class="sxs-lookup"><span data-stu-id="067d2-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="067d2-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="067d2-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="067d2-105">語法</span><span class="sxs-lookup"><span data-stu-id="067d2-105">Syntax</span></span>  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="067d2-106">參數</span><span class="sxs-lookup"><span data-stu-id="067d2-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="067d2-107">[in]值為[HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)指定為啟動應用程式的主機類型的列舉。</span><span class="sxs-lookup"><span data-stu-id="067d2-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="067d2-108">[in]正在啟動應用程式的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="067d2-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="067d2-109">[in]應用程式資訊清單路徑數目。</span><span class="sxs-lookup"><span data-stu-id="067d2-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="067d2-110">[in]字串陣列，其中每個指定的路徑啟動應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="067d2-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="067d2-111">[in]正在啟動應用程式啟用資料的項目數目。</span><span class="sxs-lookup"><span data-stu-id="067d2-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="067d2-112">[in]字串陣列，其中每一個都是應用程式正在啟動的啟用資料項目。</span><span class="sxs-lookup"><span data-stu-id="067d2-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="067d2-113">[out]程序中載入應用程式的相關資訊的指標。</span><span class="sxs-lookup"><span data-stu-id="067d2-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="067d2-114">需求</span><span class="sxs-lookup"><span data-stu-id="067d2-114">Requirements</span></span>  
 <span data-ttu-id="067d2-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="067d2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="067d2-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="067d2-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="067d2-117">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="067d2-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="067d2-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="067d2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="067d2-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="067d2-119">See Also</span></span>  
 [<span data-ttu-id="067d2-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="067d2-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
