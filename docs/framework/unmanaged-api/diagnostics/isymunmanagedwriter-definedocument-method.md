---
title: ISymUnmanagedWriter::DefineDocument 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9a36e094689696b746fcf7f10c282a1b0d9c570
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777833"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="3305a-102">ISymUnmanagedWriter::DefineDocument 方法</span><span class="sxs-lookup"><span data-stu-id="3305a-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="3305a-103">定義來源文件。</span><span class="sxs-lookup"><span data-stu-id="3305a-103">Defines a source document.</span></span> <span data-ttu-id="3305a-104">已知的語言、 廠商和文件類型提供的 Guid。</span><span class="sxs-lookup"><span data-stu-id="3305a-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3305a-105">語法</span><span class="sxs-lookup"><span data-stu-id="3305a-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3305a-106">參數</span><span class="sxs-lookup"><span data-stu-id="3305a-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="3305a-107">[in]指標`WCHAR`定義識別文件的統一資源定位器 (URL)。</span><span class="sxs-lookup"><span data-stu-id="3305a-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="3305a-108">[in]定義文件語言 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="3305a-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="3305a-109">[in]定義文件語言廠商的身分識別的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="3305a-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="3305a-110">[in]定義文件類型的 GUID 指標。</span><span class="sxs-lookup"><span data-stu-id="3305a-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3305a-111">[out]所傳回的指標[ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="3305a-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3305a-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="3305a-112">Return Value</span></span>  
 <span data-ttu-id="3305a-113">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="3305a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3305a-114">需求</span><span class="sxs-lookup"><span data-stu-id="3305a-114">Requirements</span></span>  
 <span data-ttu-id="3305a-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3305a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3305a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3305a-116">See also</span></span>

- [<span data-ttu-id="3305a-117">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="3305a-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
