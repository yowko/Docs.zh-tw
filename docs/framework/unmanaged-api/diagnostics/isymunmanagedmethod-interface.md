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
ms.openlocfilehash: b72a77fecd15a43efbddd9dfd4618897c3372f88
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699270"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod 介面

代表符號存放區內的方法。 這個介面僅提供方法的符號相關屬性的存取權，而不是與型別相關的屬性。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetNamespace 方法](isymunmanagedmethod-getnamespace-method.md)|取得在其中定義此方法的命名空間。|  
|[GetOffset 方法](isymunmanagedmethod-getoffset-method.md)|傳回這個方法中，對應至檔內指定位置的位移。|  
|[GetParameters 方法](isymunmanagedmethod-getparameters-method.md)|取得這個方法的參數。|  
|[GetRanges 方法](isymunmanagedmethod-getranges-method.md)|在檔中指定位置時，會傳回一組開始和結束位移組的陣列，其對應至該位置在此方法內所涵蓋的 Microsoft 中繼語言 (MSIL) 範圍。|  
|[GetRootScope 方法](isymunmanagedmethod-getrootscope-method.md)|取得此方法內的根詞彙範圍。 這個範圍會封入整個方法。|  
|[GetScopeFromOffset 方法](isymunmanagedmethod-getscopefromoffset-method.md)|取得這個方法內的最封閉詞彙範圍，該範圍會括住指定的位移。|  
|[GetSequencePointCount 方法](isymunmanagedmethod-getsequencepointcount-method.md)|取得此方法內的序列點計數。|  
|[GetSequencePoints 方法](isymunmanagedmethod-getsequencepoints-method.md)|取得此方法內的所有序列點。|  
|[GetSourceStartEnd 方法](isymunmanagedmethod-getsourcestartend-method.md)|取得此方法之來源的開始和結束檔位置。|  
|[GetToken 方法](isymunmanagedmethod-gettoken-method.md)|傳回這個方法的中繼資料語彙基元。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
