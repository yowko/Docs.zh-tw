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
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate 方法
驗證指定的可攜式執行檔 (PE) 或 Microsoft intermediate language (MSIL) 檔案。  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="parameters"></a>參數  
 `veh`  
 [in]指標`IVEHandler`處理驗證錯誤的執行個體。  
  
 `pAppDomain`  
 [in]此檔案會載入應用程式定義域的指標。  
  
 `ulFlags`  
 [in]位元組合[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值，指出應該執行的驗證。  
  
 `ulMaxError`  
 [in]結束驗證之前允許的錯誤數目上限。  
  
 `token`  
 [in]不使用。  
  
 `fileName`  
 [in]字串，指定要驗證檔案的名稱。  
  
 `pe`  
 [in]此檔案會儲存記憶體緩衝區的指標。  
  
 `ulSize`  
 [in]以位元組為單位，以驗證檔案的大小。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** IValidator.idl, IValidator.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
