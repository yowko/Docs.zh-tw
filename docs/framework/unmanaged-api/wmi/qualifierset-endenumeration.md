---
title: QualifierSet_EndEnumeration 函式（非受控 API 參考）
description: QualifierSet_EndEnumeration 函數會終止列舉。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5a817174ec4c4e4407c19bb1d6d2d852d86dd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798327"
---
# <a name="qualifierset_endenumeration-function"></a>QualifierSet_EndEnumeration 函式
透過呼叫[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)函式，終止開始的列舉。  

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
在未使用此參數。

`ptr`   
在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在*WbemCli*標頭檔中定義的，您也可以在程式碼中將它定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝對[IWbemQualifierSet：： EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration)方法的呼叫。

建議使用此呼叫，但不是必要的。 它會立即釋放與列舉相關聯的資源。

## <a name="requirements"></a>需求  

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
**標頭：** WMINet_Utils.idl  
  
**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
