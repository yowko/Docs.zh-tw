---
title: CorSymSearchPolicyAttributes 列舉
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: 4fd31e6b752e13a5c43198760e9a4d62a8f77d10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448572"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes 列舉
指定搜尋符號讀取器時要使用的原則。 這些常數是由[ISymUnmanagedBinder2：： GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)和[ISymUnmanagedBinder3：： GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)方法所使用。  
  
> [!IMPORTANT]
> 從不受信任的來源開啟程式資料庫（PDB）檔案會有安全性風險。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`AllowRegistryAccess`|查詢登錄中的符號搜尋路徑。|  
|`AllowSymbolServerAccess`|存取符號伺服器。|  
|`AllowOriginalPathAccess`|搜尋在 Debug 目錄中指定的路徑。|  
|`AllowReferencePathAccess`|在 .exe 檔案所在的位置搜尋 PDB。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區列舉](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
