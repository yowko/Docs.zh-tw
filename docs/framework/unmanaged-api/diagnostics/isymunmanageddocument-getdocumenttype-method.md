---
title: "ISymUnmanagedDocument::GetDocumentType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetDocumentType
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71b173562412a185b562e86045456a3ce781f4c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a>ISymUnmanagedDocument::GetDocumentType 方法
取得這份文件的文件類型。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]接收文件類型的變數的指標。  
  
## <a name="return-value"></a>傳回值  
 如果此方法成功為 S_OK。  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedDocument 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
