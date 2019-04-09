---
title: ISymUnmanagedWriter4 介面
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5732cc08512df25a14cc8ea9dcaa03c56207dde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202030"
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
|[GetDebugInfoWithPadding 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|函數一樣[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)不同之處在於路徑字串以下列結束的 null 字元，讓字串資料的固定的大小的零來填補`MAX_PATH`。 如果路徑字串的長度本身是只指定填補小於`MAX_PATH`。<br /><br /> 這可讓您更輕鬆地撰寫工具類型的差異 PE 檔案。|  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
