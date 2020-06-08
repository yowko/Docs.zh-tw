---
title: ISymUnmanagedWriter::CloseScope 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: e2e911fb1d737ebb6b2106c89ac11335788ace4f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501725"
---
# <a name="isymunmanagedwriterclosescope-method"></a>ISymUnmanagedWriter::CloseScope 方法
關閉目前的語彙範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a>參數  
 `endOffset`  
 在在詞法範圍中最後一個指令的結尾處，點開頭的位移（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="remarks"></a>備註  
 關閉範圍之後，就無法在其中定義更多變數。  
  
 [ISymUnmanagedWriter：： OpenScope](isymunmanagedwriter-openscope-method.md)會傳回不透明的範圍識別碼，可與[ISymUnmanagedWriter：： SetScopeRange](isymunmanagedwriter-setscoperange-method.md)搭配使用，稍後定義範圍的開始和結束位移。 在這種情況下，傳遞到 `ISymUnmanagedWriter::OpenScope` 和 `ISymUnmanagedWriter::CloseScope` 的位移會被忽略。 範圍識別碼只在目前的方法中有效。  
  
## <a name="requirements"></a>規格需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
