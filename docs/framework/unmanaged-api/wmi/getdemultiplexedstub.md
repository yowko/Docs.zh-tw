---
title: 獲取多工Stub函數（非託管 API 引用）
description: GetDe多工Stub函數創建一個物件轉寄站接收器，以説明用戶端接收來自 Windows 管理的非同步調用。
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
ms.openlocfilehash: d15fed261db2ca2cda6dbf824dc9cb0d5c56eed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174962"
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
[在]指向用戶端在進程中實現[IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)的指標。

`isLocal`  
[在]指示事件是否為本地的標誌 （`true`;否則， `false`.

`ppObject`  
[出]物件轉寄站接收器，用於説明用戶端接收來自 Windows 管理的非同步調用。

## <a name="return-value"></a>傳回值

如果函數成功，則傳回值為`S_OK`（0）。

如果函數失敗，傳回值是非零錯誤代碼。 要獲取擴展的錯誤資訊，請致電[GetErrorInfo](geterrorinfo.md)函數。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
