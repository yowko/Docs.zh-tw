---
title: ISymUnmanagedDocument 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33213aced635549dd439cf679d89367a71baa7c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168801"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="cbe26-102">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="cbe26-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="cbe26-103">代表符號存放區所參考的文件。</span><span class="sxs-lookup"><span data-stu-id="cbe26-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="cbe26-104">文件是由統一資源定位器 (URL) 和 GUID 的文件類型定義。</span><span class="sxs-lookup"><span data-stu-id="cbe26-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="cbe26-105">您可以找出文件，不論它使用 URL 的儲存方式和文件類型的 GUID。</span><span class="sxs-lookup"><span data-stu-id="cbe26-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="cbe26-106">您可以在符號存放區中儲存的文件來源，並透過這個介面擷取它。</span><span class="sxs-lookup"><span data-stu-id="cbe26-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cbe26-107">方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-107">Methods</span></span>  
  
|<span data-ttu-id="cbe26-108">方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-108">Method</span></span>|<span data-ttu-id="cbe26-109">描述</span><span class="sxs-lookup"><span data-stu-id="cbe26-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cbe26-110">FindClosestLine 方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="cbe26-111">在此可能會或可能不是序列點的文件中會傳回是序列點，最接近的一行。</span><span class="sxs-lookup"><span data-stu-id="cbe26-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="cbe26-112">GetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="cbe26-113">取得總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="cbe26-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="cbe26-114">GetCheckSumAlgorithmId 方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="cbe26-115">取得總和檢查碼演算法識別項，或如果沒有任何總和檢查碼會傳回全部為零的 GUID。</span><span class="sxs-lookup"><span data-stu-id="cbe26-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="cbe26-116">GetDocumentType 方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="cbe26-117">取得此文件的文件類型。</span><span class="sxs-lookup"><span data-stu-id="cbe26-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="cbe26-118">GetLanguage 方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="cbe26-119">取得這份文件的語言識別碼。</span><span class="sxs-lookup"><span data-stu-id="cbe26-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="cbe26-120">GetLanguageVendor 方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="cbe26-121">取得這份文件的語言廠商。</span><span class="sxs-lookup"><span data-stu-id="cbe26-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="cbe26-122">GetSourceLength 方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="cbe26-123">取得內嵌來源的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="cbe26-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="cbe26-124">GetSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="cbe26-125">傳回指定的範圍的內嵌來源到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="cbe26-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="cbe26-126">GetURL 方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="cbe26-127">傳回這份文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="cbe26-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="cbe26-128">HasEmbeddedSource 方法</span><span class="sxs-lookup"><span data-stu-id="cbe26-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="cbe26-129">會傳回`true`文件具有來源內嵌在偵錯的符號; 否則會傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="cbe26-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbe26-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbe26-130">See also</span></span>

- [<span data-ttu-id="cbe26-131">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="cbe26-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
