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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58e50a0c02f15590e5bbbcadaabeaa7e3886b74b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736826"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification 方法
啟用和停用指定之型別的自訂偵錯工具通知。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>參數  
 `pClass`  
 [in]指定自訂的偵錯工具通知的型別。  
  
 `fEnable`  
 [in]`true`以啟用自訂的偵錯工具通知;`false`停用通知。 預設值為 `false`。  
  
## <a name="remarks"></a>備註  
 當`fEnable`設定為`true`，呼叫<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>方法觸發程序[ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)回呼。 根據預設，會停用通知因此，偵錯工具必須指定它所知，並想要處理的任何通知類型。 因為[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)類別的範圍由應用程式定義域、 偵錯工具必須呼叫`SetEnableCustomNotification`程序，如果它要接收通知，跨整個程序中的每個應用程式定義域。  
  
 從.NET Framework 4 開始，唯一支援的通知會是跨執行緒相依性通知。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
