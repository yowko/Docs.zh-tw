---
title: ICorDebugMutableDataTarget::WriteVirtual 方法
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fba970de6e5882d3cbe9be17b5b49be5a3e81aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171648"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget::WriteVirtual 方法
將記憶體寫入目標處理序位址空間。  
  
## <a name="syntax"></a>語法  
  
```  
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
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugMutableDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
