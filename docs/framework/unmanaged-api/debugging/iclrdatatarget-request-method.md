---
title: ICLRDataTarget::Request 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
ms.openlocfilehash: e5d7a6b9826a734363d6beeb2e3fab8422964558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113346"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request 方法
由 common language runtime （CLR）資料存取服務呼叫，以要求作業，如實作為所定義。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a>參數  
 `reqCode`  
 在使用者定義的。  
  
 `inBufferSize`  
 在輸入緩衝區的大小，用於傳入的要求。  
  
 `inBuffer`  
 在包含要求的緩衝區。  
  
 `outBufferSize`  
 在輸出緩衝區的大小，用於回應。  
  
 `outBuffer`  
 脫銷包含回應的緩衝區。  
  
## <a name="remarks"></a>備註  
 `Request` 方法可協助新增未指定的自訂作業。 也就是說，這個方法會提供擴充性，而不需要修改介面定義。  
  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl，ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
