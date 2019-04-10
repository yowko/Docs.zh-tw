---
title: QualifierSet_EndEnumeration 函式 （Unmanaged API 參考）
description: QualifierSet_EndEnumeration 函式會終止列舉型別。
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
ms.openlocfilehash: be2dfd6bb521dee14afd3728bdd9c446cb779e85
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149223"
---
# <a name="qualifiersetendenumeration-function"></a>QualifierSet_EndEnumeration 函式
結束藉由呼叫開始列舉[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)函式。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用此參數。

`ptr`   
[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。

## <a name="return-value"></a>傳回值

此函數所傳回的下列值定義在*WbemCli.h*標頭檔，或者您可以定義它做為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration)方法。

這個呼叫是建議，但並非必要。 它會立即釋放與列舉相關聯的資源。

## <a name="requirements"></a>需求  

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
**標頭：** WMINet_Utils.idl  
  
**.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
