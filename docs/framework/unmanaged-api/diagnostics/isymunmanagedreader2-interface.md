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
ms.openlocfilehash: d4c5ff46d37b1292059b18920abd8042c18bbf31
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615393"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 介面
表示符號讀取器，可讓您存取符號存放區中的檔、方法和變數。 這個介面會擴充[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap 方法](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|取得符號讀取器方法，並指定方法權杖和編輯後繼續版本號碼。|  
|[GetMethodsInDocument 方法](isymunmanagedreader2-getmethodsindocument-method.md)|取得提供的檔中具有行資訊的每一個方法。|  
|[GetSymAttributePreRemap 方法](isymunmanagedreader2-getsymattributepreremap-method.md)|依據名稱取得自訂屬性。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader 介面](isymunmanagedreader-interface.md)
