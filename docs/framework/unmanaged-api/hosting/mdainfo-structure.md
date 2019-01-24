---
title: MDAInfo 結構
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d48c3d701b0369ab00150625c26d94f4111b2d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607208"
---
# <a name="mdainfo-structure"></a>MDAInfo 結構
提供有關的詳細資料`Event_MDAFired`事件，這會觸發建立的 managed 偵錯助理 (MDA)。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`lpMDACaption`|目前的 MDA 的標題。 標題描述的觸發的失敗類型`Event_MDAFired`事件。|  
|`lpMDAMessage`|目前的 MDA 所提供的輸出訊息。|  
  
## <a name="remarks"></a>備註  
 Managed 偵錯助理 (Mda) 會在執行階段執行引擎中偵錯輔助工具，能夠搭配 common language runtime (CLR) 執行工作，例如識別無效的條件或傾印的狀態相關的其他資訊引擎。 Mda 會產生 XML 訊息，否則很難攔截事件。 它們是特別適用於偵錯 managed 和 unmanaged 程式碼之間的轉換。  
  
 觸發程序建立的 MDA 事件引發時，執行階段會採取下列步驟：  
  
-   如果主機尚未註冊[IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)藉由呼叫的執行個體[iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)收到的通知`Event_MDAFired`事件，執行階段會繼續進行其預設值，非託管的行為。  
  
-   如果主機已登錄這個事件處理常式，執行階段會檢查是否要將偵錯工具附加至處理程序。 如果是，執行階段會中斷偵錯工具。 當偵錯工具繼續時，它會呼叫到主機。 如果沒有偵錯工具附加時，執行階段會呼叫`IActionOnCLREvent::OnEvent`，並將傳遞的指標`MDAInfo`執行個體做為`data`參數。  
  
 若要啟用 Mda，然後啟用 MDA 時收到通知，可以選擇主應用程式。 這會讓主機覆寫預設行為，並中止 managed 的執行緒引發事件，以避免損毀處理序狀態。 如需使用 Mda 的詳細資訊，請參閱 < [Managed 偵錯助理診斷錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
