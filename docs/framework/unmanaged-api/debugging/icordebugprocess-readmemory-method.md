---
title: ICorDebugProcess::ReadMemory 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d74da502492065dbffb5e5499581263760636c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737075"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory 方法
讀取指定的此程序的記憶體區域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>參數  
 `address`  
 [in]A`CORDB_ADDRESS`值，指定要讀取的記憶體的基底位址。  
  
 `size`  
 [in]若要從記憶體讀取的位元組數目。  
  
 `buffer`  
 [out]接收內容的記憶體緩衝區。  
  
 `read`  
 [out]指標的位元組數傳送至指定的緩衝區。  
  
## <a name="remarks"></a>備註  
 `ReadMemory`方法主要是用來檢查正在使用的 unmanaged 偵錯項目一部分的記憶體區域的 interop 偵錯。 這個方法也可用來讀取 Microsoft intermediate language (MSIL) 程式碼和原生的 JIT 編譯程式碼。  
  
 將移除任何受管理的中斷點，從資料中傳回的`buffer`參數。 將進行不會調整，藉由設定原生的中斷點[ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)。  
  
 無快取的程序記憶體會執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
