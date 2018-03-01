---
title: "ICorDebugProcess::WriteMemory 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a1a12d1393d1db69ea47833958fdf828b552064
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory 方法
將資料寫入此程序的記憶體區域。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a>參數  
 `address`  
 [in]A`CORDB_ADDRESS`寫入值，也就是基底資料的記憶體區域。 資料傳輸發生之前，系統會確認指定的大小，開始的基底位址的記憶體區域是可供寫入存取。 如果您不能存取，方法就會失敗。  
  
 `size`  
 [in]寫入記憶體區域的位元組數目。  
  
 `buffer`  
 [in]包含要寫入資料的緩衝區。  
  
 `written`  
 [out]寫入記憶體區域，此程序中的位元組數目變數的指標。 如果`written`是 NULL，這個參數已忽略。  
  
## <a name="remarks"></a>備註  
 任何中斷點之後，會自動寫入資料。 在.NET Framework 2.0 版中，原生偵錯工具不應使用這個方法將中斷點插入指令資料流。 使用[icordebugprocess2:: Setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)改為。  
  
 `WriteMemory`方法應只有外部 managed 程式碼使用。 如果不當使用，這個方法可能會損毀的執行階段。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
