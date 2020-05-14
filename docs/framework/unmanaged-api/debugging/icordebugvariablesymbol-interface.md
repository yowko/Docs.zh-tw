---
title: ICorDebugVariableSymbol 介面
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 412ecbfc03378947e5a578e163034d104718bc91
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397098"
---
# <a name="icordebugvariablesymbol-interface"></a>ICorDebugVariableSymbol 介面
擷取變數的偵錯符號資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetName 方法](icordebugvariablesymbol-getname-method.md)|取得變數的名稱。|  
|[GetSize 方法](icordebugvariablesymbol-getsize-method.md)|取得變數的大小 (以位元組為單位)。|  
|[GetSlotIndex 方法](icordebugvariablesymbol-getslotindex-method.md)|取得區域變數的 Managed 位置索引。|  
|[GetValue 方法](icordebugvariablesymbol-getvalue-method.md)|取得變數的值做為位元組陣列。|  
|[SetValue 方法](icordebugvariablesymbol-setvalue-method.md)|指派位元組陣列的值給變數。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面僅適用於 .NET 原生。 如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
