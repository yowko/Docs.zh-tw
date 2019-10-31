---
title: CoInitializeEE 函式
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 9e90772ae8c3e6be5744fcccc9901123df871831
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131934"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="27fa1-102">CoInitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="27fa1-102">CoInitializeEE Function</span></span>
<span data-ttu-id="27fa1-103">確保 common language runtime 執行引擎已載入進程中。</span><span class="sxs-lookup"><span data-stu-id="27fa1-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="27fa1-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="27fa1-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="27fa1-105">請改用[ICLRRuntimeHost：： Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="27fa1-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27fa1-106">語法</span><span class="sxs-lookup"><span data-stu-id="27fa1-106">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27fa1-107">參數</span><span class="sxs-lookup"><span data-stu-id="27fa1-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="27fa1-108">在其中一個[COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)列舉常數。</span><span class="sxs-lookup"><span data-stu-id="27fa1-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27fa1-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="27fa1-109">Return Value</span></span>  
 <span data-ttu-id="27fa1-110">這個方法會傳回 Winerror.h 中定義的標準 COM 錯誤碼，以及下表中的值。</span><span class="sxs-lookup"><span data-stu-id="27fa1-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="27fa1-111">傳回碼</span><span class="sxs-lookup"><span data-stu-id="27fa1-111">Return code</span></span>|<span data-ttu-id="27fa1-112">描述</span><span class="sxs-lookup"><span data-stu-id="27fa1-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="27fa1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="27fa1-113">S_OK</span></span>|<span data-ttu-id="27fa1-114">已成功載入執行引擎。</span><span class="sxs-lookup"><span data-stu-id="27fa1-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="27fa1-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="27fa1-115">S_FALSE</span></span>|<span data-ttu-id="27fa1-116">已載入執行引擎。</span><span class="sxs-lookup"><span data-stu-id="27fa1-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="27fa1-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="27fa1-117">E_FAIL</span></span>|<span data-ttu-id="27fa1-118">無法載入執行引擎。</span><span class="sxs-lookup"><span data-stu-id="27fa1-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27fa1-119">備註</span><span class="sxs-lookup"><span data-stu-id="27fa1-119">Remarks</span></span>  
 <span data-ttu-id="27fa1-120">這個方法會載入執行引擎（如果先前尚未載入）。</span><span class="sxs-lookup"><span data-stu-id="27fa1-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27fa1-121">需求</span><span class="sxs-lookup"><span data-stu-id="27fa1-121">Requirements</span></span>  
 <span data-ttu-id="27fa1-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27fa1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27fa1-123">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="27fa1-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27fa1-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="27fa1-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27fa1-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27fa1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27fa1-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="27fa1-126">See also</span></span>

- [<span data-ttu-id="27fa1-127">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="27fa1-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
