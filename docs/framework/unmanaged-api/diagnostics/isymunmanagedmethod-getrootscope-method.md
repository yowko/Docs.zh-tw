---
title: ISymUnmanagedMethod::GetRootScope 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8956d72d25f240eff653d3eefb92b68431f4e2ae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771778"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a>ISymUnmanagedMethod::GetRootScope 方法
取得這個方法內的根語彙範圍。 這個範圍會封入整個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `pRetVal`  
 [out]設定指標所傳回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
