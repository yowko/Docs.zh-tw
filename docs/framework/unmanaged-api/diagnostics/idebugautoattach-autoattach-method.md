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
ms.openlocfilehash: 64dd653bb0d4e383075a999e0803e4acfd0fae3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720096"
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach 方法

執行伺服器調用的偵錯工具自動附加。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a>參數  

 `guidPort`  
 在一律設定為 `GUID_NULL` 。  
  
 `dwPid`  
 在處理序識別碼，通常會與函數一起抓取 `GetCurrentProcessId` 。  
  
 `dwProgramType`  
 在程式類型： `AUTOATTACH_PROGRAM_WIN32` 、 `AUTOATTACH_PROGRAM_COMPLUS` 或 `AUTOATTACH_PROGRAM_UNKNOWN` 。  
  
 `dwProgramId`  
 在程式識別碼。  
  
 `pszSessionId`  
 在Debug 動詞命令所傳遞的字串。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK。  
  
## <a name="requirements"></a>需求  

 **標頭：** DbgAutoAttach。h  
  
## <a name="see-also"></a>另請參閱

- [IDebugAutoAttach 介面](idebugautoattach-interface.md)
