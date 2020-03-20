---
title: 獲取當前公寓類型函數（非託管 API 參考）
description: GetCurrent公寓類型函數檢索調用方正在其中執行的公寓類型。
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
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176821"
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
[在]此參數未使用。

`ptr`  
[在]指向[IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)實例的指標。

`aptType`  
[出]指向[APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype)枚舉值的指標，指示調用方的公寓。

## <a name="return-value"></a>傳回值

|持續性  |值  |描述  |
|---------|---------|---------|
| `S_OK` | 0 | 功能已成功完成。 |
| `E_FAIL` | 0x80000008 | 調用方未在公寓中執行。 |
  
## <a name="remarks"></a>備註

此函數將調用包起來到[IComThreadingInfo：：獲取當前公寓類型](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
