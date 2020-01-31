---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: 8b259636a8bd28abd3bba12c4a05dda3c13557e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784896"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法
根據介面識別碼，取得應用程式域中快取 Windows 執行階段類型的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `cReqTypes`  
 在必要類型的數目。  
  
 `iidsToResolve`  
 在陣列的指標，其中包含對應至要抓取之 Windows 執行階段類型之 managed 表示的介面識別碼。  
  
 `ppTypesEnum`  
 脫銷「ICorDebugTypeEnum」介面物件位址的指標，可根據 `iidsToResolve`中的介面識別碼，列舉所抓取之 Windows 執行階段類型的快取 managed 標記法。  
  
## <a name="remarks"></a>備註  
 如果方法無法抓取特定介面識別碼的資訊，則 "ICorDebugTypeEnum" 集合中對應的專案將會有因數據抓取問題而發生錯誤的 `ELEMENT_TYPE_END` 類型，或針對未知的介面識別碼 `ELEMENT_TYPE_VOID`。  
  
## <a name="requirements"></a>需求  
 **平臺：** Windows 執行階段  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugAppDomain3 介面](icordebugappdomain3-interface.md)
