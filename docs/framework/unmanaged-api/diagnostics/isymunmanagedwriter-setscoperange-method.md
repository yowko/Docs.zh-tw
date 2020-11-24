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
ms.openlocfilehash: 06dff4847ec3d15f446f1c89219b10eddb8eec4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683520"
---
# <a name="isymunmanagedwritersetscoperange-method"></a>ISymUnmanagedWriter::SetScopeRange 方法

定義指定語彙範圍的位移範圍。 範圍會變成新的目前範圍，並推送至範圍的堆疊。 範圍必須形成階層。 不允許將同級重迭。  
  
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
 在從方法開頭之詞法範圍中第一個指令的位移（以位元組為單位）。  
  
 `endOffset`  
 在從方法的開頭之詞法範圍中，最後一個指令的位移（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="remarks"></a>備註  

 [ISymUnmanagedWriter：： OpenScope](isymunmanagedwriter-openscope-method.md) 會傳回不透明的範圍識別碼，這個識別碼可以搭配使用 `ISymUnmanagedWriter::SetScopeRange` ，以定義稍後的範圍開始和結束位移。 在此情況下， `ISymUnmanagedWriter::OpenScope` 會忽略傳遞給和 [ISymUnmanagedWriter：： CloseScope](isymunmanagedwriter-closescope-method.md) 的位移。 範圍識別碼只有在目前方法中才有效。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
