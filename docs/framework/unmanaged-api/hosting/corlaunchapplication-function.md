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
ms.openlocfilehash: e01698d2d8491b2496bb664c13dca97964cd1481
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136938"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="41f32-102">CorLaunchApplication 函式</span><span class="sxs-lookup"><span data-stu-id="41f32-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="41f32-103">使用指定的資訊清單和其他應用程式資料，在指定的網路路徑啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="41f32-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="41f32-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="41f32-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f32-105">語法</span><span class="sxs-lookup"><span data-stu-id="41f32-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="41f32-106">參數</span><span class="sxs-lookup"><span data-stu-id="41f32-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="41f32-107">在[HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)列舉的值，指定正在啟動應用程式的主控制項類型。</span><span class="sxs-lookup"><span data-stu-id="41f32-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="41f32-108">在正在啟動之應用程式的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="41f32-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="41f32-109">在應用程式的資訊清單路徑數目。</span><span class="sxs-lookup"><span data-stu-id="41f32-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="41f32-110">在字串陣列，其中每個都指定要啟動之應用程式的資訊清單路徑。</span><span class="sxs-lookup"><span data-stu-id="41f32-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="41f32-111">在正在啟動之應用程式的啟用資料項目數目。</span><span class="sxs-lookup"><span data-stu-id="41f32-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="41f32-112">在字串陣列，其中每一個都是要啟動之應用程式的啟用資料項目。</span><span class="sxs-lookup"><span data-stu-id="41f32-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="41f32-113">脫銷已載入應用程式之進程的相關資訊指標。</span><span class="sxs-lookup"><span data-stu-id="41f32-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41f32-114">需求</span><span class="sxs-lookup"><span data-stu-id="41f32-114">Requirements</span></span>  
 <span data-ttu-id="41f32-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41f32-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41f32-116">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="41f32-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41f32-117">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="41f32-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41f32-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41f32-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f32-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="41f32-119">See also</span></span>

- [<span data-ttu-id="41f32-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="41f32-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
