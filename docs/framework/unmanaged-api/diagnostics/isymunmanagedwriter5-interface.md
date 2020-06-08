---
title: ISymUnmanagedWriter5 介面
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: d9204457b71b670e1c96ed228ad11116bdf41fe6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493574"
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
|[CloseMapTokensToSourceSpans 方法](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|關閉 [特殊自訂資料] 區段，以取得權杖對來源的對應資訊。 關閉之後，就無法再新增任何對應資訊。|  
|[MapTokenToSourceSpan 方法](isymunmanagedwriter5-maptokentosourcespan-method.md)|將給定的元資料標記對應至指定之原始程式檔中的給定原始程式列範圍。<br /><br /> 必須在[OpenMapTokensToSourceSpans 方法](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)和[CloseMapTokensToSourceSpans 方法](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)的呼叫之間呼叫。|  
|[OpenMapTokensToSourceSpans 方法](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|開啟特殊的自訂資料區段，以在中發出權杖對來源的範圍對應資訊。 當方法已經開啟時開啟此區段，反之亦然，則為錯誤。|  
  
## <a name="requirements"></a>規格需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4 介面](isymunmanagedwriter4-interface.md)
