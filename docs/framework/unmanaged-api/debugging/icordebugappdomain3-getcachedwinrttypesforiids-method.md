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
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179067"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法
根據應用程式域中的介面識別碼獲取應用程式域中緩存的 Windows 運行時類型的枚舉器。  
  
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
 [在]所需類型的數量。  
  
 `iidsToResolve`  
 [在]指向陣列的指標，其中包含與要檢索的 Windows 運行時類型的託管表示形式對應的介面識別碼。  
  
 `ppTypesEnum`  
 [出]指向"ICorDebugTypeEnum"介面物件的位址的指標，該物件允許根據 中的`iidsToResolve`介面識別碼檢索到已檢索的 Windows 運行時類型的緩存託管表示形式。  
  
## <a name="remarks"></a>備註  
 如果方法無法檢索特定介面識別碼的資訊，則"ICorDebugTypeEnum"集合中的相應條目將具有一種`ELEMENT_TYPE_END`因數據檢索問題或`ELEMENT_TYPE_VOID`未知介面識別碼而導致的錯誤類型。  
  
## <a name="requirements"></a>需求  
 **平臺：** 視窗運行時  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugAppDomain3 介面](icordebugappdomain3-interface.md)
