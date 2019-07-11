---
title: CorLaunchApplication 函式
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9861de733a9acb43c7e2a4b4941f9945fc5f0ba7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758369"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="58732-102">CorLaunchApplication 函式</span><span class="sxs-lookup"><span data-stu-id="58732-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="58732-103">啟動指定的網路路徑，使用指定的資訊清單和其他應用程式資料的應用程式。</span><span class="sxs-lookup"><span data-stu-id="58732-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="58732-104">此函式已被取代，在.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="58732-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58732-105">語法</span><span class="sxs-lookup"><span data-stu-id="58732-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="58732-106">參數</span><span class="sxs-lookup"><span data-stu-id="58732-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="58732-107">[in]值為[HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)列舉，指定正在啟動應用程式的主控件的型別。</span><span class="sxs-lookup"><span data-stu-id="58732-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="58732-108">[in]正在啟動應用程式的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="58732-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="58732-109">[in]應用程式資訊清單路徑數目。</span><span class="sxs-lookup"><span data-stu-id="58732-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="58732-110">[in]字串陣列，每一個都會指定要啟動之應用程式資訊清單的路徑。</span><span class="sxs-lookup"><span data-stu-id="58732-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="58732-111">[in]正在啟動之應用程式啟用資料的項目數目。</span><span class="sxs-lookup"><span data-stu-id="58732-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="58732-112">[in]字串陣列，每個都是要啟動之應用程式的啟用資料的項目。</span><span class="sxs-lookup"><span data-stu-id="58732-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="58732-113">[out]程序中載入應用程式的相關資訊的指標。</span><span class="sxs-lookup"><span data-stu-id="58732-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58732-114">需求</span><span class="sxs-lookup"><span data-stu-id="58732-114">Requirements</span></span>  
 <span data-ttu-id="58732-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58732-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58732-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58732-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58732-117">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58732-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58732-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58732-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58732-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58732-119">See also</span></span>

- [<span data-ttu-id="58732-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="58732-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
