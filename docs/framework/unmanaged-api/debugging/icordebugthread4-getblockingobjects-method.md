---
title: ICorDebugThread4::GetBlockingObjects 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
ms.openlocfilehash: 39833b689f28437b4241d9cb15fb4a92b2f9bcc3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791380"
---
# <a name="icordebugthread4getblockingobjects-method"></a>ICorDebugThread4::GetBlockingObjects 方法
提供[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構的已排序列舉，以提供執行緒封鎖資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a>參數  
 `ppBlockingObjectEnum`  
 脫銷[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構之已排序列舉的指標。  
  
## <a name="remarks"></a>備註  
 傳回之列舉中的第一個專案會對應至封鎖執行緒的第一個結構。 第二個元素對應至在執行非同步程序呼叫（APC）時，在第一個專案上被封鎖時所遇到的封鎖專案，依此類推。  
  
 列舉只在目前已同步處理狀態的持續時間內有效。  
  
 當調試物件處於已同步處理的狀態時，必須呼叫這個方法。  
  
 如果 `ppBlockingObjectEnum` 不是有效的指標，則結果會是未定義的。  
  
 如果執行緒遭到封鎖，而且無法判斷錯誤，則方法會傳回表示失敗的 HRESULT;否則，它會傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugThread4 介面](icordebugthread4-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
