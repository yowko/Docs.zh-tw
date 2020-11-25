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
ms.openlocfilehash: 8e88d90e3291d21888fae7aa162f84b6377658c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730015"
---
# <a name="mdainfo-structure"></a>MDAInfo 結構

提供事件的詳細資料 `Event_MDAFired` ，這會觸發 (MDA) 的 managed 偵錯工具建立。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`lpMDACaption`|目前 MDA 的標題。 標題描述觸發事件的失敗類型 `Event_MDAFired` 。|  
|`lpMDAMessage`|目前的 MDA 所提供的輸出訊息。|  
  
## <a name="remarks"></a>備註  

 Managed 偵錯工具 (Mda) 是與 common language runtime 搭配使用的偵錯工具， (CLR) 來執行工作，例如在執行時間執行引擎中找出不正確條件，或是傾印引擎狀態的其他相關資訊。 Mda 會產生有關事件的 XML 訊息，而這種情況很難進行陷阱。 它們特別適用于在 managed 和非受控碼之間的轉換進行偵錯工具。  
  
 引發觸發建立 MDA 的事件時，執行時間會採取下列步驟：  
  
- 如果主機尚未藉由呼叫[ICLROnEventManager：： RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)註冊[IActionOnCLREvent](iactiononclrevent-interface.md)實例來通知 `Event_MDAFired` 事件，執行時間會繼續其預設的非裝載行為。  
  
- 如果主機已註冊這個事件的處理常式，執行時間會檢查偵錯工具是否已附加至進程。 如果是，執行時間會中斷進入偵錯工具。 當偵錯工具繼續時，它會呼叫主機。 如果未附加任何偵錯工具，執行時間會呼叫 `IActionOnCLREvent::OnEvent` ，並將指標傳遞至 `MDAInfo` 實例作為 `data` 參數。  
  
 主機可以選擇啟用 Mda，並且在啟用 MDA 時收到通知。 這可讓主機有機會覆寫預設行為，並中止引發事件的 managed 執行緒，以防止它損毀進程狀態。 如需使用 Mda 的詳細資訊，請參閱 [診斷 Managed 偵錯工具的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](hosting-structures.md)
- [診斷 Managed 偵錯助理的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
