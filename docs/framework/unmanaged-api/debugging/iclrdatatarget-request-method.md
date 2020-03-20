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
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179118"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request 方法
由通用語言運行時 （CLR） 資料訪問服務調用，以請求由實現定義的操作。  
  
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
 [在]使用者定義。  
  
 `inBufferSize`  
 [在]用於傳入請求的輸入緩衝區的大小。  
  
 `inBuffer`  
 [在]包含請求的緩衝區。  
  
 `outBufferSize`  
 [在]用於回應的輸出緩衝區的大小。  
  
 `outBuffer`  
 [出]包含回應的緩衝區。  
  
## <a name="remarks"></a>備註  
 該方法`Request`便於添加未指定的自訂操作。 也就是說，此方法提供可擴充性，而無需修訂介面定義。  
  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** ClrData.idl， ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRDataTarget 介面](iclrdatatarget-interface.md)
