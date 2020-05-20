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
ms.openlocfilehash: a8ff6d3a925773e58e0713a87b167420c246f85b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615562"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="dffa5-102">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="dffa5-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="dffa5-103">代表符號存放區所參考的文件。</span><span class="sxs-lookup"><span data-stu-id="dffa5-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="dffa5-104">檔是由統一資源定位器（URL）和檔案類型 GUID 所定義。</span><span class="sxs-lookup"><span data-stu-id="dffa5-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="dffa5-105">不論檔的儲存方式為何，都可以使用 URL 和檔案類型 GUID 來尋找。</span><span class="sxs-lookup"><span data-stu-id="dffa5-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="dffa5-106">您可以將檔來源儲存在符號存放區中，並透過這個介面加以取出。</span><span class="sxs-lookup"><span data-stu-id="dffa5-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dffa5-107">方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-107">Methods</span></span>  
  
|<span data-ttu-id="dffa5-108">方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-108">Method</span></span>|<span data-ttu-id="dffa5-109">描述</span><span class="sxs-lookup"><span data-stu-id="dffa5-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dffa5-110">FindClosestLine 方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-110">FindClosestLine Method</span></span>](isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="dffa5-111">如果本檔中的行不一定是序列點，則傳回最接近序列點的行。</span><span class="sxs-lookup"><span data-stu-id="dffa5-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="dffa5-112">GetCheckSum 方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-112">GetCheckSum Method</span></span>](isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="dffa5-113">取得總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="dffa5-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="dffa5-114">GetCheckSumAlgorithmId 方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-114">GetCheckSumAlgorithmId Method</span></span>](isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="dffa5-115">取得總和檢查碼演算法識別碼，如果沒有總和檢查碼，則傳回所有零的 GUID。</span><span class="sxs-lookup"><span data-stu-id="dffa5-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="dffa5-116">GetDocumentType 方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-116">GetDocumentType Method</span></span>](isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="dffa5-117">取得此檔的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="dffa5-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="dffa5-118">GetLanguage 方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-118">GetLanguage Method</span></span>](isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="dffa5-119">取得此檔的語言識別項。</span><span class="sxs-lookup"><span data-stu-id="dffa5-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="dffa5-120">GetLanguageVendor 方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-120">GetLanguageVendor Method</span></span>](isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="dffa5-121">取得此檔的語言廠商。</span><span class="sxs-lookup"><span data-stu-id="dffa5-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="dffa5-122">GetSourceLength 方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-122">GetSourceLength Method</span></span>](isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="dffa5-123">取得內嵌來源的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="dffa5-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="dffa5-124">GetSourceRange 方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-124">GetSourceRange Method</span></span>](isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="dffa5-125">將內嵌來源的指定範圍傳回到給定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="dffa5-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="dffa5-126">GetURL 方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-126">GetURL Method</span></span>](isymunmanageddocument-geturl-method.md)|<span data-ttu-id="dffa5-127">傳回此檔的 URL。</span><span class="sxs-lookup"><span data-stu-id="dffa5-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="dffa5-128">HasEmbeddedSource 方法</span><span class="sxs-lookup"><span data-stu-id="dffa5-128">HasEmbeddedSource Method</span></span>](isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="dffa5-129">`true`如果檔的來源內嵌在偵錯工具符號中，則傳回，否則傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="dffa5-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dffa5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dffa5-130">See also</span></span>

- [<span data-ttu-id="dffa5-131">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="dffa5-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
