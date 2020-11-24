---
title: ISymUnmanagedWriter::DefineField 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: 5683c10938873821cbe998dbf13937a6a7d24d7c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675083"
---
# <a name="isymunmanagedwriterdefinefield-method"></a>ISymUnmanagedWriter::DefineField 方法

定義不在方法內的單一變數。 這個方法用於類別、位欄位等的某些欄位。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>參數  

 `parent`  
 在元資料類型或方法標記。  
  
 `name`  
 在功能變數名稱。  
  
 `attributes`  
 在欄位屬性。  
  
 `cSig`  
 在， `ULONG32` 這是包含欄位簽章所需的緩衝區大小（以字元為單位）。  
  
 `signature`  
 在欄位特徵標記的陣列。  
  
 `addrKind`  
 在網址類別型。  
  
 `addr1`  
 在欄位規格的第一個位址。  
  
 `addr2`  
 在欄位規格的第二個位址。  
  
 `addr3`  
 在欄位規格的第三個位址。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
