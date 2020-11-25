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
ms.openlocfilehash: 9a088c7e4e9c72c8247ccdd384bc724587210c37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710866"
---
# <a name="icordebugmdagetxml-method"></a>ICorDebugMDA::GetXML 方法

取得與 managed 偵錯工具相關聯的完整 XML 資料流程 (MDA) 以 [ICorDebugMDA](icordebugmda-interface.md)表示。  
  
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
 擴展XML 資料流程長度的指標。  
  
 `szName`  
 擴展要在其中儲存 XML 資料流程的陣列。 陣列可能是空的。  
  
## <a name="remarks"></a>備註  

 `GetXML`根據相關聯 XML 資料流程的大小而定，此方法可能會影響效能。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugMDA 介面](icordebugmda-interface.md)
- [診斷 Managed 偵錯助理的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
