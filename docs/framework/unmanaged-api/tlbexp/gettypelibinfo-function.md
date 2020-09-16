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
ms.openlocfilehash: 4c630f5f7e3dc66ce44f10cd69fcd108226b0250
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554328"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo 函式
藉由檢查其 [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) 結構，傳回指定類型程式庫的相關資訊。  
  
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
 擴展類型程式庫的 GUID。  
  
 `pTypeLibLCID`  
 擴展類型程式庫的當地語系化識別碼。  
  
 `pTypeLibPlatform`  
 擴展識別類型程式庫之目標作業系統的 [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) 旗標。 一般值為 SYS_WIN32 和 SYS_WIN64。  
  
 `pTypeLibMajorVer`  
 擴展類型程式庫的主要版本號碼。 例如，針對版本 *x. y*，主要版本號碼為 *x*。  
  
 `pTypeLibMinorVer`  
 擴展類型程式庫的次要版本號碼。 例如，針對版本 *x. y*，次要版本號碼是 *y*。  
  
## <a name="remarks"></a>備註  
 函式 `GetTypeLibInfo` 是由 [Tlbexp.exe (型別程式庫匯出工具) ](../../tools/tlbexp-exe-type-library-exporter.md)所呼叫。 此工具會產生類型程式庫，以描述 common language runtime (CLR) 元件中的類型。  
  
 如果有任何參數為 null，則函數會傳回 `HRESULT` 的 `E_POINTER` 。 否則會傳回 `S_OK`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** TlbRef。h  
  
 連結**庫：** TlbRef .lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [Tlbexp Helper 函式](index.md)
- [LoadTypeLibEx 函式](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
