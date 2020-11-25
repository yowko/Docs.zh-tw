---
title: ISymUnmanagedDocument::GetLanguage 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
ms.openlocfilehash: 075d46b0bbc68add0203daf7430afb712c998fe0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700973"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a>ISymUnmanagedDocument::GetLanguage 方法

取得此檔的語言識別項  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a>參數  

 `pRetVal`  
 擴展接收語言識別項之變數的指標。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK。  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedDocument 介面](isymunmanageddocument-interface.md)
