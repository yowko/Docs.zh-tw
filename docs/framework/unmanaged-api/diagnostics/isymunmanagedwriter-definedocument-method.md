---
title: "ISymUnmanagedWriter::DefineDocument 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 522cc3a63101ec7ebe47e8e23878b9d1b12bca1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="f04b1-102">ISymUnmanagedWriter::DefineDocument 方法</span><span class="sxs-lookup"><span data-stu-id="f04b1-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="f04b1-103">定義來源文件。</span><span class="sxs-lookup"><span data-stu-id="f04b1-103">Defines a source document.</span></span> <span data-ttu-id="f04b1-104">Guid 被提供已知的語言、 廠商和文件類型。</span><span class="sxs-lookup"><span data-stu-id="f04b1-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f04b1-105">語法</span><span class="sxs-lookup"><span data-stu-id="f04b1-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f04b1-106">參數</span><span class="sxs-lookup"><span data-stu-id="f04b1-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="f04b1-107">[in]指標`WCHAR`定義識別文件的統一資源定位器 (URL)。</span><span class="sxs-lookup"><span data-stu-id="f04b1-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="f04b1-108">[in]定義文件語言的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="f04b1-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="f04b1-109">[in]識別文件語言的廠商定義的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="f04b1-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="f04b1-110">[in]定義文件類型的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="f04b1-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f04b1-111">[out]所傳回的指標[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="f04b1-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f04b1-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="f04b1-112">Return Value</span></span>  
 <span data-ttu-id="f04b1-113">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f04b1-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f04b1-114">需求</span><span class="sxs-lookup"><span data-stu-id="f04b1-114">Requirements</span></span>  
 <span data-ttu-id="f04b1-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f04b1-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f04b1-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f04b1-116">See Also</span></span>  
 [<span data-ttu-id="f04b1-117">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="f04b1-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
