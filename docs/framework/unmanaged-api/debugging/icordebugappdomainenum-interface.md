---
title: ICorDebugAppDomainEnum Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf8db3b02ba4766d046fc549eec8add31f51069
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomainenum-interface1"></a>ICorDebugAppDomainEnum Interface1
提供`Next`方法，這個方法會傳回指定的數目的`ICorDebugAppDomainEnum`開始列舉中的下一個位置的值。 這個介面是 「 ICorDebugEnum"的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|從集合中，從目前游標位置開始，取得指定的應用程式定義域數目。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
