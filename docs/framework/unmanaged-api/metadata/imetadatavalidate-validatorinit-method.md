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
ms.openlocfilehash: e2f54e11906cd4ba1440e220530f2ca5b9de769f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708552"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="7bb85-102">IMetaDataValidate::ValidatorInit 方法</span><span class="sxs-lookup"><span data-stu-id="7bb85-102">IMetaDataValidate::ValidatorInit Method</span></span>

<span data-ttu-id="7bb85-103">設定會指定目前中繼資料範圍內模組類型的旗標，並註冊對於驗證錯誤的指定回呼方法。</span><span class="sxs-lookup"><span data-stu-id="7bb85-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb85-104">語法</span><span class="sxs-lookup"><span data-stu-id="7bb85-104">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bb85-105">參數</span><span class="sxs-lookup"><span data-stu-id="7bb85-105">Parameters</span></span>  

 `dwModule`  
 <span data-ttu-id="7bb85-106">在 [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) 列舉的值，這個值會指定目前中繼資料範圍中的模組類型。</span><span class="sxs-lookup"><span data-stu-id="7bb85-106">[in] A value of the [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="7bb85-107">在 [IUnknown](/cpp/atl/iunknown) 實例的指標，可作為驗證錯誤的函數回呼。</span><span class="sxs-lookup"><span data-stu-id="7bb85-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb85-108">需求</span><span class="sxs-lookup"><span data-stu-id="7bb85-108">Requirements</span></span>  

 <span data-ttu-id="7bb85-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bb85-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb85-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="7bb85-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bb85-111">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="7bb85-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7bb85-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb85-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb85-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bb85-113">See also</span></span>

- [<span data-ttu-id="7bb85-114">IMetaDataValidate 介面</span><span class="sxs-lookup"><span data-stu-id="7bb85-114">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)
