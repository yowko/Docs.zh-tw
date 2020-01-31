---
title: ICorDebugMDA::GetXML 方法
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: cd1882bdfca1258889514a041726a59435e126b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793209"
---
# <a name="icordebugmdagetxml-method"></a>ICorDebugMDA::GetXML 方法
取得與[ICorDebugMDA](icordebugmda-interface.md)代表的 managed 偵錯工具（MDA）相關聯的完整 XML 資料流程。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cchName`  
 [in] `szName` 陣列的大小。  
  
 `pcchName`  
 脫銷XML 資料流程長度的指標。  
  
 `szName`  
 脫銷要在其中儲存 XML 資料流程的陣列。 陣列可能是空的。  
  
## <a name="remarks"></a>備註  
 視相關聯的 XML 資料流程大小而定，`GetXML` 方法可能會影響效能。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugMDA 介面](icordebugmda-interface.md)
- [使用 Managed 偵錯助理診斷錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
