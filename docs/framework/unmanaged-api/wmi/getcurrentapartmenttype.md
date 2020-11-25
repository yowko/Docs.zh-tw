---
title: 'GetCurrentApartmentType 函式 (非受控 API 參考) '
description: GetCurrentApartmentType 函式會抓取呼叫端執行所在的單元類型。
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0832867d86b7dda80e037846d9aa66c1d37f87be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726193"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType 函式

擷取呼叫者在其中執行之 Apartment 的型別。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a>參數

`vFunc`  
在此參數未使用。

`ptr`  
在 [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) 實例的指標。

`aptType`  
擴展 [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) 列舉值的指標，指出呼叫端的單元。

## <a name="return-value"></a>傳回值

|常數  |值  |描述  |
|---------|---------|---------|
| `S_OK` | 0 | 函數已順利完成。 |
| `E_FAIL` | 0x80000008 | 呼叫端並未在單元中執行。 |
  
## <a name="remarks"></a>備註

此函數會包裝對 [IComThreadingInfo：： GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) 方法的呼叫。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
