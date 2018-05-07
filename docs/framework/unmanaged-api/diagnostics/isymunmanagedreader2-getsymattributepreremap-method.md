---
title: ISymUnmanagedReader2::GetSymAttributePreRemap 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 326f970f53293b74bbf8c5e77830f3f6ce1b73ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap 方法
取得其名稱為基礎的自訂屬性。 不同於中繼資料的自訂屬性，這些屬性是存放在符號存放區中。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a>參數  
 `parent`  
 [in]父系中繼資料語彙基元。  
  
 `name`  
 [in]指標`WCHAR`其中包含的名稱。  
  
 `cBuffer`  
 [in]A`ULONG32`指出的大小`buffer`陣列。  
  
 `pcBuffer`  
 [out]指標`ULONG32`包含屬性位元組所需要的緩衝區大小。  
  
 `buffer`  
 [out]接收屬性位元組的緩衝區指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedReader2 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
