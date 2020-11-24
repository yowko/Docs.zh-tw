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
ms.openlocfilehash: 18416954517c3cac09d013b8075bd097305a1dca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673952"
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory 方法

將資料寫入此進程中的記憶體區域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a>參數  

 `address`  
 在 `CORDB_ADDRESS` 值，這個值是寫入資料的記憶體區域基底位址。 在進行資料傳輸之前，系統會先確認指定大小的記憶體區域（從基底位址開始）可以進行寫入。 如果無法存取，方法將會失敗。  
  
 `size`  
 在要寫入記憶體區域的位元組數目。  
  
 `buffer`  
 在包含要寫入之資料的緩衝區。  
  
 `written`  
 擴展變數的指標，此變數會接收此進程中寫入記憶體區域的位元組數目。 如果 `written` 是 Null，則會忽略這個參數。  
  
## <a name="remarks"></a>備註  

 資料會自動寫入任何中斷點後方。 在 .NET Framework 2.0 版中，原生偵錯工具不應該使用這個方法將中斷點插入指令資料流程中。 請改用 [ICorDebugProcess2：： SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) 。  
  
 `WriteMemory`方法只能在 managed 程式碼之外使用。 如果使用不正確，此方法可能會損毀執行時間。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
