---
title: ICorDebugClass2::SetJMCStatus 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23f248625753c15a4798ea69a1eb3b377b79f95d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747760"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus 方法
每一個方法的類別中，設定值，指出方法是否為使用者定義的程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>參數  
 `bIsJustMyCode`  
 [in]設定為`true`表示的方法是使用者定義程式碼; 否則設定為`false`。  
  
## <a name="remarks"></a>備註  
 只是我的程式碼 (JMC) 步進會略過的非使用者程式碼。 使用者定義的程式碼必須是可偵錯的程式碼的子集。  
  
 `SetJMCStatus` 如果它無法設定值，對於任何方法，即使它已成功設定所有其他方法的值，則傳回 S_FALSE 的 HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
