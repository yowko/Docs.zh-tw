---
title: ISymUnmanagedReader::GetDocument 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a173c23ea33532f05e30d072677715e15d04018
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093679"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="34a5c-102">ISymUnmanagedReader::GetDocument 方法</span><span class="sxs-lookup"><span data-stu-id="34a5c-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="34a5c-103">尋找文件。</span><span class="sxs-lookup"><span data-stu-id="34a5c-103">Finds a document.</span></span> <span data-ttu-id="34a5c-104">文件語言、 廠商和類型是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="34a5c-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34a5c-105">語法</span><span class="sxs-lookup"><span data-stu-id="34a5c-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34a5c-106">參數</span><span class="sxs-lookup"><span data-stu-id="34a5c-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="34a5c-107">[in]識別文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="34a5c-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="34a5c-108">[in]文件語言。</span><span class="sxs-lookup"><span data-stu-id="34a5c-108">[in] The document language.</span></span> <span data-ttu-id="34a5c-109">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="34a5c-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="34a5c-110">[in]文件語言廠商的身分識別。</span><span class="sxs-lookup"><span data-stu-id="34a5c-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="34a5c-111">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="34a5c-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="34a5c-112">[in]文件類型。</span><span class="sxs-lookup"><span data-stu-id="34a5c-112">[in] The type of the document.</span></span> <span data-ttu-id="34a5c-113">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="34a5c-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="34a5c-114">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="34a5c-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34a5c-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="34a5c-115">Return Value</span></span>  
 <span data-ttu-id="34a5c-116">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="34a5c-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34a5c-117">需求</span><span class="sxs-lookup"><span data-stu-id="34a5c-117">Requirements</span></span>  
 <span data-ttu-id="34a5c-118">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="34a5c-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34a5c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34a5c-119">See also</span></span>

- [<span data-ttu-id="34a5c-120">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="34a5c-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
