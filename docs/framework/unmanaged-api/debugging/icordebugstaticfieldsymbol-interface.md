---
title: ICorDebugStaticFieldSymbol 介面
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: b50b9c8435f19e1a77229f01dc85514f5f75c9f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791808"
---
# <a name="icordebugstaticfieldsymbol-interface"></a>ICorDebugStaticFieldSymbol 介面
代表靜態欄位的偵錯符號資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetAddress 方法](icordebugstaticfieldsymbol-getaddress-method.md)|取得靜態欄位的位址。|  
|[GetName 方法](icordebugstaticfieldsymbol-getname-method.md)|取得靜態欄位的名稱。|  
|[GetSize 方法](icordebugstaticfieldsymbol-getsize-method.md)|取得靜態欄位的大小 (以位元組為單位)。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugStaticFieldSymbol` 介面可用來擷取靜態欄位的偵錯符號資訊。  
  
> [!NOTE]
> 這個介面僅適用於 .NET 原生。 如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugInstanceFieldSymbol 介面](icordebuginstancefieldsymbol-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
