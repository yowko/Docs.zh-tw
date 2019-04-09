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
ms.openlocfilehash: 18f1a4ede1a362860df1271835600e7b867eac00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127760"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="67091-102">CoInitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="67091-102">CoInitializeEE Function</span></span>
<span data-ttu-id="67091-103">可確保 common language runtime 執行引擎會載入處理序。</span><span class="sxs-lookup"><span data-stu-id="67091-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="67091-104">此函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="67091-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="67091-105">使用[iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="67091-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67091-106">語法</span><span class="sxs-lookup"><span data-stu-id="67091-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67091-107">參數</span><span class="sxs-lookup"><span data-stu-id="67091-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="67091-108">[in]其中一個[COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md)列舉常數。</span><span class="sxs-lookup"><span data-stu-id="67091-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67091-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="67091-109">Return Value</span></span>  
 <span data-ttu-id="67091-110">定義在 Winerror.h 和下表中的值，這個方法會傳回標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="67091-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="67091-111">傳回碼</span><span class="sxs-lookup"><span data-stu-id="67091-111">Return code</span></span>|<span data-ttu-id="67091-112">描述</span><span class="sxs-lookup"><span data-stu-id="67091-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="67091-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="67091-113">S_OK</span></span>|<span data-ttu-id="67091-114">執行引擎已順利載入。</span><span class="sxs-lookup"><span data-stu-id="67091-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="67091-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="67091-115">S_FALSE</span></span>|<span data-ttu-id="67091-116">已載入的執行引擎。</span><span class="sxs-lookup"><span data-stu-id="67091-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="67091-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="67091-117">E_FAIL</span></span>|<span data-ttu-id="67091-118">無法載入的執行引擎。</span><span class="sxs-lookup"><span data-stu-id="67091-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67091-119">備註</span><span class="sxs-lookup"><span data-stu-id="67091-119">Remarks</span></span>  
 <span data-ttu-id="67091-120">如果先前尚未載入，這個方法會載入執行引擎。</span><span class="sxs-lookup"><span data-stu-id="67091-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67091-121">需求</span><span class="sxs-lookup"><span data-stu-id="67091-121">Requirements</span></span>  
 <span data-ttu-id="67091-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67091-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67091-123">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="67091-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67091-124">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="67091-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="67091-125">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="67091-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="67091-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67091-126">See also</span></span>

- [<span data-ttu-id="67091-127">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="67091-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
