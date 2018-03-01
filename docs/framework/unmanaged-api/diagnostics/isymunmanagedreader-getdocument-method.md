---
title: "ISymUnmanagedReader::GetDocument 方法"
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
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 00ded0e7e88cacbcedb66e1cef27e4f5eaaf4d29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="46cf7-102">ISymUnmanagedReader::GetDocument 方法</span><span class="sxs-lookup"><span data-stu-id="46cf7-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="46cf7-103">尋找文件。</span><span class="sxs-lookup"><span data-stu-id="46cf7-103">Finds a document.</span></span> <span data-ttu-id="46cf7-104">文件語言、 廠商和類型是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="46cf7-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46cf7-105">語法</span><span class="sxs-lookup"><span data-stu-id="46cf7-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46cf7-106">參數</span><span class="sxs-lookup"><span data-stu-id="46cf7-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="46cf7-107">[in]識別文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="46cf7-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="46cf7-108">[in]文件語言。</span><span class="sxs-lookup"><span data-stu-id="46cf7-108">[in] The document language.</span></span> <span data-ttu-id="46cf7-109">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="46cf7-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="46cf7-110">[in]文件語言的廠商識別。</span><span class="sxs-lookup"><span data-stu-id="46cf7-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="46cf7-111">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="46cf7-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="46cf7-112">[in]文件類型。</span><span class="sxs-lookup"><span data-stu-id="46cf7-112">[in] The type of the document.</span></span> <span data-ttu-id="46cf7-113">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="46cf7-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="46cf7-114">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="46cf7-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46cf7-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="46cf7-115">Return Value</span></span>  
 <span data-ttu-id="46cf7-116">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="46cf7-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46cf7-117">需求</span><span class="sxs-lookup"><span data-stu-id="46cf7-117">Requirements</span></span>  
 <span data-ttu-id="46cf7-118">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="46cf7-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46cf7-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="46cf7-119">See Also</span></span>  
 [<span data-ttu-id="46cf7-120">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="46cf7-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
