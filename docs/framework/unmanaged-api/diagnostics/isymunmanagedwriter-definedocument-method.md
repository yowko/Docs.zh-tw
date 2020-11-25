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
ms.openlocfilehash: 6413935df86b85a959fa4f354c6233d18baf99d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727571"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="3e3d8-102">ISymUnmanagedWriter::DefineDocument 方法</span><span class="sxs-lookup"><span data-stu-id="3e3d8-102">ISymUnmanagedWriter::DefineDocument Method</span></span>

<span data-ttu-id="3e3d8-103">定義來源文件。</span><span class="sxs-lookup"><span data-stu-id="3e3d8-103">Defines a source document.</span></span> <span data-ttu-id="3e3d8-104">系統會提供已知語言、廠商和檔案類型的 Guid。</span><span class="sxs-lookup"><span data-stu-id="3e3d8-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e3d8-105">語法</span><span class="sxs-lookup"><span data-stu-id="3e3d8-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e3d8-106">參數</span><span class="sxs-lookup"><span data-stu-id="3e3d8-106">Parameters</span></span>  

 `url`  
 <span data-ttu-id="3e3d8-107">在的指標 `WCHAR` ，定義識別檔 (URL) 的統一資源定位器。</span><span class="sxs-lookup"><span data-stu-id="3e3d8-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="3e3d8-108">在定義檔語言之 GUID 的指標。</span><span class="sxs-lookup"><span data-stu-id="3e3d8-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="3e3d8-109">在GUID 的指標，定義檔語言的廠商識別。</span><span class="sxs-lookup"><span data-stu-id="3e3d8-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="3e3d8-110">在定義檔案類型之 GUID 的指標。</span><span class="sxs-lookup"><span data-stu-id="3e3d8-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3e3d8-111">擴展傳回之 [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="3e3d8-111">[out] A pointer to the returned [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e3d8-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="3e3d8-112">Return Value</span></span>  

 <span data-ttu-id="3e3d8-113">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3e3d8-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e3d8-114">需求</span><span class="sxs-lookup"><span data-stu-id="3e3d8-114">Requirements</span></span>  

 <span data-ttu-id="3e3d8-115">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3e3d8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e3d8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e3d8-116">See also</span></span>

- [<span data-ttu-id="3e3d8-117">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="3e3d8-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
