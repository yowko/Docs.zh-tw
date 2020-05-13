---
title: ICorDebugProcess3::SetEnableCustomNotification 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
ms.openlocfilehash: 523d9665ffd2637a0e856d74d4d3b3838cb5e83c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212122"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification 方法
啟用和停用指定類型的自訂偵錯工具通知。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>參數  
 `pClass`  
 在指定自訂偵錯工具通知的類型。  
  
 `fEnable`  
 [in] `true`若要啟用自訂偵錯工具通知;`false`停用通知。 預設值是 `false`。  
  
## <a name="remarks"></a>備註  
 當 `fEnable` 設定為時 `true` ，對方法的呼叫會 <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> 觸發[ICorDebugManagedCallback3：： CustomNotification](icordebugmanagedcallback3-customnotification-method.md)回呼。 預設會停用通知;因此，偵錯工具必須指定它知道的任何通知類型，並想要處理。 由於[ICorDebugClass](icordebug-interface.md)類別的範圍是由應用程式域所限定，因此偵錯工具必須 `SetEnableCustomNotification` 針對進程中的每個應用程式域呼叫，如果它想要在整個進程中接收通知。  
  
 從 .NET Framework 4 開始，唯一支援的通知是跨執行緒相依性通知。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess3 介面](icordebugprocess3-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
