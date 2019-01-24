---
title: ICLRDataTarget3 介面
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 974abb123c4c11f6bb512431cea5cc6460a5c55a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654735"
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3 介面
子類別[ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)提供例外狀況資訊的存取權。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetExceptionRecord 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|由通用語言執行平台 (CLR) 資料存取服務呼叫，用於擷取與目標處理序相關聯的例外狀況記錄。|  
|[GetExceptionContextRecord 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|由 CLR 資料存取服務呼叫，用於擷取與目標處理序相關聯的內容記錄。|  
|[GetExceptionThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|由 CLR 資料存取服務呼叫以取得擲出例外狀況的執行緒 ID。|  
  
## <a name="remarks"></a>備註  
 API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。 例如，即時處理序的實作與記憶體傾印的實作不同。 目標可能不支援修改其記憶體區域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl, ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICLRDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [ICLRDataTarget2 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
