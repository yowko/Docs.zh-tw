---
title: ISymUnmanagedVariable::GetSignature 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abd4bb00f5c1e703740462f1709407616ac8a8e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778236"
---
# <a name="isymunmanagedvariablegetsignature-method"></a>ISymUnmanagedVariable::GetSignature 方法
取得這個變數的簽章。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a>參數  
 `cSig`  
 [in]所指向緩衝區的長度`sig`參數。  
  
 `pcSig`  
 [out]指標`ULONG32`接收大小，以字元為單位，以包含簽章所需的緩衝區。  
  
 `sig`  
 [out]儲存簽章的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedVariable 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
