---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans 方法
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: 43c35596d31842b85bbdc96a63413a176a59a172
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121647"
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
  
## <a name="see-also"></a>請參閱

- [ISymUnmanagedWriter5 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
