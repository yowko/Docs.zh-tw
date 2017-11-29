---
title: "ISymUnmanagedDocument::GetURL 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetURL
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 591383fee2f9b22a00956193555c719e72d722bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgeturl-method"></a>ISymUnmanagedDocument::GetURL 方法
傳回這份文件的統一資源定位器 (URL)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
#### <a name="parameters"></a>參數  
 `cchUrl`  
 [in]大小，以字元為單位的`szURL`緩衝區。  
  
 `pcchUrl`  
 [out]大小的 URL，包括 null 結束之變數的指標。  
  
 `szUrl`  
 [out]包含 URL 的緩衝區。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，錯誤代碼。  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedDocument 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
