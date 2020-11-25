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
ms.openlocfilehash: 0d3e6a95d8fd71a67b97923dac53c1f615dfe666
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703417"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget 介面

提供與 common language runtime (CLR) 的目標專案互動的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCurrentThreadID 方法](iclrdatatarget-getcurrentthreadid-method.md)|取得目前線程的作業系統識別碼。|  
|[GetImageBase 方法](iclrdatatarget-getimagebase-method.md)|取得指定之影像的基底記憶體位址。|  
|[GetMachineType 方法](iclrdatatarget-getmachinetype-method.md)|取得目標進程正在使用之指令集種類的識別碼。|  
|[GetPointerSize 方法](iclrdatatarget-getpointersize-method.md)|取得目前目標指標的大小（以位元組為單位）。|  
|[GetThreadContext 方法](iclrdatatarget-getthreadcontext-method.md)|取得具有指定識別碼之執行緒內容的指標。|  
|[GetTLSValue 方法](iclrdatatarget-gettlsvalue-method.md)|取得執行緒區域儲存區中的值， (TLS) 位於指定之執行緒的指定索引處。|  
|[ReadVirtual 方法](iclrdatatarget-readvirtual-method.md)|將資料從指定的虛擬記憶體位址讀入指定的緩衝區。|  
|[Request 方法](iclrdatatarget-request-method.md)|由 common language runtime 呼叫 (CLR) 資料存取服務來要求作業，如實作為所定義。|  
|[SetThreadContext 方法](iclrdatatarget-setthreadcontext-method.md)|在目標進程中，設定指定之執行緒的目前內容。|  
|[SetTLSValue 方法](iclrdatatarget-settlsvalue-method.md)|設定執行緒區域儲存區中的值， (目標進程中指定之執行緒的 TLS) 。|  
|[WriteVirtual 方法](iclrdatatarget-writevirtual-method.md)|將資料從指定的緩衝區寫入至指定的虛擬記憶體位址。|  
  
## <a name="remarks"></a>備註  

 API 用戶端 (也就是偵錯工具) 必須適當地針對特定目標專案執行這個介面。 例如，即時處理序的實作與記憶體傾印的實作不同。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl、ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRDataTarget2 介面](iclrdatatarget2-interface.md)
- [偵錯介面](debugging-interfaces.md)
