---
title: ISymUnmanagedWriter::DefineParameter 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6b01abc16334dbe091e7586efcce1c3e390a64e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterdefineparameter-method"></a>ISymUnmanagedWriter::DefineParameter 方法
定義目前方法中的單一參數。 參數型別是取自方法的簽章中參數的位置 （序列）。  
  
 參數指定方法的中繼資料中定義的如果您沒有使用此方法來重新定義。 符號讀取器必須檢查符號存放區之前先檢查一般參數的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 [in]參數名稱。  
  
 `attributes`  
 [in]參數屬性。  
  
 `sequence`  
 [in]參數簽章。  
  
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
