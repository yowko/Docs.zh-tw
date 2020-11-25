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
ms.openlocfilehash: 5afc91d1dc6d02f052e860787ebf0858a2f5d12d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730041"
---
# <a name="isymunmanagedwriteropenscope-method"></a>ISymUnmanagedWriter::OpenScope 方法

開啟目前方法中的新語彙範圍。 範圍會變成新的目前範圍，並推送至範圍的堆疊。 範圍必須形成階層。 不允許將同級重迭。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>參數  

 `startOffset`  
 在從方法的開頭開始，詞法範圍中第一個指令的位移（以位元組為單位）。  
  
 `pRetVal`  
 擴展 `ULONG32` 接收範圍識別碼之的指標。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="remarks"></a>備註  

 `ISymUnmanagedWriter::OpenScope` 傳回不透明的範圍識別碼，這個識別碼可以與 [ISymUnmanagedWriter：： SetScopeRange](isymunmanagedwriter-setscoperange-method.md) 搭配使用，以定義稍後的範圍開始和結束位移。 在此情況下， `ISymUnmanagedWriter::OpenScope` 會忽略傳遞給和 [ISymUnmanagedWriter：： CloseScope](isymunmanagedwriter-closescope-method.md) 的位移。 範圍識別碼只有在目前方法中才有效。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
