---
title: ICorDebugAppDomainEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
ms.openlocfilehash: 9fb849c78636d5e29f58a70f59aa4cb3cd22df40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784744"
---
# <a name="icordebugappdomainenum-interface"></a>ICorDebugAppDomainEnum 介面

提供 `Next` 方法，它會從列舉中的下一個位置開始，傳回指定數目的 `ICorDebugAppDomainEnum` 值。 這個介面是 "ICorDebugEnum" 的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](icordebugappdomainenum-next-method.md)|從目前的資料指標位置開始，取得集合中指定的應用程式域數目。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebug 介面](icordebug-interface.md)
- [偵錯介面](debugging-interfaces.md)
