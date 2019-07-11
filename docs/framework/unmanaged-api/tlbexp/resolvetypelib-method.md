---
title: ResolveTypeLib 方法
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b6db8925fb966f4a8b2a213b0d6e340d0edf107
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756423"
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib 方法
藉由傳回它的完整的路徑來解析型別程式庫的簡單名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a>參數  
 `bstrSimpleName`  
 [in]A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) ，其中包含型別程式庫的簡單名稱。  
  
 `tlbid`  
 [in]指派給類型程式庫在登錄中的 GUID。  
  
 `lcid`  
 [in]當地語系化類型程式庫的識別碼。  
  
 `wMajorVersion`  
 [in]型別程式庫主要版本號碼。 例如，針對版本*x.y*，主要版本號碼是*x*。  
  
 `wMinorVersion`  
 [in]型別程式庫的次要版本號碼。 例如，針對版本*x.y*，次要版本號碼是*y*。  
  
 `syskind`  
 [in]A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind)旗標，以識別作業的環境。 常見的值為 SYS_WIN32 和 SYS_WIN64。  
  
 `pbstrResolvedTlbName`  
 [out]指標[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) ，其中包含在名為的型別程式庫的完整路徑`bstrSimpleName`參數。  
  
## <a name="remarks"></a>備註  
 `ResolveTypeLib`方法會呼叫[LoadTypeLibWithResolver 函式](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)期間[Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)處理。  
  
 這個介面的自訂實作必須傳回[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) ，其中包含在名為的型別程式庫的完整路徑`bstrSimpleName`參數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** TlbRef.idl TlbRef.h  
  
 **LIBRARY:** TlbRef.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [Tlbexp Helper 函式](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
