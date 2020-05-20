---
title: ISymUnmanagedReader::GetSymAttribute 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
ms.openlocfilehash: b7e2814e56765037b69c6ef7ca0ba610dd7d3c95
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614925"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a>ISymUnmanagedReader::GetSymAttribute 方法
依據名稱取得自訂屬性。 不同于中繼資料自訂屬性，這些自訂屬性會保留在符號存放區中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a>參數  
 `parent`  
 在要求其屬性之物件的元資料標記。  
  
 `name`  
 在變數的指標，指出要取得的屬性。  
  
 `cBuffer`  
 [in] `buffer` 陣列的大小。  
  
 `pcBuffer`  
 脫銷接收屬性資料長度之變數的指標。  
  
 `buffer`  
 脫銷接收屬性資料之變數的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedReader 介面](isymunmanagedreader-interface.md)
