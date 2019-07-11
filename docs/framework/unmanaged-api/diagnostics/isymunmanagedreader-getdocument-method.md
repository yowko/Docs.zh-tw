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
ms.openlocfilehash: 32b7505a9e512f3c3e3e7a9fcbff40276e98ecf4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759343"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="64a11-102">ISymUnmanagedReader::GetDocument 方法</span><span class="sxs-lookup"><span data-stu-id="64a11-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="64a11-103">尋找文件。</span><span class="sxs-lookup"><span data-stu-id="64a11-103">Finds a document.</span></span> <span data-ttu-id="64a11-104">文件語言、 廠商和類型是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="64a11-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64a11-105">語法</span><span class="sxs-lookup"><span data-stu-id="64a11-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64a11-106">參數</span><span class="sxs-lookup"><span data-stu-id="64a11-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="64a11-107">[in]識別文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="64a11-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="64a11-108">[in]文件語言。</span><span class="sxs-lookup"><span data-stu-id="64a11-108">[in] The document language.</span></span> <span data-ttu-id="64a11-109">這個參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="64a11-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="64a11-110">[in]文件語言廠商的身分識別。</span><span class="sxs-lookup"><span data-stu-id="64a11-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="64a11-111">這個參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="64a11-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="64a11-112">[in]文件類型。</span><span class="sxs-lookup"><span data-stu-id="64a11-112">[in] The type of the document.</span></span> <span data-ttu-id="64a11-113">這個參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="64a11-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="64a11-114">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="64a11-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64a11-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="64a11-115">Return Value</span></span>  
 <span data-ttu-id="64a11-116">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="64a11-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64a11-117">需求</span><span class="sxs-lookup"><span data-stu-id="64a11-117">Requirements</span></span>  
 <span data-ttu-id="64a11-118">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="64a11-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64a11-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64a11-119">See also</span></span>

- [<span data-ttu-id="64a11-120">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="64a11-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
