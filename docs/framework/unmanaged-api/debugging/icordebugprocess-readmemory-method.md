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
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178656"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory 方法
讀取此過程的指定記憶體區域。  
  
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
 [在]指定`CORDB_ADDRESS`要讀取的記憶體的基本位址的值。  
  
 `size`  
 [在]要從記憶體中讀取的位元組數。  
  
 `buffer`  
 [出]接收記憶體內容的緩衝區。  
  
 `read`  
 [出]指向傳輸到指定緩衝區的位元組數的指標。  
  
## <a name="remarks"></a>備註  
 該方法`ReadMemory`主要用於內部調試，以檢查調試器的非託管部分正在使用的記憶體區域。 此方法還可用於讀取 Microsoft 中間語言 （MSIL） 代碼和本機 JIT 編譯代碼。  
  
 任何託管中斷點都將從`buffer`參數中返回的資料中刪除。 [ICorDebugProcess2：：：setUn託管中斷點](icordebugprocess2-setunmanagedbreakpoint-method.md)設置的本機中斷點不會進行調整。  
  
 不執行進程記憶體的緩存。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
