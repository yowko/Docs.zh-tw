---
title: ICorDebugDataTarget3 介面
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 57ef9b567d57c77c523ca6daefcf80b1d7de66d1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976404"
---
# <a name="icordebugdatatarget3-interface"></a>ICorDebugDataTarget3 介面
以邏輯方式擴充[ICorDebugDataTarget](icordebugdatatarget-interface.md)介面，以提供已載入模組的相關資訊。  
  
## <a name="method"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetLoadedModules 方法](icordebugdatatarget3-getloadedmodules-method.md)|取得到目前為止已載入的模組清單。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面僅適用於 .NET 原生。 如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
