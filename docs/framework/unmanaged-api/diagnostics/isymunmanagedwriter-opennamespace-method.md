---
title: ISymUnmanagedWriter::OpenNamespace 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
ms.openlocfilehash: ab248c6a624fbed1a6783383566be093c449ff97
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609881"
---
# <a name="isymunmanagedwriteropennamespace-method"></a>ISymUnmanagedWriter::OpenNamespace 方法
開啟新的命名空間。 在定義佔用命名空間的方法或變數之前，請先呼叫這個方法。 命名空間可以嵌套。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a>參數  
 `name`  
 在新命名空間名稱的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
- [CloseNamespace 方法](isymunmanagedwriter-closenamespace-method.md)
