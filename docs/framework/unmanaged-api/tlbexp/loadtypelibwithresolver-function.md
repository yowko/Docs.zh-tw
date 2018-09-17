---
title: LoadTypeLibWithResolver 函式
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6a217e2212bb900d7ba83ccdd9cb00d30454baf
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45749644"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver 函式
載入類型程式庫，並使用所提供[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)來解析任何的內部參考的型別程式庫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a>參數  
 `szFile`  
 [in]型別程式庫檔案路徑。  
  
 `regkind`  
 [in]A [REGKIND 列舉](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind)控制型別程式庫的註冊方式的旗標。 其可能的值為：  
  
-   `REGKIND_DEFAULT`： 使用預設註冊行為。  
  
-   `REGKIND_REGISTER`： 註冊此型別程式庫。  
  
-   `REGKIND_NONE`： 請勿註冊此型別程式庫。  
  
 `pTlbResolver`  
 [in]實作的指標[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)。  
  
 `pptlib`  
 [out]正在載入類型程式庫的參考。  
  
## <a name="return-value"></a>傳回值  
 下表所列的 HRESULT 值之一。  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|記憶體不足。|  
|`E_POINTER`|一或多個指標均為無效。|  
|`E_INVALIDARG`|一或多個引數均為無效。|  
|`TYPE_E_IOERROR`|此函式無法寫入檔案。|  
|`TYPE_E_REGISTRYACCESS`|無法開啟系統註冊資料庫。|  
|`TYPE_E_INVALIDSTATE`|無法開啟型別程式庫。|  
|`TYPE_E_CANTLOADLIBRARY`|無法載入類型程式庫或 DLL。|  
  
## <a name="remarks"></a>備註  
 [Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)呼叫`LoadTypeLibWithResolver`在組件至型別程式庫轉換過程中的函式。  
  
 此函式會載入至登錄的最小存取指定的型別程式庫。 函式接著會檢查內部參考的型別程式庫，其中每個必須載入並加入至父型別程式庫的類型程式庫。  
  
 可以載入參考的型別程式庫之前，必須解析其參考檔案路徑的完整檔案路徑。 這透過達成[ResolveTypeLib 方法](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md)所提供[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)，這會傳入`pTlbResolver`參數。  
  
 當已知的參考的類型程式庫的完整檔案路徑時，`LoadTypeLibWithResolver`函式載入，並將參考的類型程式庫加入至父型別程式庫，建立合併的主要類型程式庫。  
  
 函式會解析並載入所有的內部參考的型別程式庫之後，它會傳回的主要解析的型別程式庫中的參考`pptlib`參數。  
  
 `LoadTypeLibWithResolver`通常會呼叫函式[Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)，提供其本身內部[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)中的實作`pTlbResolver`參數。  
  
 如果您呼叫`LoadTypeLibWithResolver`直接管理，您必須提供您自己[ITypeLibResolver 介面](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** TlbRef.h  
  
 **程式庫：** TlbRef.lib  
  
 **.NET framework 版本：** 3.5、 3.0、 2.0  
  
## <a name="see-also"></a>另請參閱  
 [Tlbexp Helper 函式](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx 函式](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
