---
title: 獲取方法源函數（非託管 API 引用）
description: GetMethodOrigin 函數確定聲明方法的類。
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b4609b6649be875aea7dfcf52ba36b1e98ab7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176795"
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin 函式
判斷方法在其中宣告的類別。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a>參數

`vFunc`  
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`wszMethodName`  
[在]正在請求其擁有類的物件的方法的名稱。

`pstrClassName`  
[出]接收擁有 方法的類的名稱。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0 x80041002 | 找不到指定的方法。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一個或多個參數無效。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數包裝對[IWbem ClassObject 的調用：：獲取方法原點](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)方法。

由於類可以從一個或多個基類繼承方法，因此開發人員通常希望確定在其中定義給定方法的類。

在`pstrClassName`調用函數之前，參數不能指向`BSTR`有效，因為這是一個`out`參數;因此，參數在調用函數之前，不能指向該參數。函數返回後，此指標不會處理。

## <a name="requirements"></a>需求  
**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
