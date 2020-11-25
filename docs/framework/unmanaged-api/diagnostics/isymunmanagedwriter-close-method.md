---
title: ISymUnmanagedWriter::Close 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: 1d684c14f14fcc93040798ae4ee3b8bb1df5354d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733252"
---
# <a name="isymunmanagedwriterclose-method"></a>ISymUnmanagedWriter::Close 方法

將符號認可到符號存放區之後，關閉符號寫入器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="remarks"></a>備註  

 在這個呼叫之後，符號寫入器會變成無效，以供進一步的更新。 若要在不認可符號的情況下關閉符號寫入器，請改用 [ISymUnmanagedWriter：： Abort](isymunmanagedwriter-abort-method.md) 方法。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
