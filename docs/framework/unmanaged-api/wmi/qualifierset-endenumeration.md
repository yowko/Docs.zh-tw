---
title: QualifierSet_EndEnumeration函數（非託管 API 引用）
description: QualifierSet_EndEnumeration函數終止枚舉。
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c606580ff2e02c5659c14b134b1a17a65651952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176743"
---
# <a name="qualifierset_endenumeration-function"></a>QualifierSet_EndEnumeration 函式
終止從調用[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)函數開始的枚舉。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr
);
```  

## <a name="parameters"></a>參數

`vFunc`  
[在]此參數未使用。

`ptr`[在]指向[IWbem 限定詞集實例的](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，也可以將其定義為代碼中的常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數包裝對[IWbem 限定詞集：：結束枚舉方法的](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration)調用。

建議使用此調用，但不是必需的。 它立即釋放與枚舉關聯的資源。

## <a name="requirements"></a>需求  

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
**標題：** WMINet_Utils.idl  
  
**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
