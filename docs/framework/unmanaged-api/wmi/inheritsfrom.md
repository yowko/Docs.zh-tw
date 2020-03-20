---
title: 繼承來自函數（非託管 API 引用）
description: 繼承 From 函數確定類或實例是否派生自特定的父類。
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c735c01c45beda8a1ba988a5c580e6b04ae46312
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174936"
---
# <a name="inheritsfrom-function"></a>InheritsFrom 函式
判斷目前類別或執行個體衍生自指定的父類別。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a>參數

`vFunc`  
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`wszAncestor`  
[在]類的名稱。 `wszAncestor`必須指向有效的`LPCWSTR`。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | 當前物件從`wszAncestor`繼承。  |
| `WBEM_S_FALSE` | 1 | 當前物件不從`wszAncestor`繼承。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor` 為 `null`。 |
  
## <a name="remarks"></a>備註

此函數包裝對[IWbem ClassObject 的調用：：繼承方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom)。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
