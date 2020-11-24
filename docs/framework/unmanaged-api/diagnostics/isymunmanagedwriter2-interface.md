---
title: ISymUnmanagedWriter2 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 6feb48b7c78dda64ba372e470b83ffb14f21f2f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683325"
---
# <a name="isymunmanagedwriter2-interface"></a>ISymUnmanagedWriter2 介面

表示符號寫入器，並提供定義文件、序列點、語彙範圍和變數的方法。 這個介面會擴充 [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) 介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DefineConstant2 方法](isymunmanagedwriter2-defineconstant2-method.md)|定義常數值的名稱。|  
|[DefineGlobalVariable2 方法](isymunmanagedwriter2-defineglobalvariable2-method.md)|定義單一全域變數。|  
|[DefineLocalVariable2 方法](isymunmanagedwriter2-definelocalvariable2-method.md)|在目前的語彙範圍中定義單一變數。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter3 介面](isymunmanagedwriter3-interface.md)
