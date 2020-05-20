---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 053727604c795bf43a9b1658d5841fe85f53090a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614626"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a>ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法
關閉 [特殊自訂資料] 區段，以取得權杖對來源的對應資訊。 關閉之後，就無法再新增任何對應資訊。  
  
## <a name="syntax"></a>語法  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a>傳回值  
 傳回 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter5 介面](isymunmanagedwriter5-interface.md)
