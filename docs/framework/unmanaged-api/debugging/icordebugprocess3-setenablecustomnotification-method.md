---
title: "ICorDebugProcess3::SetEnableCustomNotification 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess3.SetEnableCustomNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ccd1f4b6be56202d5efea1d2e38dce554835218
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification 方法
啟用和停用指定之類型的自訂偵錯工具通知。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a>參數  
 `pClass`  
 [in]指定自訂偵錯工具通知的型別。  
  
 `fEnable`  
 [in]`true`啟用自訂偵錯工具通知。`false`停用通知。 預設值是 `false`。  
  
## <a name="remarks"></a>備註  
 當`fEnable`設`true`，呼叫<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>方法觸發程序[icordebugmanagedcallback3:: Customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)回呼。 預設值則會停用通知因此，偵錯工具必須指定它知道，而且想要處理的任何通知類型。 因為[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)範圍類別是由應用程式定義域，偵錯工具必須呼叫`SetEnableCustomNotification`每個應用程式網域中的程序，如果它要接收通知接收之間的整個程序。  
  
 從開始[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]，僅支援的通知是跨執行緒相依性通知。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorDebugProcess3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
