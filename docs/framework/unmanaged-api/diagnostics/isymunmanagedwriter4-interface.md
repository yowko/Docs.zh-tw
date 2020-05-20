---
title: ISymUnmanagedWriter4 介面
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: eaf2e8e60d9812ab6a31fb3b9050cbaae0f1a9d7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609465"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 介面
ISymUnmanagedWriter4 介面。  
  
## <a name="syntax"></a>語法  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>方法  
 這個介面包含下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetDebugInfoWithPadding 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|函式與[GetDebugInfo 方法](isymunmanagedwriter-getdebuginfo-method.md)相同，不同之處在于路徑字串會在結束的 null 字元之後以零填補，使字串資料成為固定大小 `MAX_PATH` 。 只有在路徑字串長度本身小於時，才會提供填補 `MAX_PATH` 。<br /><br /> 這可讓您更輕鬆地撰寫與 PE 檔案不同的工具。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 介面](isymunmanagedwriter3-interface.md)
