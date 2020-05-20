---
title: ISymUnmanagedWriter2::DefineLocalVariable2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
ms.openlocfilehash: ac7559bd5431f45b266602404ddde9081aa2944d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614691"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 方法
在目前的語彙範圍中定義單一變數。 這個方法可以針對相同名稱的變數多次呼叫，其具有整個範圍中的多個家庭。 不過，在此情況下， `startOffset` 和參數的值不能重 `endOffset` 迭。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>參數  
 `name`  
 在本機變數名稱。  
  
 `attributes`  
 在區域變數屬性。  
  
 `sigToken`  
 在簽章的元資料標記。  
  
 `addrKind`  
 在網址類別型。  
  
 `addr1`  
 在參數規格的第一個位址。  
  
 `addr2`  
 在參數規格的第二個位址。  
  
 `addr3`  
 在參數規格的第三個位址。  
  
 `startOffset`  
 在變數的開始位移。 此為選擇性參數。 如果為0，則會忽略此參數，並在整個範圍中定義變數。 如果是非零值，則變數會落在目前範圍的位移內。  
  
 `endOffset`  
 在變數的結束位移。 此為選擇性參數。 如果為0，則會忽略此參數，並在整個範圍中定義變數。 如果是非零值，則變數會落在目前範圍的位移內。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter2 介面](isymunmanagedwriter2-interface.md)
- [DefineLocalVariable 方法](isymunmanagedwriter-definelocalvariable-method.md)
