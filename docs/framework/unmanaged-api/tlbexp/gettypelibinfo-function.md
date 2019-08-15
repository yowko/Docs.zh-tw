---
title: GetTypeLibInfo 函式
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7da0986269189ba5c2dfa0f10d509bf51deb446d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040197"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo 函式
藉由檢查[TLIBATTR](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr)結構, 傳回指定之類型程式庫的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a>參數  
 `szFile`  
 在類型程式庫的檔案名。  
  
 `pTypeLibID`  
 脫銷類型程式庫的 GUID。  
  
 `pTypeLibLCID`  
 脫銷類型程式庫的當地語系化識別碼。  
  
 `pTypeLibPlatform`  
 脫銷[SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind)旗標, 可識別類型程式庫的目標作業系統。 常見的值為 SYS_WIN32 和 SYS_WIN64。  
  
 `pTypeLibMajorVer`  
 脫銷類型程式庫的主要版本號碼。 例如, 針對版本*x. y*, 主要版本號碼為*x*。  
  
 `pTypeLibMinorVer`  
 脫銷類型程式庫的次要版本號碼。 例如, 針對版本*x. y*, 次要版本號碼為*y*。  
  
## <a name="remarks"></a>備註  
 此`GetTypeLibInfo`函式是由[tlbexp.exe (類型程式庫匯出工具)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)所呼叫。 此工具會產生類型程式庫, 以描述 common language runtime (CLR) 元件中的類型。  
  
 如果有任何參數為 null, 函數`HRESULT`會傳回的。 `E_POINTER` 否則，它會傳回 `S_OK`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** TlbRef。h  
  
 **LIBRARY:** TlbRef.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [Tlbexp Helper 函式](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx 函式](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
