---
title: ICLRDataTarget 介面
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: 51b246e45b8bbdf809f5e90ac2bc29ca724751fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113496"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget 介面
提供與 common language runtime （CLR）的目標專案互動的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCurrentThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|取得目前線程的作業系統識別碼。|  
|[GetImageBase 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|取得指定之映射的基底記憶體位址。|  
|[GetMachineType 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|取得目標進程所使用之指令集種類的識別碼。|  
|[GetPointerSize 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|取得目前目標的指標大小（以位元組為單位）。|  
|[GetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|取得具有指定識別碼之執行緒內容的指標。|  
|[GetTLSValue 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|取得指定執行緒之指定索引處的執行緒區域儲存區（TLS）中的值。|  
|[ReadVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|將資料從指定的虛擬記憶體位址讀入指定的緩衝區。|  
|[Request 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|由 common language runtime （CLR）資料存取服務呼叫，以要求作業，如實作為所定義。|  
|[SetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|設定目標進程中指定之執行緒的目前內容。|  
|[SetTLSValue 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|設定目標進程中指定執行緒的執行緒區域儲存區（TLS）中的值。|  
|[WriteVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|將資料從指定的緩衝區寫入指定的虛擬記憶體位址。|  
  
## <a name="remarks"></a>備註  
 API 用戶端（也就是偵錯工具）必須針對特定目標專案，實作為適當的介面。 例如，即時處理序的實作與記憶體傾印的實作不同。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl，ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRDataTarget2 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
