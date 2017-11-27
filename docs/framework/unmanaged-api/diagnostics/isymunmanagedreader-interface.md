---
title: "ISymUnmanagedReader 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader
helpviewer_keywords: ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56e0012ae1412c0fb5b434d3b4c0221831296c60
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="1f5c2-102">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="1f5c2-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="1f5c2-103">代表符號讀取器可存取文件、 方法和符號存放區內的變數。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1f5c2-104">方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-104">Methods</span></span>  
  
|<span data-ttu-id="1f5c2-105">方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-105">Method</span></span>|<span data-ttu-id="1f5c2-106">說明</span><span class="sxs-lookup"><span data-stu-id="1f5c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1f5c2-107">GetDocument 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="1f5c2-108">尋找文件。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-108">Finds a document.</span></span>|  
|[<span data-ttu-id="1f5c2-109">GetDocuments 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="1f5c2-110">傳回定義在符號存放區中的所有文件的陣列。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="1f5c2-111">GetDocumentVersion 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="1f5c2-112">取得指定的文件指定的版本。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="1f5c2-113">GetGlobalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="1f5c2-114">傳回所有的全域變數。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="1f5c2-115">GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="1f5c2-116">取得符號讀取器方法，指定方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="1f5c2-117">GetMethodByVersion 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="1f5c2-118">取得符號讀取器方法，指定方法語彙基元和編輯複製版本號碼。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="1f5c2-119">GetMethodFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="1f5c2-120">傳回包含中斷點的文件中指定位置的方法。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="1f5c2-121">GetMethodsFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="1f5c2-122">傳回的陣列的方法，其中每個包含文件中指定位置的中斷點。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="1f5c2-123">GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="1f5c2-124">取得方法的版本。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="1f5c2-125">GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="1f5c2-126">取得在這個符號存放區內的全域範圍定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="1f5c2-127">GetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="1f5c2-128">取得其名稱為基礎的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="1f5c2-129">GetSymbolStoreFileName 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="1f5c2-130">提供符號存放區的磁碟上檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="1f5c2-131">GetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="1f5c2-132">傳回指定為模組的使用者進入點方法，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="1f5c2-133">GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="1f5c2-134">傳回非本機變數，指定其父系和名稱。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="1f5c2-135">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="1f5c2-136">初始化這個讀取器會與，以及檔案名稱的模組相關聯的中繼資料匯入工具介面的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="1f5c2-137">ReplaceSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="1f5c2-138">以差異符號存放區來取代現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="1f5c2-139">UpdateSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="1f5c2-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="1f5c2-140">以差異符號存放區來更新現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="1f5c2-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f5c2-141">需求</span><span class="sxs-lookup"><span data-stu-id="1f5c2-141">Requirements</span></span>  
 <span data-ttu-id="1f5c2-142">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1f5c2-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f5c2-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f5c2-143">See Also</span></span>  
 [<span data-ttu-id="1f5c2-144">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="1f5c2-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="1f5c2-145">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="1f5c2-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
