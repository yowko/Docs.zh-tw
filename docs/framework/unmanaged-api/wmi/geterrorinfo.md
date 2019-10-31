---
title: GetErrorInfo 函式（非受控 API 參考）
description: GetErrorInfo 函數會從先前的函式呼叫抓取錯誤資訊。
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 062dc62dfe53af3bf5158cb1add0897eccc1df60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102619"
---
# <a name="geterrorinfo-function"></a>GetErrorInfo 函式
從上一個函式呼叫擷取錯誤資訊。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a>傳回值

如果函式呼叫成功，則為[IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)物件的指標，如果失敗，則為 `null`。
  
## <a name="remarks"></a>備註

此函式會包裝對[IComThreadingInfo：： GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)方法的呼叫。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .def  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
