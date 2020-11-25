---
title: ISymUnmanagedWriter5 介面
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 894f3b0e45df2c681cbdec1f154703be64f32fc5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725790"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 介面

ISymUnmanagedWriter5 介面。  
  
## <a name="syntax"></a>Syntax  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>方法  

 這個介面包含下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans 方法](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|針對權杖對來源範圍的對應資訊，關閉特殊的自訂資料區段。 關閉之後，就無法再加入任何對應資訊。|  
|[MapTokenToSourceSpan 方法](isymunmanagedwriter5-maptokentosourcespan-method.md)|將指定的元資料標記對應至指定原始程式檔中的指定原始程式列範圍。<br /><br /> 必須在呼叫 [OpenMapTokensToSourceSpans 方法](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) 和 [CloseMapTokensToSourceSpans 方法](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)之間呼叫。|  
|[OpenMapTokensToSourceSpans 方法](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|開啟特殊的自訂資料區段，以在中發出權杖對來源範圍的對應資訊。 當方法已經開啟時開啟此區段，反之亦然，則是錯誤。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4 介面](isymunmanagedwriter4-interface.md)
