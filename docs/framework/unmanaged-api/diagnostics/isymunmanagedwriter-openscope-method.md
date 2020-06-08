---
title: ISymUnmanagedWriter::OpenScope 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
ms.openlocfilehash: 2808606be24399c9a4fe03df4c53202d31cbbe91
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501712"
---
# <a name="isymunmanagedwriteropenscope-method"></a>ISymUnmanagedWriter::OpenScope 方法
開啟目前方法中的新語彙範圍。 範圍會變成新的目前範圍，並推送至範圍的堆疊。 範圍必須形成階層。 同級不允許重迭。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `startOffset`  
 在從方法開頭算起的詞法範圍中，第一個指令的位移（以位元組為單位）。  
  
 `pRetVal`  
 脫銷`ULONG32`接收範圍識別碼之的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="remarks"></a>備註  
 `ISymUnmanagedWriter::OpenScope`傳回不透明的範圍識別碼，可以與[ISymUnmanagedWriter：： SetScopeRange](isymunmanagedwriter-setscoperange-method.md)搭配使用，以便稍後定義範圍的開始和結束位移。 在此情況下，傳遞至 `ISymUnmanagedWriter::OpenScope` 和[ISymUnmanagedWriter：： CloseScope](isymunmanagedwriter-closescope-method.md)的位移會被忽略。 範圍識別碼只在目前的方法中有效。  
  
## <a name="requirements"></a>規格需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
