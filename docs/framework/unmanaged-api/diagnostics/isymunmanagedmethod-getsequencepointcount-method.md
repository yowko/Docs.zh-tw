---
title: ISymUnmanagedMethod::GetSequencePointCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
ms.openlocfilehash: a44f81deb2d57b49f1fd0650fa52c06383210352
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614431"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a>ISymUnmanagedMethod::GetSequencePointCount 方法
取得這個方法內的序列點計數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `pRetVal`  
 脫銷的指標 `ULONG32` ，接收包含序列點所需的緩衝區大小。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedMethod 介面](isymunmanagedmethod-interface.md)
