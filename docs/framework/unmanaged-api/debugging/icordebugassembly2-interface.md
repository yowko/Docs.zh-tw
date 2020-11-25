---
title: ICorDebugAssembly2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2
helpviewer_keywords:
- ICorDebugAssembly2 interface [.NET Framework debugging]
ms.assetid: c0766e29-e573-4f9a-a928-167d1de5aa7e
topic_type:
- apiref
ms.openlocfilehash: 5add8f18a91f2ea1a2833ffa2cf3dc4bf3b644bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728468"
---
# <a name="icordebugassembly2-interface"></a>ICorDebugAssembly2 介面

表示組件。 此介面是 ICorDebugAssembly 介面的延伸。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[IsFullyTrusted 方法](icordebugassembly2-isfullytrusted-method.md)|取得值，這個值會指出是否已將執行時間安全性系統授與元件完全信任。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
