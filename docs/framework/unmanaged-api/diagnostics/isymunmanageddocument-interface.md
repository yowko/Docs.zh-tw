---
title: "ISymUnmanagedDocument 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument
helpviewer_keywords: ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8654f28cc4d82a5ed1419215807ec3360522fd55
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="ef284-102">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="ef284-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="ef284-103">代表符號存放區所參考的文件。</span><span class="sxs-lookup"><span data-stu-id="ef284-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="ef284-104">文件是由統一資源定位器 (URL) 和 GUID 文件類型定義。</span><span class="sxs-lookup"><span data-stu-id="ef284-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="ef284-105">您可以找出不論如何使用 URL 儲存文件及文件類型的 GUID。</span><span class="sxs-lookup"><span data-stu-id="ef284-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="ef284-106">您可以在符號存放區中儲存的文件來源，並透過此介面擷取它。</span><span class="sxs-lookup"><span data-stu-id="ef284-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef284-107">方法</span><span class="sxs-lookup"><span data-stu-id="ef284-107">Methods</span></span>  
  
|<span data-ttu-id="ef284-108">方法</span><span class="sxs-lookup"><span data-stu-id="ef284-108">Method</span></span>|<span data-ttu-id="ef284-109">說明</span><span class="sxs-lookup"><span data-stu-id="ef284-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef284-110">FindClosestLine 方法</span><span class="sxs-lookup"><span data-stu-id="ef284-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="ef284-111">傳回最接近的一行，也就是序列點，在本文件也可能不是序列點中。</span><span class="sxs-lookup"><span data-stu-id="ef284-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="ef284-112">GetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="ef284-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="ef284-113">取得總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="ef284-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="ef284-114">GetCheckSumAlgorithmId 方法</span><span class="sxs-lookup"><span data-stu-id="ef284-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="ef284-115">取得總和檢查碼演算法識別項，或如果沒有任何總和檢查碼傳回全部為零的 GUID。</span><span class="sxs-lookup"><span data-stu-id="ef284-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="ef284-116">GetDocumentType 方法</span><span class="sxs-lookup"><span data-stu-id="ef284-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="ef284-117">取得這份文件的文件類型。</span><span class="sxs-lookup"><span data-stu-id="ef284-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="ef284-118">GetLanguage 方法</span><span class="sxs-lookup"><span data-stu-id="ef284-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="ef284-119">取得這份文件的語言識別項。</span><span class="sxs-lookup"><span data-stu-id="ef284-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="ef284-120">GetLanguageVendor 方法</span><span class="sxs-lookup"><span data-stu-id="ef284-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="ef284-121">取得這份文件的語言廠商。</span><span class="sxs-lookup"><span data-stu-id="ef284-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="ef284-122">GetSourceLength 方法</span><span class="sxs-lookup"><span data-stu-id="ef284-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="ef284-123">取得內嵌來源的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="ef284-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="ef284-124">GetSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="ef284-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="ef284-125">傳回指定的範圍的內嵌的來源到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ef284-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="ef284-126">GetURL 方法</span><span class="sxs-lookup"><span data-stu-id="ef284-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="ef284-127">傳回這份文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="ef284-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="ef284-128">HasEmbeddedSource 方法</span><span class="sxs-lookup"><span data-stu-id="ef284-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="ef284-129">傳回`true`如果文件來源內嵌在偵錯符號; 否則傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="ef284-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef284-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef284-130">See Also</span></span>  
 [<span data-ttu-id="ef284-131">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="ef284-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
