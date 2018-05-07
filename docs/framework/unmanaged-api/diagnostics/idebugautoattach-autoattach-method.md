---
title: IDebugAutoAttach::AutoAttach 方法
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5c95423a6918da7cc043f8d46de13d166b8d895
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach 方法
執行伺服器叫用偵錯工具自動附加。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidPort`  
 [in]一律設為`GUID_NULL`。  
  
 `dwPid`  
 [in]處理序識別碼，通常會使用擷取`GetCurrentProcessId`函式。  
  
 `dwProgramType`  
 [in]程式類型： `AUTOATTACH_PROGRAM_WIN32`， `AUTOATTACH_PROGRAM_COMPLUS`，或`AUTOATTACH_PROGRAM_UNKNOWN`。  
  
 `dwProgramId`  
 [in]程式識別碼。  
  
 `pszSessionId`  
 [in]偵錯動詞命令所傳遞的字串。  
  
## <a name="return-value"></a>傳回值  
 如果此方法成功為 S_OK。  
  
## <a name="requirements"></a>需求  
 **標頭：** DbgAutoAttach.h  
  
## <a name="see-also"></a>另請參閱  
 [IDebugAutoAttach 介面](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
