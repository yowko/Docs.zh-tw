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
ms.openlocfilehash: d234e01e3d47a64b9a001591ee2b61074eea8afb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403389"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus 方法
每個類別的方法設定值，指出方法是否為使用者定義的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bIsJustMyCode`  
 [in]設定為`true`表示方法是由使用者定義程式碼，否則設為`false`。  
  
## <a name="remarks"></a>備註  
 剛-我的程式碼 (JMC) stepper 將略過的非使用者定義的程式碼。 使用者定義的程式碼必須是可偵錯的程式碼的子集。  
  
 `SetJMCStatus` 如果無法設定的值對於任何方法，即使它已成功設定的值為所有其他方法會傳回 S_FALSE 的 HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
