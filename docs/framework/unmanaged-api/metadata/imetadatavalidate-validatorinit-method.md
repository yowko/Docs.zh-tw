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
ms.openlocfilehash: 687f33c364f9730a554a41ade1ca2b78e33ffdc5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489672"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="7ee5a-102">IMetaDataValidate::ValidatorInit 方法</span><span class="sxs-lookup"><span data-stu-id="7ee5a-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="7ee5a-103">設定會指定目前中繼資料範圍內模組類型的旗標，並註冊對於驗證錯誤的指定回呼方法。</span><span class="sxs-lookup"><span data-stu-id="7ee5a-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee5a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ee5a-104">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ee5a-105">參數</span><span class="sxs-lookup"><span data-stu-id="7ee5a-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="7ee5a-106">在[CorValidatorModuleType](corvalidatormoduletype-enumeration.md)列舉的值，指定目前中繼資料範圍中的模組類型。</span><span class="sxs-lookup"><span data-stu-id="7ee5a-106">[in] A value of the [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="7ee5a-107">在[IUnknown](/cpp/atl/iunknown)實例的指標，做為驗證錯誤的函數回呼。</span><span class="sxs-lookup"><span data-stu-id="7ee5a-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ee5a-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="7ee5a-108">Requirements</span></span>  
 <span data-ttu-id="7ee5a-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee5a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ee5a-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="7ee5a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ee5a-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="7ee5a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ee5a-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ee5a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee5a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ee5a-113">See also</span></span>

- [<span data-ttu-id="7ee5a-114">IMetaDataValidate 介面</span><span class="sxs-lookup"><span data-stu-id="7ee5a-114">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)
