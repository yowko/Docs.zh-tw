---
title: ISymUnmanagedDispose::Destroy 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
ms.openlocfilehash: e930a9a3753ccf2b8aff798916c876fbedad4df4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430710"
---
# <a name="isymunmanageddisposedestroy-method"></a>ISymUnmanagedDispose::Destroy 方法
Causes the underlying object to release all internal references and return failure on any subsequent method calls.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a>傳回值  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>需求  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>請參閱

- [ISymUnmanagedDispose 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
