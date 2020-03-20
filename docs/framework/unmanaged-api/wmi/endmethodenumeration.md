---
title: 結束方法枚舉函數（非託管 API 引用）
description: EndMethodEee）計數函數終止方法枚舉序列。
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 63667d0668f905ded2aedd961be0d1831faf838c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175001"
---
# <a name="endmethodenumeration-function"></a>EndMethodEnumeration 函式
終止以調用[BeginMethodEee 計算函數](beginmethodenumeration.md)開始的枚舉序列。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a>參數

`vFunc`  
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | 0x8004101d | 發生內部錯誤。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數將調用包起來到[IWbemClassObject：：結束方法枚舉](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration)方法。

調用方使用[BeginMethodEee 枚舉函數](beginmethodenumeration.md)開始枚舉序列，然後調用[NextMethod 函數](nextmethod.md )，直到`WBEM_S_NO_MORE_DATA`方法返回 。 調用方通過調用`EndMethodEnumeration`完成序列。 調用方可能通過隨時調用`EndMethodEnumeration`來提前終止枚舉。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
