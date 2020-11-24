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
ms.openlocfilehash: d30ee9318d76aaf3ad2cde789ae292aed54f457e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689676"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="53af6-102">ISymUnmanagedDocument::GetDocumentType 方法</span><span class="sxs-lookup"><span data-stu-id="53af6-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>

<span data-ttu-id="53af6-103">取得此檔的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="53af6-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53af6-104">語法</span><span class="sxs-lookup"><span data-stu-id="53af6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53af6-105">參數</span><span class="sxs-lookup"><span data-stu-id="53af6-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="53af6-106">擴展接收檔案類型之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="53af6-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53af6-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="53af6-107">Return Value</span></span>  

 <span data-ttu-id="53af6-108">如果方法成功，則為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="53af6-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53af6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53af6-109">See also</span></span>

- [<span data-ttu-id="53af6-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="53af6-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
