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
ms.openlocfilehash: e6248aba1c41b2815f2806942d419da869ed94b4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614912"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap 方法
依據名稱取得自訂屬性。 不同于中繼資料自訂屬性，這些屬性會保留在符號存放區中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a>參數  
 `parent`  
 在父系的元資料標記。  
  
 `name`  
 在包含名稱之的指標 `WCHAR` 。  
  
 `cBuffer`  
 在`ULONG32`，指出陣列的大小 `buffer` 。  
  
 `pcBuffer`  
 脫銷的指標 `ULONG32` ，接收包含屬性位元組所需的緩衝區大小。  
  
 `buffer`  
 脫銷接收屬性位元組之緩衝區的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedReader2 介面](isymunmanagedreader2-interface.md)
