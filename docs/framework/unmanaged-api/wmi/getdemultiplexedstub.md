---
title: 'GetDemultiplexedStub 函式 (非受控 API 參考) '
description: GetDemultiplexedStub 函式會建立物件轉寄站接收，以協助用戶端接收來自 Windows 管理的非同步呼叫。
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f8f9b56268168bb16c476a9366facd17e8ac44e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730626"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub 函式

建立物件轉寄站接收以協助用戶端從 Windows Management 接收非同步呼叫。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a>參數

`pObject`  
在 [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)之用戶端的同進程執行指標。

`isLocal`  
在指出事件是否為本機 () 的旗標 `true` ，否則為 `false` 。

`ppObject`  
擴展物件轉寄站接收，可協助用戶端接收來自 Windows 管理的非同步呼叫。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為 `S_OK` (0) 。

如果函式失敗，則傳回值為非零的錯誤碼。 若要取得延伸錯誤資訊，請呼叫 [GetErrorInfo](geterrorinfo.md) 函數。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .idl  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
