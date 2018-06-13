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
ms.openlocfilehash: 0460086874af38cad348c965237f8c423f18e868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435992"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="1e5bb-102">ISymUnmanagedDocument::GetDocumentType 方法</span><span class="sxs-lookup"><span data-stu-id="1e5bb-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="1e5bb-103">取得這份文件的文件類型。</span><span class="sxs-lookup"><span data-stu-id="1e5bb-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e5bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="1e5bb-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e5bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="1e5bb-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1e5bb-106">[out]接收文件類型的變數的指標。</span><span class="sxs-lookup"><span data-stu-id="1e5bb-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e5bb-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="1e5bb-107">Return Value</span></span>  
 <span data-ttu-id="1e5bb-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="1e5bb-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5bb-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e5bb-109">See Also</span></span>  
 [<span data-ttu-id="1e5bb-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="1e5bb-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
