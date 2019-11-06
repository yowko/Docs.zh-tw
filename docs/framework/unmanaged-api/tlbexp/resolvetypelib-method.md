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
ms.openlocfilehash: 46cd8b5c22f48ba45c4da7fa8876d6807a21f2b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124148"
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib 方法
藉由傳回完整的路徑，解析類型程式庫的簡單名稱。  
  
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
 在包含類型程式庫之簡單名稱的[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) 。  
  
 `tlbid`  
 在指派給登錄中類型程式庫的 GUID。  
  
 `lcid`  
 在類型程式庫的當地語系化識別碼。  
  
 `wMajorVersion`  
 在類型程式庫的主要版本號碼。 例如，針對版本*x. y*，主要版本號碼為*x*。  
  
 `wMinorVersion`  
 在類型程式庫的次要版本號碼。 例如，針對版本*x. y*，次要版本號碼為*y*。  
  
 `syskind`  
 在識別操作環境的[SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind)旗標。 常見的值為 SYS_WIN32 和 SYS_WIN64。  
  
 `pbstrResolvedTlbName`  
 脫銷[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr)的指標，其中包含在 `bstrSimpleName` 參數中命名之類型程式庫的完整路徑。  
  
## <a name="remarks"></a>備註  
 在[tlbexp.exe （類型程式庫匯出工具）](../../tools/tlbexp-exe-type-library-exporter.md)處理期間， [LoadTypeLibWithResolver](loadtypelibwithresolver-function.md)函式會呼叫 `ResolveTypeLib` 方法。  
  
 此介面的自訂執行必須傳回一個[BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) ，其中包含在 `bstrSimpleName` 參數中名為之類型程式庫的完整路徑。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** TlbRef .idl，TlbRef。h  
  
 連結**庫：** TlbRef .lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [Tlbexp Helper 函式](index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
