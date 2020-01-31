---
title: ICorDebugMergedAssemblyRecord 介面
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 6d5d862110cd91e8ac81c96e50486be10c579903
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793062"
---
# <a name="icordebugmergedassemblyrecord-interface"></a>ICorDebugMergedAssemblyRecord 介面
提供合併組件的相關資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCulture 方法](icordebugmergedassemblyrecord-getculture-method.md)|取得組件的文化特性名稱字串。|  
|[GetIndex 方法](icordebugmergedassemblyrecord-getindex-method.md)|取得組件的前置詞索引。|  
|[GetPublicKey 方法](icordebugmergedassemblyrecord-getpublickey-method.md)|取得組件的公開金鑰。|  
|[GetPublicKeyToken 方法](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|取得組件的公開金鑰語彙基元。|  
|[GetSimpleName 方法](icordebugmergedassemblyrecord-getsimplename-method.md)|取得組件的簡單名稱。|  
|[GetVersion 方法](icordebugmergedassemblyrecord-getversion-method.md)|取得組件的版本資訊。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面僅適用於 .NET 原生。 如果您在 .NET 原生之外針對 ICorDebug 案例實作這個介面，Common Language Runtime 會忽略這個介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
