---
title: ISymUnmanagedDocument::GetDocumentType 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetDocumentType
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7694c9b736700466ac1299b9632440e133109288
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154072"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="7a5bc-102">ISymUnmanagedDocument::GetDocumentType 方法</span><span class="sxs-lookup"><span data-stu-id="7a5bc-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="7a5bc-103">取得此文件的文件類型。</span><span class="sxs-lookup"><span data-stu-id="7a5bc-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a5bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a5bc-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a5bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a5bc-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7a5bc-106">[out]接收文件類型的變數的指標。</span><span class="sxs-lookup"><span data-stu-id="7a5bc-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a5bc-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7a5bc-107">Return Value</span></span>  
 <span data-ttu-id="7a5bc-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="7a5bc-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a5bc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a5bc-109">See also</span></span>

- [<span data-ttu-id="7a5bc-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="7a5bc-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
