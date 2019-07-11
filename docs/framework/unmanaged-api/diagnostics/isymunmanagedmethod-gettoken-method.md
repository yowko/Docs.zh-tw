---
title: ISymUnmanagedMethod::GetToken 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1bb9a444d8e8b674d1f173214d8bac427f24e408
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759401"
---
# <a name="isymunmanagedmethodgettoken-method"></a>ISymUnmanagedMethod::GetToken 方法
傳回此方法的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a>參數  
 `pToken`  
 [out]指標`mdMethodDef`接收大小，以字元為單位，以包含中繼資料所需的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
