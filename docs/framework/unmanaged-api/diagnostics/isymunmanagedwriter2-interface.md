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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbafe39fffd28a9bfccaa275c9009bc03549cda6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriter2-interface"></a>ISymUnmanagedWriter2 介面
代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。 這個介面延伸[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DefineConstant2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|定義常數值的名稱。|  
|[DefineGlobalVariable2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|定義單一的全域變數。|  
|[DefineLocalVariable2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|在目前的語彙範圍中定義單一變數。|  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [ISymUnmanagedWriter3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
