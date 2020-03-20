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
ms.openlocfilehash: 786e53d43ecde0bc3a97fadb77184d25d41430bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178341"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes 列舉
指定在搜索符號讀取器時要使用的策略。 這些常量由[ISymUn 託管 Binder2：：getReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)和[ISymUn託管 Binder3：：getReader 來自回檔](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)方法使用。  
  
> [!IMPORTANT]
> 從不受信任的源打開程式資料庫 （PDB） 檔存在安全風險。  
  
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
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`AllowRegistryAccess`|查詢符號搜索路徑的註冊表。|  
|`AllowSymbolServerAccess`|訪問符號伺服器。|  
|`AllowOriginalPathAccess`|搜索調試目錄中指定的路徑。|  
|`AllowReferencePathAccess`|在 .exe 檔所在的位置搜索 PDB。|  
  
## <a name="requirements"></a>需求  
 **標題：** 科西姆.伊德爾，科西姆.h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區列舉](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
