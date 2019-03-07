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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 061a54dd3b3700840f90843a135cf81d8ed81a2e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481153"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="0af2e-102">CoInitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="0af2e-102">CoInitializeEE Function</span></span>
<span data-ttu-id="0af2e-103">可確保 common language runtime 執行引擎會載入處理序。</span><span class="sxs-lookup"><span data-stu-id="0af2e-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="0af2e-104">此函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0af2e-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="0af2e-105">使用[iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="0af2e-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0af2e-106">語法</span><span class="sxs-lookup"><span data-stu-id="0af2e-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0af2e-107">參數</span><span class="sxs-lookup"><span data-stu-id="0af2e-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="0af2e-108">[in]其中一個[COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)列舉常數。</span><span class="sxs-lookup"><span data-stu-id="0af2e-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0af2e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="0af2e-109">Return Value</span></span>  
 <span data-ttu-id="0af2e-110">定義在 Winerror.h 和下表中的值，這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0af2e-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="0af2e-111">傳回碼</span><span class="sxs-lookup"><span data-stu-id="0af2e-111">Return code</span></span>|<span data-ttu-id="0af2e-112">描述</span><span class="sxs-lookup"><span data-stu-id="0af2e-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="0af2e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0af2e-113">S_OK</span></span>|<span data-ttu-id="0af2e-114">執行引擎已順利載入。</span><span class="sxs-lookup"><span data-stu-id="0af2e-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="0af2e-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0af2e-115">S_FALSE</span></span>|<span data-ttu-id="0af2e-116">已載入的執行引擎。</span><span class="sxs-lookup"><span data-stu-id="0af2e-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="0af2e-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0af2e-117">E_FAIL</span></span>|<span data-ttu-id="0af2e-118">無法載入的執行引擎。</span><span class="sxs-lookup"><span data-stu-id="0af2e-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0af2e-119">備註</span><span class="sxs-lookup"><span data-stu-id="0af2e-119">Remarks</span></span>  
 <span data-ttu-id="0af2e-120">如果先前尚未載入，這個方法會載入執行引擎。</span><span class="sxs-lookup"><span data-stu-id="0af2e-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0af2e-121">需求</span><span class="sxs-lookup"><span data-stu-id="0af2e-121">Requirements</span></span>  
 <span data-ttu-id="0af2e-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0af2e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0af2e-123">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0af2e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0af2e-124">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0af2e-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0af2e-125">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0af2e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af2e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0af2e-126">See also</span></span>
- [<span data-ttu-id="0af2e-127">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="0af2e-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
