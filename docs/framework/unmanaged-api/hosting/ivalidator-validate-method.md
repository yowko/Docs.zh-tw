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
ms.openlocfilehash: 688abd210cca193bf03c40f000b74ecb66eb8ede
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008543"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate 方法
驗證指定的可移植執行檔（PE）或 Microsoft 中繼語言（MSIL）檔案。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 在`IVEHandler`處理驗證錯誤之實例的指標。  
  
 `pAppDomain`  
 在載入檔案之應用程式域的指標。  
  
 `ulFlags`  
 在[ValidatorFlags](validatorflags-enumeration.md)值的位元組合，表示應該執行的驗證。  
  
 `ulMaxError`  
 在結束驗證之前允許的錯誤數目上限。  
  
 `token`  
 在未使用。  
  
 `fileName`  
 在字串，指定要驗證的檔案名。  
  
 `pe`  
 在儲存檔案之記憶體緩衝區的指標。  
  
 `ulSize`  
 在要驗證之檔案的大小（以位元組為單位）。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** IValidator .idl，IValidator。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
