---
title: ICorDebugVariableSymbol::GetSlotIndex Method
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 251a978e96ff396d0d9d9282ded7f8a25ae0ba0b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397086"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a>ICorDebugVariableSymbol::GetSlotIndex Method
取得區域變數的 Managed 位置索引。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>參數  
 `pSlotIndex`  
 [out] 區域變數位置索引的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為 `S_OK`。 如果變數是函式引數，則為 `E_FAIL`。  
  
## <a name="remarks"></a>備註  
 區域變數的 Managed 位置索引可用來擷取變數的中繼資料資訊。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugVariableSymbol 介面](icordebugvariablesymbol-interface.md)
- [偵錯介面](debugging-interfaces.md)
