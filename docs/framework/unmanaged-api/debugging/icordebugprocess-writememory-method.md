---
title: ICorDebugProcess::WriteMemory 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e9d640fb1c9dae5bb195baa504e560ba8e45821
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497089"
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory 方法
將資料寫入至這個處理程序中的記憶體區域。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a>參數  
 `address`  
 [in]A`CORDB_ADDRESS`寫入資料的記憶體區域的基底位址的值。 傳送資料之前，系統會驗證指定的大小，在基底的位址，從開始的記憶體區域是可供寫入存取。 如果您不能存取，方法就會失敗。  
  
 `size`  
 [in]要寫入的記憶體區域的位元組數目。  
  
 `buffer`  
 [in]這種緩衝區包含要寫入的資料。  
  
 `written`  
 [out]在此程序的記憶體區域寫入的位元組數目接收變數的指標。 如果`written`為 NULL，就會忽略這個參數。  
  
## <a name="remarks"></a>備註  
 任何中斷點之後，會自動寫入資料。 在.NET Framework 2.0 版中，原生偵錯工具應該使用這個方法來插入指令資料流中的中斷點。 使用[ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)改。  
  
 `WriteMemory`方法應該只在 managed 程式碼之外使用。 如果不當使用，這個方法可能會損毀的執行階段。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
