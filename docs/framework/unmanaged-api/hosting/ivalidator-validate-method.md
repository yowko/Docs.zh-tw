---
title: IValidator::Validate 方法
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf2c343db459879ca95372e104aee68b22dee6b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440612"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="a5dfe-102">IValidator::Validate 方法</span><span class="sxs-lookup"><span data-stu-id="a5dfe-102">IValidator::Validate Method</span></span>
<span data-ttu-id="a5dfe-103">驗證指定的可攜式執行檔 (PE) 或 Microsoft 中繼語言 (MSIL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="a5dfe-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5dfe-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5dfe-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5dfe-105">參數</span><span class="sxs-lookup"><span data-stu-id="a5dfe-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="a5dfe-106">[in]指標`IVEHandler`處理驗證錯誤的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a5dfe-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="a5dfe-107">[in]應用程式定義域載入該檔案指標。</span><span class="sxs-lookup"><span data-stu-id="a5dfe-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="a5dfe-108">[in]位元組合[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值，表示應該執行的驗證。</span><span class="sxs-lookup"><span data-stu-id="a5dfe-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="a5dfe-109">[in]結束驗證前，允許的錯誤數目上限。</span><span class="sxs-lookup"><span data-stu-id="a5dfe-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="a5dfe-110">[in]未使用。</span><span class="sxs-lookup"><span data-stu-id="a5dfe-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="a5dfe-111">[in]字串，指定要驗證檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a5dfe-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="a5dfe-112">[in]檔案會儲存記憶體緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="a5dfe-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="a5dfe-113">[in]以位元組為單位來驗證檔案大小。</span><span class="sxs-lookup"><span data-stu-id="a5dfe-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5dfe-114">需求</span><span class="sxs-lookup"><span data-stu-id="a5dfe-114">Requirements</span></span>  
 <span data-ttu-id="a5dfe-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5dfe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5dfe-116">**標頭：** IValidator.idl、 IValidator.h</span><span class="sxs-lookup"><span data-stu-id="a5dfe-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="a5dfe-117">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a5dfe-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5dfe-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5dfe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5dfe-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5dfe-119">See Also</span></span>  
 
