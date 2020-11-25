---
title: CLRCreateInstance 函式
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
ms.openlocfilehash: 3c7a14f828e55310435a99693c1195f2f0dd40c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711672"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="2d453-102">CLRCreateInstance 函式</span><span class="sxs-lookup"><span data-stu-id="2d453-102">CLRCreateInstance Function</span></span>

<span data-ttu-id="2d453-103">提供三個介面的其中一個： [ICLRMetaHost](iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)或 [ICLRDebugging](../debugging/iclrdebugging-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="2d453-103">Provides one of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d453-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d453-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d453-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d453-105">Parameters</span></span>  

 `clsid`  
 <span data-ttu-id="2d453-106">在三個類別識別碼的其中一個： CLSID_CLRMetaHost、CLSID_CLRMetaHostPolicy 或 CLSID_CLRDebugging。</span><span class="sxs-lookup"><span data-stu-id="2d453-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="2d453-107">在 (Iid) 的三個介面識別碼之一： IID_ICLRMetaHost、IID_ICLRMetaHostPolicy 或 IID_ICLRDebugging。</span><span class="sxs-lookup"><span data-stu-id="2d453-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="2d453-108">擴展下列三個介面之一： [ICLRMetaHost](iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)或 [ICLRDebugging](../debugging/iclrdebugging-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="2d453-108">[out] One of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d453-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d453-109">Return Value</span></span>  

 <span data-ttu-id="2d453-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="2d453-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2d453-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d453-111">HRESULT</span></span>|<span data-ttu-id="2d453-112">描述</span><span class="sxs-lookup"><span data-stu-id="2d453-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d453-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d453-113">S_OK</span></span>|<span data-ttu-id="2d453-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="2d453-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="2d453-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2d453-115">E_POINTER</span></span>|<span data-ttu-id="2d453-116">`ppInterface` 為 null。</span><span class="sxs-lookup"><span data-stu-id="2d453-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d453-117">備註</span><span class="sxs-lookup"><span data-stu-id="2d453-117">Remarks</span></span>  

 <span data-ttu-id="2d453-118">下表顯示和支援的組合 `clsid` `riid` 。</span><span class="sxs-lookup"><span data-stu-id="2d453-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="2d453-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="2d453-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="2d453-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="2d453-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="2d453-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="2d453-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="2d453-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="2d453-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="2d453-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="2d453-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="2d453-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="2d453-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="2d453-125">下列程式碼示範如何使用 `CLRCreateInstance` 來取得這三個介面：</span><span class="sxs-lookup"><span data-stu-id="2d453-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2d453-126">需求</span><span class="sxs-lookup"><span data-stu-id="2d453-126">Requirements</span></span>  

 <span data-ttu-id="2d453-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d453-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d453-128">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="2d453-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2d453-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="2d453-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d453-130">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d453-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d453-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d453-131">See also</span></span>

- [<span data-ttu-id="2d453-132">裝載</span><span class="sxs-lookup"><span data-stu-id="2d453-132">Hosting</span></span>](index.md)
