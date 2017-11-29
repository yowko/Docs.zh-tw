---
title: "IValidator::Validate 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 722c6acc7e152a78ba28bc2730b2fdc7e0c45eb0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate 方法
驗證指定的可攜式執行檔 (PE) 或 Microsoft 中繼語言 (MSIL) 檔案。  
  
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
  
#### <a name="parameters"></a>參數  
 `veh`  
 [in]指標`IVEHandler`處理驗證錯誤的執行個體。  
  
 `pAppDomain`  
 [in]應用程式定義域載入該檔案指標。  
  
 `ulFlags`  
 [in]位元組合[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值，表示應該執行的驗證。  
  
 `ulMaxError`  
 [in]結束驗證前，允許的錯誤數目上限。  
  
 `token`  
 [in]未使用。  
  
 `fileName`  
 [in]字串，指定要驗證檔案的名稱。  
  
 `pe`  
 [in]檔案會儲存記憶體緩衝區的指標。  
  
 `ulSize`  
 [in]以位元組為單位來驗證檔案大小。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** IValidator.idl、 IValidator.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 
