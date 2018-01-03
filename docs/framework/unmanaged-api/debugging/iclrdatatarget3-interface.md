---
title: "ICLRDataTarget3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget3
api_location: mscordbi.dll
api_type: COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64ecb4ca4dfd829bb140c3067085c55a7b86c919
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3 介面
子類別[ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)可提供存取例外狀況資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetExceptionRecord 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|由通用語言執行平台 (CLR) 資料存取服務呼叫，用於擷取與目標處理序相關聯的例外狀況記錄。|  
|[GetExceptionContextRecord 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|由 CLR 資料存取服務呼叫，用於擷取與目標處理序相關聯的內容記錄。|  
|[GetExceptionThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|由 CLR 資料存取服務呼叫以取得擲出例外狀況的執行緒 ID。|  
  
## <a name="remarks"></a>備註  
 API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。 例如，即時處理序的實作與記憶體傾印的實作不同。 目標可能不支援修改其記憶體區域。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl、 ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICLRDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [ICLRDataTarget2 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
