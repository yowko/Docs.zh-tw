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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0a5abe8877c8414443fadc00e223df240721132
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget 介面
提供 common language runtime (CLR) 的目標項目互動的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCurrentThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|取得目前執行緒的作業系統識別項。|  
|[GetImageBase 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|取得指定的映像的基底的記憶體位址。|  
|[GetMachineType 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|取得目標處理序正在使用的指令集類型的識別項。|  
|[GetPointerSize 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|取得大小，以位元組為單位的目前目標的指標。|  
|[GetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|取得具有指定識別碼的執行緒內容的指標。|  
|[GetTLSValue 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|執行緒區域儲存區 (TLS) 中取得值，指定執行緒的指定索引處。|  
|[ReadVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|從指定的虛擬記憶體位址將資料讀入指定的緩衝區。|  
|[Request 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|由通用語言執行平台 (CLR) 資料存取服務要求的操作，實作所定義。|  
|[SetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|目標處理序中，設定指定之執行緒的目前內容。|  
|[SetTLSValue 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|執行緒區域儲存區 (TLS) 的目標處理序中指定的執行緒中設定的值。|  
|[WriteVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|將資料從指定的緩衝區寫入指定的虛擬記憶體位址。|  
  
## <a name="remarks"></a>備註  
 API 用戶端 （也就是偵錯工具） 必須實作此介面適用於特定的目標項目。 例如，即時處理序的實作與記憶體傾印的實作不同。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl、 ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRDataTarget2 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
