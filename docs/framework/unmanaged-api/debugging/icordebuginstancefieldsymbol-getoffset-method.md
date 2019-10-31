---
title: ICorDebugInstanceFieldSymbol：： GetOffset 方法
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 3886e29a1c2fd44fbe50d1eef722f99da7abdbe5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139007"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a>ICorDebugInstanceFieldSymbol：： GetOffset 方法
取得在父類別中此執行個體欄位之位元組的位移。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a>參數  
 `pcbOffset`  
 此執行個體欄位在其父類別中的位移位元組數目。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugInstanceFieldSymbol 介面](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
