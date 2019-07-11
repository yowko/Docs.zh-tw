---
title: ISymUnmanagedWriter::DefineConstant 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a04bf93a2b2809198673d15f29714f52c9435b68
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767836"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a>ISymUnmanagedWriter::DefineConstant 方法
定義常值的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a>參數  
 `name`  
 [in]指標`WCHAR`定義常數的名稱。  
  
 `value`  
 [in]常數的值。  
  
 `cSig`  
 [in] `signature` 陣列的大小。  
  
 `signature`  
 [in]常數類型簽章。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [DefineConstant2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
