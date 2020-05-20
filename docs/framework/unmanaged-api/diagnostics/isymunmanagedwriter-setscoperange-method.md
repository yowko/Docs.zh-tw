---
title: ISymUnmanagedWriter::SetScopeRange 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
ms.openlocfilehash: b57bb549278f62cdce6ed5deaaa62f154ec919b5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609361"
---
# <a name="isymunmanagedwritersetscoperange-method"></a>ISymUnmanagedWriter::SetScopeRange 方法
定義指定語彙範圍的位移範圍。 範圍會變成新的目前範圍，並推送至範圍的堆疊。 範圍必須形成階層。 同級不允許重迭。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a>參數  
 `scopeId`  
 在範圍的範圍識別碼。  
  
 `startOffset`  
 在在方法開頭的詞法範圍中，第一個指令的位移（以位元組為單位）。  
  
 `endOffset`  
 在從方法開頭的詞法範圍中，最後一個指令的位移（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="remarks"></a>備註  
 [ISymUnmanagedWriter：： OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)會傳回不透明的範圍識別碼，可與搭配使用 `ISymUnmanagedWriter::SetScopeRange` 以定義範圍的開始和結束位移。 在此情況下，傳遞至 `ISymUnmanagedWriter::OpenScope` 和[ISymUnmanagedWriter：： CloseScope](isymunmanagedwriter-closescope-method.md)的位移會被忽略。 範圍識別碼只在目前的方法中有效。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
