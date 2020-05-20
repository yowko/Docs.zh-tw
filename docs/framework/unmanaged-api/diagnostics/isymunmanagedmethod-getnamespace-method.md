---
title: ISymUnmanagedMethod::GetNamespace 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
ms.openlocfilehash: cda30f3c73bf75c37ff79fc415e02382b053807e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614483"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a>ISymUnmanagedMethod::GetNamespace 方法
取得在其中定義這個方法的命名空間。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `pRetVal`  
 脫銷設定為所傳回[ISymUnmanagedNamespace](isymunmanagednamespace-interface.md)介面的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedMethod 介面](isymunmanagedmethod-interface.md)
