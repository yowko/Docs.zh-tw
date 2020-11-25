---
title: ISymUnmanagedDocument::GetSourceLength 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
ms.openlocfilehash: c384fe6c4357c63bc56f9f9b1cc907dea64fddf7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700934"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a>ISymUnmanagedDocument::GetSourceLength 方法

取得內嵌來源的長度 (以位元組為單位)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a>參數  

 `pRetVal`  
 擴展變數的指標，指出內嵌來源的長度（以位元組為單位）。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK。  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedDocument 介面](isymunmanageddocument-interface.md)
