---
title: IValidator::FormatEventInfo 方法
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17217146d8e5ed53feb8305ca4ac16c8f96ddeb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653851"
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo 方法
取得對應至指定的驗證錯誤的錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a>參數  
 `hVECode`  
 [in]HRESULT 值傳遞給驗證的錯誤處理常式。  
  
 `Context`  
 [in]A`VEContext`執行個體，其中包含驗證錯誤的內容資訊。  
  
 `msg`  
 [in、 out]字串，包含傳回的錯誤訊息。  
  
 `ulMaxLength`  
 [in]錯誤訊息的最大長度。  
  
 `psa`  
 [in]安全陣列，包含描述錯誤的其他參數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** IValidator.idl, IValidator.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

