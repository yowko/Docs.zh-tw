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
ms.openlocfilehash: 1fba06360a0c31e0a7fa3e61de9793bad14650fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127500"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="eb2d8-102">IValidator::Validate 方法</span><span class="sxs-lookup"><span data-stu-id="eb2d8-102">IValidator::Validate Method</span></span>
<span data-ttu-id="eb2d8-103">驗證指定的可攜式執行檔 (PE) 或 Microsoft intermediate language (MSIL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="eb2d8-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb2d8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="eb2d8-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb2d8-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="eb2d8-106">[in]指標`IVEHandler`處理驗證錯誤的執行個體。</span><span class="sxs-lookup"><span data-stu-id="eb2d8-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="eb2d8-107">[in]此檔案會載入應用程式定義域的指標。</span><span class="sxs-lookup"><span data-stu-id="eb2d8-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="eb2d8-108">[in]位元組合[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值，指出應該執行的驗證。</span><span class="sxs-lookup"><span data-stu-id="eb2d8-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="eb2d8-109">[in]結束驗證之前允許的錯誤數目上限。</span><span class="sxs-lookup"><span data-stu-id="eb2d8-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="eb2d8-110">[in]不使用。</span><span class="sxs-lookup"><span data-stu-id="eb2d8-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="eb2d8-111">[in]字串，指定要驗證檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="eb2d8-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="eb2d8-112">[in]此檔案會儲存記憶體緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="eb2d8-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="eb2d8-113">[in]以位元組為單位，以驗證檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="eb2d8-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb2d8-114">需求</span><span class="sxs-lookup"><span data-stu-id="eb2d8-114">Requirements</span></span>  
 <span data-ttu-id="eb2d8-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb2d8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb2d8-116">**標頭：** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="eb2d8-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="eb2d8-117">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eb2d8-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb2d8-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb2d8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
