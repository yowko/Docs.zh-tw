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
ms.openlocfilehash: 053c94bc540b130510f155506b6fad32f032a475
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449542"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="bcb4c-102">IMetaDataValidate::ValidatorInit 方法</span><span class="sxs-lookup"><span data-stu-id="bcb4c-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="bcb4c-103">設定會指定目前中繼資料範圍內模組類型的旗標，並註冊對於驗證錯誤的指定回呼方法。</span><span class="sxs-lookup"><span data-stu-id="bcb4c-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb4c-104">語法</span><span class="sxs-lookup"><span data-stu-id="bcb4c-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcb4c-105">參數</span><span class="sxs-lookup"><span data-stu-id="bcb4c-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="bcb4c-106">[in]值為[CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md)列舉，指定目前中繼資料範圍內模組類型。</span><span class="sxs-lookup"><span data-stu-id="bcb4c-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="bcb4c-107">[in]指標，<<!--zzxref:IUnknown --> `IUnknown`> 做為驗證錯誤的函式回呼的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bcb4c-107">[in] A pointer to an <<!--zzxref:IUnknown --> `IUnknown`> instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcb4c-108">需求</span><span class="sxs-lookup"><span data-stu-id="bcb4c-108">Requirements</span></span>  
 <span data-ttu-id="bcb4c-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bcb4c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcb4c-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bcb4c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bcb4c-111">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bcb4c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bcb4c-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcb4c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb4c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcb4c-113">See Also</span></span>  
 [<span data-ttu-id="bcb4c-114">IMetaDataValidate 介面</span><span class="sxs-lookup"><span data-stu-id="bcb4c-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
