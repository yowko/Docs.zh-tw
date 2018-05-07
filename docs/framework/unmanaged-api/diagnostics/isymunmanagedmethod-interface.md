---
title: ISymUnmanagedMethod 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 728acc09f739fe567fca4a2571cbabf1ba8838a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod 介面
代表符號存放區內的方法。 這個介面提供存取只與符號相關屬性的方法，而非類型相關的屬性。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetNamespace 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|取得在其中定義這個方法的命名空間。|  
|[GetOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|回到文件中的指定位置中對應這個方法內位移。|  
|[GetParameters 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|取得這個方法的參數。|  
|[GetRanges 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|指定的文件中的位置，傳回陣列的開始和結束位移組對應的 Microsoft 中繼語言 (MSIL) 這個方法內的位置所涵蓋的範圍。|  
|[GetRootScope 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|取得這個方法內的根語彙範圍。 這個範圍會封入整個方法。|  
|[GetScopeFromOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|取得圍住儲存指定的位移這個方法內的最封入語彙範圍。|  
|[GetSequencePointCount 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|取得這個方法內的序列點的計數。|  
|[GetSequencePoints 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|取得這個方法內的所有序列點。|  
|[GetSourceStartEnd 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|取得這個方法來源的開始和結束文件位置。|  
|[GetToken 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|傳回這個方法的中繼資料語彙基元。|  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [診斷符號存放區介面](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
