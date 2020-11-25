---
title: ISymUnmanagedDocument::GetURL 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: c862b6d3bfa415b622b68898db1ff30c6759e8f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726934"
---
# <a name="isymunmanageddocumentgeturl-method"></a>ISymUnmanagedDocument::GetURL 方法

傳回此檔 (URL) 的統一資源定位器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a>參數  

 `cchUrl`  
 在緩衝區的大小（以字元為單位） `szURL` 。  
  
 `pcchUrl`  
 擴展變數的指標，此變數會接收 URL 的大小，包括 null 終止。  
  
 `szUrl`  
 擴展包含 URL 的緩衝區。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則為錯誤碼。  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedDocument 介面](isymunmanageddocument-interface.md)
