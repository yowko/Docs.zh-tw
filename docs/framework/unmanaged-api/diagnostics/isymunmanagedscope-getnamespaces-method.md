---
title: ISymUnmanagedScope::GetNamespaces 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e577fd6bafecb9adaf3b759d100ab21f6b32ffd4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693171"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a>ISymUnmanagedScope::GetNamespaces 方法
取得此範圍內使用的命名空間。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a>參數  
 `cNameSpaces`  
 [in] `namespaces` 陣列的大小。  
  
 `pcNameSpaces`  
 [out]指標`ULONG32`接收包含命名空間所需的緩衝區大小。  
  
 `namespaces`  
 [out]的陣列，接收的命名空間。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱
- [ISymUnmanagedScope 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
