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
ms.openlocfilehash: ca427439f03d92b20e7714b9724d90b240e9cecb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704067"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="d9965-102">CorLaunchApplication 函式</span><span class="sxs-lookup"><span data-stu-id="d9965-102">CorLaunchApplication Function</span></span>

<span data-ttu-id="d9965-103">使用指定的資訊清單和其他應用程式資料，在指定的網路路徑上啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9965-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="d9965-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="d9965-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9965-105">語法</span><span class="sxs-lookup"><span data-stu-id="d9965-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d9965-106">參數</span><span class="sxs-lookup"><span data-stu-id="d9965-106">Parameters</span></span>  

 `dwClickOnceHost`  
 <span data-ttu-id="d9965-107">在 [HOST_TYPE](host-type-enumeration.md) 列舉值，這個值會指定正在啟動應用程式的主控制項類型。</span><span class="sxs-lookup"><span data-stu-id="d9965-107">[in] A value of the [HOST_TYPE](host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="d9965-108">在即將啟動之應用程式的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="d9965-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="d9965-109">在應用程式的資訊清單路徑數目。</span><span class="sxs-lookup"><span data-stu-id="d9965-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="d9965-110">在字串的陣列，每個字串都指定要啟動之應用程式的資訊清單路徑。</span><span class="sxs-lookup"><span data-stu-id="d9965-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="d9965-111">在即將啟動之應用程式的啟用資料項目數目。</span><span class="sxs-lookup"><span data-stu-id="d9965-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="d9965-112">在字串的陣列，每個字串都是正在啟動之應用程式的啟用資料項目。</span><span class="sxs-lookup"><span data-stu-id="d9965-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="d9965-113">擴展已載入應用程式之進程的相關資訊指標。</span><span class="sxs-lookup"><span data-stu-id="d9965-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9965-114">需求</span><span class="sxs-lookup"><span data-stu-id="d9965-114">Requirements</span></span>  

 <span data-ttu-id="d9965-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9965-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9965-116">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d9965-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9965-117">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9965-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9965-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9965-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9965-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9965-119">See also</span></span>

- [<span data-ttu-id="d9965-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="d9965-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
