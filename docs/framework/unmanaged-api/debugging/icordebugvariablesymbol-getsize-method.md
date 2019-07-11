---
title: ICorDebugVariableSymbol::GetSize 方法
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e963e655c933c9191953bb32ba0b73adf0ae86d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774877"
---
# <a name="icordebugvariablesymbolgetsize-method"></a>ICorDebugVariableSymbol::GetSize 方法
取得變數的大小 (以位元組為單位)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `pcbValue`  
 32 位元不帶正負號的整數指標，這個整數包含變數的大小。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugVariableSymbol 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
