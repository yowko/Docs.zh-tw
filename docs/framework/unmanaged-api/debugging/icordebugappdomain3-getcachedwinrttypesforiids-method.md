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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95c84f7f40db0096b26ec448f8f229cdbfe3afb1
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025901"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法
取得其介面識別項為基礎的應用程式定義域中快取的 Windows 執行階段類型的列舉值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `cReqTypes`  
 [in]必要的型別數目。  
  
 `iidsToResolve`  
 [in]包含對應至受管理的表示法，要擷取 Windows 執行階段類型的介面識別碼的陣列指標。  
  
 `ppTypesEnum`  
 [out]擷取可讓受管理的快取表示，Windows 執行階段類型的列舉型別"ICorDebugTypeEnum 」 介面物件的位址指標，根據中的介面識別項`iidsToResolve`。  
  
## <a name="remarks"></a>備註  
 如果方法無法擷取特定的介面識別項的資訊，「 ICorDebugTypeEnum 」 集合中的對應項目會有一種`ELEMENT_TYPE_END`的資料擷取問題，因為錯誤或`ELEMENT_TYPE_VOID`未知的介面識別項。  
  
## <a name="requirements"></a>需求  
 **平台：** Windows 執行階段  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugAppDomain3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
