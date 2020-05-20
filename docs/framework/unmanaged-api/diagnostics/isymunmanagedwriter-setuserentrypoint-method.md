---
title: ISymUnmanagedWriter::SetUserEntryPoint 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
ms.openlocfilehash: 8b51a9dc3a968c6bd2f5f9b149f13f88dc6a1e05
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614743"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a>ISymUnmanagedWriter::SetUserEntryPoint 方法
指定使用者定義的方法，這是此模組的進入點。 例如，這個進入點可能是使用者的 main 方法，而不是編譯器在 main 之前產生的 stub。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a>參數  
 `entryMethod`  
 在使用者進入點之方法的元資料標記。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
