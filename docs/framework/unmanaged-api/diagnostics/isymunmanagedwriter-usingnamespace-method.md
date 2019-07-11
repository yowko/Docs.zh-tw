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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0076b70c85c21f0c4b1fb140b15000f99dbff742
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755142"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a>ISymUnmanagedWriter::UsingNamespace 方法
指定目前開啟的語彙範圍內，正在使用指定的完整命名空間名稱。 將所有領域都繼承自目前開啟的範圍內使用的命名空間。 關閉目前的範圍也會停止使用命名空間。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a>參數  
 `fullName`  
 [in]命名空間的完整格式名稱的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
