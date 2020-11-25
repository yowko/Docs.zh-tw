---
title: ISymUnmanagedReader2 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: 3f34be833d3ccb5c636d2c5f18ccb6e216ef2c49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709072"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 介面

代表可讓您存取符號存放區內文件、方法和變數的符號讀取器。 這個介面會擴充 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap 方法](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|取得符號讀取器方法，並指定方法 token 和編輯後繼續版本號碼。|  
|[GetMethodsInDocument 方法](isymunmanagedreader2-getmethodsindocument-method.md)|取得在提供的檔中有行資訊的每個方法。|  
|[GetSymAttributePreRemap 方法](isymunmanagedreader2-getsymattributepreremap-method.md)|根據名稱，取得自訂屬性。|  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader 介面](isymunmanagedreader-interface.md)
