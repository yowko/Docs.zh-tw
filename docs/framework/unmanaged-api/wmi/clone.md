---
title: 複製函式 （Unmanaged API 參考）
description: 複製函數會傳回目前的完整複本的新物件。
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5841c89cf394502f68381dfed42593c9debdcb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="clone-function"></a>複製函式
傳回目前物件的完整複本的新物件。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`ppCopy`  
[out]新的物件已完成的單獨`ptr`。 這個引數不可為`null`如果它接收的目前物件的複本。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `null` 已指定為參數，而且不合法，在這種用法。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可供複製物件。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx)方法。

複製的物件是 COM 物件的參考計數為 1。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
