---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
ms.openlocfilehash: a76435be591d9f73d5975c5315f6e744f8972fc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614613"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a>ISymUnmanagedDocument::GetCheckSumAlgorithmId 方法
取得總和檢查碼演算法識別碼，如果沒有總和檢查碼，則傳回所有零的 GUID。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `pRetVal`  
 脫銷接收總和檢查碼演算法識別碼之變數的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK。  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedDocument 介面](isymunmanageddocument-interface.md)
