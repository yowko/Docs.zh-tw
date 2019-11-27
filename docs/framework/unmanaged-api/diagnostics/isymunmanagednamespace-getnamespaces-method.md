---
title: ISymUnmanagedNamespace::GetNamespaces 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: da2906187c02bbc7a35c937663e3fc7db1ebda13
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433893"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a>ISymUnmanagedNamespace::GetNamespaces 方法
取得這個命名空間的子系。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a>參數  
 `cNameSpaces`  
 在表示 `namespaces` 陣列大小的 `ULONG32`。  
  
 `pcNameSpaces`  
 脫銷`ULONG32` 的指標，接收包含命名空間所需的緩衝區大小（以字元為單位）。  
  
 `namespaces`  
 脫銷包含命名空間之緩衝區的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedNamespace 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
