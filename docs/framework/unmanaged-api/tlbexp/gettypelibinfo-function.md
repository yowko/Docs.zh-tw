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
ms.openlocfilehash: 0ec28c581b8e6e0aff3a2765720b6e9795be931b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003096"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo 函式
傳回指定的類型程式庫的相關資訊，藉由檢查其[TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr)結構。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szFile`  
 [in]型別程式庫檔案名稱。  
  
 `pTypeLibID`  
 [out]型別程式庫的 GUID。  
  
 `pTypeLibLCID`  
 [out]當地語系化類型程式庫的識別碼。  
  
 `pTypeLibPlatform`  
 [out]A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind)識別目標作業系統類型程式庫的旗標。 常見的值為 SYS_WIN32 和 SYS_WIN64。  
  
 `pTypeLibMajorVer`  
 [out]型別程式庫主要版本號碼。 例如，針對版本*x.y*，主要版本號碼是*x*。  
  
 `pTypeLibMinorVer`  
 [out]型別程式庫的次要版本號碼。 例如，針對版本*x.y*，次要版本號碼是*y*。  
  
## <a name="remarks"></a>備註  
 `GetTypeLibInfo`函式會呼叫[Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)。 此工具會產生類型程式庫，描述 common language runtime (CLR) 組件中的類型。  
  
 如果任何參數為 null，則函數會傳回`HRESULT`的`E_POINTER`。 否則它會傳回 `S_OK`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** TlbRef.h  
  
 **程式庫：** TlbRef.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [Tlbexp Helper 函式](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx 函式](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
