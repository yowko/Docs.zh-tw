---
title: ISymUnmanagedAsyncMethod 介面
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 448ed719331469dce8f15500f14d5c1b0707ecf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504448"
---
# <a name="isymunmanagedasyncmethod-interface"></a>ISymUnmanagedAsyncMethod 介面
這個介面是[ISymUnmanagedAsyncMethodPropertiesWriter 介面](isymunmanagedasyncmethodpropertieswriter-interface.md)的讀取補數。  
  
## <a name="syntax"></a>語法  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a>方法  
 這個介面包含下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetAsyncStepInfo 方法](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|請參閱[DefineAsyncStepInfo 方法](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。|  
|[GetAsyncStepInfoCount 方法](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|請參閱[DefineAsyncStepInfo 方法](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。|  
|[GetCatchHandlerILOffset 方法](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|請參閱[DefineCatchHandlerILOffset 方法](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。|  
|[GetKickoffMethod 方法](isymunmanagedasyncmethod-getkickoffmethod-method.md)|請參閱[DefineKickoffMethod 方法](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。|  
|[HasCatchHandlerILOffset 方法](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|請參閱[DefineCatchHandlerILOffset 方法](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。|  
|[IsAsyncMethod 方法](isymunmanagedasyncmethod-isasyncmethod-method.md)|檢查方法是否有非同步資訊。<br /><br /> 如果這個方法傳回，則 `FALSE` 呼叫這個介面中的任何其他方法是不正確。 `E_UNEXPECTED`在此情況下，它們全部都會傳回。|  
  
## <a name="requirements"></a>規格需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
