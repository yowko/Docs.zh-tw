---
title: ISymUnmanagedAsyncMethodPropertiesWriter 介面
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 779b737da43f61d1023a0a640dce936e11c4704c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707031"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter 介面

可讓您為每個方法符號定義選擇性的非同步方法資訊。 一律與開啟的方法搭配使用;也就是說，呼叫 [OpenMethod 方法](isymunmanagedwriter-openmethod-method.md) 和 [CloseMethod 方法](isymunmanagedwriter-closemethod-method.md)之間的。  
  
## <a name="syntax"></a>Syntax  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>方法  

 這個介面包含下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[DefineAsyncStepInfo 方法](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|在目前方法中定義非同步 await 作業的群組。<br /><br /> 每個 yield 位移都符合 await 的傳回指令，以識別潛在的 yield。 每一組 `breakpointMethod` / `breakpointOffset` 都會識別非同步作業將繼續的位置; 它可能在不同的方法中。|  
|[DefineCatchHandlerILOffset 方法](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|針對包裝非同步方法的編譯器產生的 catch 處理常式，設定 IL 位移。<br /><br /> 偵錯工具會使用所產生之 catch 的 IL 位移來處理 catch，如同非使用者程式碼，即使它可能發生在使用者程式碼方法中也是一樣。 尤其是，它是用來回應 **CatchHandlerFound** 例外狀況事件。|  
|[DefineKickoffMethod 方法](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|設定啟動非同步作業的起始方法。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
