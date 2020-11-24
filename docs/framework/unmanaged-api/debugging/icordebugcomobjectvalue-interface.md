---
title: ICorDebugComObjectValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
ms.openlocfilehash: 40df1416e68c86efe6d404119cb37277fe21ac56
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677540"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue 介面

提供方法，以取得與執行時間可呼叫包裝函式相關聯 (RCW) 的相關資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCachedInterfacePointers 方法](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|取得在目前 RCW 上快取的原始介面指標。|  
|[GetCachedInterfaceTypes 方法](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|提供目前物件已大寫或作為其使用之介面類別型的列舉值。|  
  
## <a name="remarks"></a>備註  

 若要檢查 "ICorDebugValue" 介面的實例是否代表 RCW，偵錯工具會呼叫 `QueryInterface` "ICorDebugValue" 上的 `IID_ICorDebugComObjectValue` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
