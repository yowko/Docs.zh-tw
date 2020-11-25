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
ms.openlocfilehash: 6497dd3e720874e47de9dfda74e483a642cbb181
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708227"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver 函式

載入類型程式庫，並使用提供的 [ITypeLibResolver 介面](itypelibresolver-interface.md) 來解析任何內部參考的類型程式庫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>參數  

 `szFile`  
 在類型程式庫的檔案路徑。  
  
 `regkind`  
 在 [REGKIND 列舉](/windows/win32/api/oleauto/ne-oleauto-regkind) 旗標，可控制如何註冊類型程式庫。 可能的值為：  
  
- `REGKIND_DEFAULT`：使用預設註冊行為。  
  
- `REGKIND_REGISTER`：註冊此類型程式庫。  
  
- `REGKIND_NONE`：請勿註冊此型別程式庫。  
  
 `pTlbResolver`  
 在 [ITypeLibResolver 介面](itypelibresolver-interface.md)之執行的指標。  
  
 `pptlib`  
 擴展正在載入之類型程式庫的參考。  
  
## <a name="return-value"></a>傳回值  

 下表所列的其中一個 HRESULT 值。  
  
|傳回值|意義|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|記憶體不足。|  
|`E_POINTER`|一或多個指標無效。|  
|`E_INVALIDARG`|一或多個引數無效。|  
|`TYPE_E_IOERROR`|函數無法寫入檔案。|  
|`TYPE_E_REGISTRYACCESS`|無法開啟系統註冊資料庫。|  
|`TYPE_E_INVALIDSTATE`|無法開啟類型程式庫。|  
|`TYPE_E_CANTLOADLIBRARY`|無法載入類型程式庫或 DLL。|  
  
## <a name="remarks"></a>備註  

 [Tlbexp.exe (型別程式庫匯出工具) ](../../tools/tlbexp-exe-type-library-exporter.md)在 `LoadTypeLibWithResolver` 元件對類型程式庫轉換程式期間呼叫函數。  
  
 此函式會以最基本的登錄存取權載入指定的類型程式庫。 然後，此函式會檢查內部參考類型程式庫的類型程式庫，而且每個類型程式庫都必須載入並新增至父型別程式庫。  
  
 在可以載入參考的類型程式庫之前，必須先將其參考檔案路徑解析為完整檔案路徑。 這是透過在參數中傳遞的[ITypeLibResolver 介面](itypelibresolver-interface.md)所提供的[ResolveTypeLib 方法](resolvetypelib-method.md)來完成 `pTlbResolver` 。  
  
 已知所參考類型程式庫的完整檔案路徑時，函式會 `LoadTypeLibWithResolver` 載入參考的類型程式庫，並將其加入至父類型程式庫，以建立組合的主要類型程式庫。  
  
 在函式解析並載入所有內部參考的類型程式庫之後，它會在參數中傳回主要解析類型程式庫的參考 `pptlib` 。  
  
 函式 `LoadTypeLibWithResolver` 通常是由 [Tlbexp.exe (型別程式庫匯出工具) ](../../tools/tlbexp-exe-type-library-exporter.md)，它會在參數中提供自己的內部 [ITypeLibResolver 介面](itypelibresolver-interface.md) 實作為 `pTlbResolver` 。  
  
 如果您 `LoadTypeLibWithResolver` 直接呼叫，則必須提供自己的 [ITypeLibResolver 介面](itypelibresolver-interface.md) 執行。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** TlbRef。h  
  
 連結 **庫：** TlbRef .lib  
  
 **.NET Framework 版本：** 3.5、3.0、2。0  
  
## <a name="see-also"></a>另請參閱

- [Tlbexp Helper 函式](index.md)
- [LoadTypeLibEx 函式](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
