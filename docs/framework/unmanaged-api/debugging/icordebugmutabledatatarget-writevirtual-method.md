---
title: ICorDebugMutableDataTarget::WriteVirtual 方法
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 6325dba99fba0ab5e2f752a0635fdd428d3065eb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206746"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget::WriteVirtual 方法
將記憶體寫入目標處理序位址空間。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a>參數  
 `address`  
 [in] 要寫入 `pBuffer` 內容的位址。  
  
 `pBuffer`  
 [in] 包含所要寫入之位元組的位元組陣列指標。  
  
 `address`  
 [in] `pBuffer` 中的位元組數。  
  
## <a name="return-value"></a>傳回值  
 成功時為 `S_OK`，失敗時為任何其他 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 如果無法寫入任何位元組，則方法呼叫失敗，但不變更目標位址空間中的任何位元組。 (否則，目標的狀態會不一致，使進一步的偵錯變得不可靠。)  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugMutableDataTarget 介面](icordebugmutabledatatarget-interface.md)
- [偵錯介面](debugging-interfaces.md)
