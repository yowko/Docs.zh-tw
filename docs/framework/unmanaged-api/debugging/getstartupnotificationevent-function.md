---
title: GetStartupNotificationEvent 函式
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f67f3ef57b4996eb4a956c596b76fb94b1bdfd7a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738883"
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent 函式
建立或開啟任何載入指定目標處理序的 Common Language Runtime (CLR) 將對其發出信號的事件控制代碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a>參數  
 `debuggeePID`  
 [in] 從其接收 CLR 啟動通知的目標處理序的處理序識別碼。  
  
 `phStartupEvent`  
 [out] 由 CLR 在啟動時通知的控制代碼指標。  
  
## <a name="return-value"></a>傳回值  
 S_OK  
 已成功取得啟動通知事件的控制代碼。  
  
 E_INVALIDARG  
 `phStartupEvent` 為 null 或 `debuggeePID` 未參考目前正在執行的處理序。  
  
 E_FAIL (或其他 E_ 傳回碼)  
 無法取得啟動通知事件的控制代碼。  
  
## <a name="remarks"></a>備註  
 在 Windows 作業系統上，`debuggeePID` 對應至 OS 處理序識別碼。  
  
 在對事件發出信號的 CLR 執行任何 Managed 程式碼之前，會對事件發出信號。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** dbgshim.h  
  
 **程式庫：** dbgshim.dll  
  
 **.NET framework 版本：** 3.5 SP1
