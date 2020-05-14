---
title: ICorDebugValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: b8d2e49031e59db0527de3c848d7d390095797bf
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396784"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue 介面
表示正在進行調試之進程中的值。 此值可以是讀取或寫入值。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](icordebugvalue-createbreakpoint-method.md)|這個方法目前尚未實作。|  
|[GetAddress 方法](icordebugvalue-getaddress-method.md)|取得此物件的位址 `ICorDebugValue` ，此為正在進行調試的進程。|  
|[GetSize 方法](icordebugvalue-getsize-method.md)|取得這個物件的大小（以位元組為單位） `ICorDebugValue` 。|  
|[GetType 方法](icordebugvalue-gettype-method.md)|取得此物件的基本類型 `ICorDebugValue` 。|  
  
## <a name="remarks"></a>備註  
 一般情況下，值物件的擁有權會在傳回時傳遞。 當物件完成時，收件者會負責從物件中移除參考。  
  
 根據從其中抓取值的位置而定，此值在進程繼續之後可能不會保持有效。 因此，一般而言，此值不應保留在[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)方法的呼叫中。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugValue3 介面](icordebugvalue3-interface.md)
- [偵錯介面](debugging-interfaces.md)
