---
title: ISymUnmanagedScope::GetChildren 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: 8f3c83a7a89553ba600f3e0e368eec0ddd0350e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727604"
---
# <a name="isymunmanagedscopegetchildren-method"></a>ISymUnmanagedScope::GetChildren 方法

取得此範圍的子系。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a>參數  

 `cChildren`  
 在 `ULONG32` ，指出陣列的大小 `children` 。  
  
 `pcChildren`  
 擴展的指標 `ULONG32` ，會接收包含子系所需的緩衝區大小。  
  
 `children`  
 擴展傳回的子係數組。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedScope 介面](isymunmanagedscope-interface.md)
- [GetParent 方法](isymunmanagedscope-getparent-method.md)
