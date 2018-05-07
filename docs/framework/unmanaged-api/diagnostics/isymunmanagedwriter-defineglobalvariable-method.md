---
title: ISymUnmanagedWriter::DefineGlobalVariable 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1dd657c004c58480ea2f603ad4494753463c79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a>ISymUnmanagedWriter::DefineGlobalVariable 方法
定義單一的全域變數。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 [in]指標`WCHAR`，定義全域變數的名稱。  
  
 `attributes`  
 [in]全域變數的屬性。  
  
 `cSig`  
 [in]A`ULONG32`指出的大小，以字元為單位的`signature`緩衝區。  
  
 `signature`  
 [in]全域變數簽章。  
  
 `addrKind`  
 [in]地址類型。  
  
 `addr1`  
 [in]參數規格的第一個位址。  
  
 `addr2`  
 [in]參數規格的第二個位址。  
  
 `addr3`  
 [in]參數規格的第三個位址。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [DefineLocalVariable 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)  
 [DefineGlobalVariable2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
