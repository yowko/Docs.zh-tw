---
title: ISymUnmanagedWriter5 介面
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88a9fa2f720db403c45d4254b17dfaf4689cd0f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706900"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 介面
ISymUnmanagedWriter5 介面。  
  
## <a name="syntax"></a>語法  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>方法  
 這個介面包含下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|關閉對應資訊的語彙基元至來源範圍的特殊的自訂資料區段。 它已關閉之後，就可以不新增任何更多的對應資訊。|  
|[MapTokenToSourceSpan 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|對應至指定的原始程式檔指定的中繼資料語彙基元跨越指定的原始程式檔中。<br /><br /> 必須呼叫之間呼叫[OpenMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)並[CloseMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)。|  
|[OpenMapTokensToSourceSpans 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|開啟要發出至來源語彙基元範圍的對應資訊的特殊的自訂資料 區段。 方法已開啟，或反之亦然，會發生錯誤時，請開啟這一節。|  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱
- [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
