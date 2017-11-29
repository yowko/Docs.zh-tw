---
title: "ISymUnmanagedWriter::DefineDocument 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 638759cb52eb28cc79217da81a867f2593e1ae97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="caea4-102">ISymUnmanagedWriter::DefineDocument 方法</span><span class="sxs-lookup"><span data-stu-id="caea4-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="caea4-103">定義來源文件。</span><span class="sxs-lookup"><span data-stu-id="caea4-103">Defines a source document.</span></span> <span data-ttu-id="caea4-104">Guid 被提供已知的語言、 廠商和文件類型。</span><span class="sxs-lookup"><span data-stu-id="caea4-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caea4-105">語法</span><span class="sxs-lookup"><span data-stu-id="caea4-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="caea4-106">參數</span><span class="sxs-lookup"><span data-stu-id="caea4-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="caea4-107">[in]指標`WCHAR`定義識別文件的統一資源定位器 (URL)。</span><span class="sxs-lookup"><span data-stu-id="caea4-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="caea4-108">[in]定義文件語言的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="caea4-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="caea4-109">[in]識別文件語言的廠商定義的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="caea4-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="caea4-110">[in]定義文件類型的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="caea4-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="caea4-111">[out]所傳回的指標[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="caea4-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="caea4-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="caea4-112">Return Value</span></span>  
 <span data-ttu-id="caea4-113">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="caea4-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caea4-114">需求</span><span class="sxs-lookup"><span data-stu-id="caea4-114">Requirements</span></span>  
 <span data-ttu-id="caea4-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="caea4-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caea4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caea4-116">See Also</span></span>  
 [<span data-ttu-id="caea4-117">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="caea4-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
