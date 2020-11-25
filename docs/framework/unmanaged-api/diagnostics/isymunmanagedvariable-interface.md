---
title: ISymUnmanagedVariable 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
ms.openlocfilehash: 93e1f8eb17f06e42ddb243f88c593979fcb28030
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733278"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable 介面

代表變數，例如參數、區域變數或欄位。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetAddressField1 方法](isymunmanagedvariable-getaddressfield1-method.md)|取得這個變數的第一個位址欄位。 其意義取決於位址的種類。|  
|[GetAddressField2 方法](isymunmanagedvariable-getaddressfield2-method.md)|取得這個變數的第二個位址欄位。 其意義取決於位址的種類。|  
|[GetAddressField3 方法](isymunmanagedvariable-getaddressfield3-method.md)|取得這個變數的第三個位址欄位。 其意義取決於位址的種類。|  
|[GetAddressKind 方法](isymunmanagedvariable-getaddresskind-method.md)|取得這個變數的位址種類。|  
|[GetAttributes 方法](isymunmanagedvariable-getattributes-method.md)|取得這個變數的屬性旗標。|  
|[GetEndOffset 方法](isymunmanagedvariable-getendoffset-method.md)|取得此變數在其父系內的結束位移。|  
|[GetName 方法](isymunmanagedvariable-getname-method.md)|取得這個變數的名稱。|  
|[GetSignature 方法](isymunmanagedvariable-getsignature-method.md)|取得這個變數的簽章。|  
|[GetStartOffset 方法](isymunmanagedvariable-getstartoffset-method.md)|取得此變數在其父系內的開始位移。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
