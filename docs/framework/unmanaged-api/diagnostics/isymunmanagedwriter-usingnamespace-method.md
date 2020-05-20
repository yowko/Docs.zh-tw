---
title: ISymUnmanagedWriter::UsingNamespace 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: e4348cc59924b65b6c6bb53a9c2a98f1a1161b50
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614730"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a>ISymUnmanagedWriter::UsingNamespace 方法
指定在目前開啟的詞法範圍內使用指定的完整命名空間名稱。 命名空間將會用於繼承自目前開啟範圍的所有範圍內。 關閉目前的範圍也會停止使用命名空間。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a>參數  
 `fullName`  
 在命名空間之完整名稱的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
