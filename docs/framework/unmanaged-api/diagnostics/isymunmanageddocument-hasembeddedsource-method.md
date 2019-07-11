---
title: ISymUnmanagedDocument::HasEmbeddedSource 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 459a24e2ed9b97a67dc0266231fdfc32a9c853a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776657"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a>ISymUnmanagedDocument::HasEmbeddedSource 方法
會傳回`true`文件具有來源內嵌在偵錯的符號; 否則會傳回`false`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a>參數  
 `pRetVal`  
 [out]此變數會指出是否有來源文件的指標會內嵌在偵錯符號。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功為 S_OK。  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedDocument 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
