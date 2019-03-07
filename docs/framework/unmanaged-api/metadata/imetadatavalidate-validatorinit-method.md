---
title: IMetaDataValidate::ValidatorInit 方法
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d2018be28cbfe72bb7c989634374b8ab43693e6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491954"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="60df8-102">IMetaDataValidate::ValidatorInit 方法</span><span class="sxs-lookup"><span data-stu-id="60df8-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="60df8-103">設定會指定目前中繼資料範圍內模組類型的旗標，並註冊對於驗證錯誤的指定回呼方法。</span><span class="sxs-lookup"><span data-stu-id="60df8-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60df8-104">語法</span><span class="sxs-lookup"><span data-stu-id="60df8-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60df8-105">參數</span><span class="sxs-lookup"><span data-stu-id="60df8-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="60df8-106">[in]值為[CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md)列舉，指定目前的中繼資料範圍中的模組類型。</span><span class="sxs-lookup"><span data-stu-id="60df8-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="60df8-107">[in]指標[IUnknown](/cpp/atl/iunknown)做為驗證錯誤的函式回呼執行個體。</span><span class="sxs-lookup"><span data-stu-id="60df8-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60df8-108">需求</span><span class="sxs-lookup"><span data-stu-id="60df8-108">Requirements</span></span>  
 <span data-ttu-id="60df8-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60df8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60df8-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="60df8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60df8-111">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="60df8-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60df8-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60df8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60df8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60df8-113">See also</span></span>
- [<span data-ttu-id="60df8-114">IMetaDataValidate 介面</span><span class="sxs-lookup"><span data-stu-id="60df8-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
