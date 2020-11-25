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
ms.openlocfilehash: c5c89e0eda6e93e34775c00d5ec8fb4ff0940707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701012"
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo 方法

取得對應到指定之驗證錯誤的錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a>參數  

 `hVECode`  
 在傳遞給驗證錯誤處理常式的 HRESULT 值。  
  
 `Context`  
 在 `VEContext` 實例，其中包含有關驗證錯誤的內容資訊。  
  
 `msg`  
 [in，out]包含傳回之錯誤訊息的字串。  
  
 `ulMaxLength`  
 在錯誤訊息的最大長度。  
  
 `psa`  
 在安全陣列，包含描述錯誤的其他參數。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** IValidator .idl、IValidator。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
