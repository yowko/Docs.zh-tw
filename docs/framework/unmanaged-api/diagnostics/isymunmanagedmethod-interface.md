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
ms.openlocfilehash: 7a98a0c40f68cef9bab1ea2de0850208aaef77a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615120"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod 介面
表示符號存放區中的方法。 這個介面只提供存取方法的符號相關屬性，而不是與型別相關的屬性。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetNamespace 方法](isymunmanagedmethod-getnamespace-method.md)|取得在其中定義這個方法的命名空間。|  
|[GetOffset 方法](isymunmanagedmethod-getoffset-method.md)|傳回這個方法內對應于檔內指定位置的位移。|  
|[GetParameters 方法](isymunmanagedmethod-getparameters-method.md)|取得這個方法的參數。|  
|[GetRanges 方法](isymunmanagedmethod-getranges-method.md)|指定檔中的位置時，會傳回開始和結束位移組的陣列，其對應于此方法內的位置所涵蓋的 Microsoft 中繼語言（MSIL）範圍。|  
|[GetRootScope 方法](isymunmanagedmethod-getrootscope-method.md)|取得這個方法內的根詞法範圍。 這個範圍會封入整個方法。|  
|[GetScopeFromOffset 方法](isymunmanagedmethod-getscopefromoffset-method.md)|取得在這個方法中，包含指定之位移的最封入詞法範圍。|  
|[GetSequencePointCount 方法](isymunmanagedmethod-getsequencepointcount-method.md)|取得這個方法內的序列點計數。|  
|[GetSequencePoints 方法](isymunmanagedmethod-getsequencepoints-method.md)|取得這個方法內的所有序列點。|  
|[GetSourceStartEnd 方法](isymunmanagedmethod-getsourcestartend-method.md)|取得這個方法之來源的開始和結束檔位置。|  
|[GetToken 方法](isymunmanagedmethod-gettoken-method.md)|傳回這個方法的中繼資料語彙基元。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
