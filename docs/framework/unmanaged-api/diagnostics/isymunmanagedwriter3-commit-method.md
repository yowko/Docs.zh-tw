---
title: ISymUnmanagedWriter3::Commit 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
ms.openlocfilehash: 5985257a186839a297c245b23f093f0b18a798fe
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438275"
---
# <a name="isymunmanagedwriter3commit-method"></a>ISymUnmanagedWriter3::Commit 方法
Commits the changes written so far to the stream.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a>傳回值  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>需求  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>請參閱

- [ISymUnmanagedWriter3 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
