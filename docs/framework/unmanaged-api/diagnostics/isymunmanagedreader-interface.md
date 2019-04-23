---
title: ISymUnmanagedReader 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0782533f773b69eeeb0b89175e5b22c61e822ed9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147208"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="92491-102">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="92491-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="92491-103">表示符號讀取器可存取文件、 方法和符號存放區內的變數。</span><span class="sxs-lookup"><span data-stu-id="92491-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92491-104">方法</span><span class="sxs-lookup"><span data-stu-id="92491-104">Methods</span></span>  
  
|<span data-ttu-id="92491-105">方法</span><span class="sxs-lookup"><span data-stu-id="92491-105">Method</span></span>|<span data-ttu-id="92491-106">描述</span><span class="sxs-lookup"><span data-stu-id="92491-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92491-107">GetDocument 方法</span><span class="sxs-lookup"><span data-stu-id="92491-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="92491-108">尋找文件。</span><span class="sxs-lookup"><span data-stu-id="92491-108">Finds a document.</span></span>|  
|[<span data-ttu-id="92491-109">GetDocuments 方法</span><span class="sxs-lookup"><span data-stu-id="92491-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="92491-110">傳回定義在符號存放區中的所有文件的陣列。</span><span class="sxs-lookup"><span data-stu-id="92491-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="92491-111">GetDocumentVersion 方法</span><span class="sxs-lookup"><span data-stu-id="92491-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="92491-112">取得指定的文件的指定的版本。</span><span class="sxs-lookup"><span data-stu-id="92491-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="92491-113">GetGlobalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="92491-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="92491-114">傳回所有全域變數。</span><span class="sxs-lookup"><span data-stu-id="92491-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="92491-115">GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="92491-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="92491-116">取得符號讀取器方法，指定方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="92491-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="92491-117">GetMethodByVersion 方法</span><span class="sxs-lookup"><span data-stu-id="92491-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="92491-118">取得符號讀取器方法，指定方法的語彙基元和編輯複製版本號碼。</span><span class="sxs-lookup"><span data-stu-id="92491-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="92491-119">GetMethodFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="92491-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="92491-120">傳回包含文件中指定位置的中斷點的方法。</span><span class="sxs-lookup"><span data-stu-id="92491-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="92491-121">GetMethodsFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="92491-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="92491-122">傳回的陣列的方法，其中每一個包含文件中指定位置的中斷點。</span><span class="sxs-lookup"><span data-stu-id="92491-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="92491-123">GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="92491-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="92491-124">取得方法的版本。</span><span class="sxs-lookup"><span data-stu-id="92491-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="92491-125">GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="92491-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="92491-126">取得在這個符號存放區內的全域範圍中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="92491-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="92491-127">GetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="92491-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="92491-128">取得自訂屬性，根據其名稱。</span><span class="sxs-lookup"><span data-stu-id="92491-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="92491-129">GetSymbolStoreFileName 方法</span><span class="sxs-lookup"><span data-stu-id="92491-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="92491-130">提供符號存放區的磁碟上檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="92491-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="92491-131">GetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="92491-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="92491-132">如果有的話，會傳回已指定為模組的使用者進入點方法。</span><span class="sxs-lookup"><span data-stu-id="92491-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="92491-133">GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="92491-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="92491-134">傳回非本機變數中，指定其父系和名稱。</span><span class="sxs-lookup"><span data-stu-id="92491-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="92491-135">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="92491-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="92491-136">初始化符號讀取器，這個讀取器會與，以及檔案名稱的模組相關聯的中繼資料匯入工具介面。</span><span class="sxs-lookup"><span data-stu-id="92491-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="92491-137">ReplaceSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="92491-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="92491-138">以差異符號存放區來取代現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="92491-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="92491-139">UpdateSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="92491-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="92491-140">以差異符號存放區來更新現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="92491-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92491-141">需求</span><span class="sxs-lookup"><span data-stu-id="92491-141">Requirements</span></span>  
 <span data-ttu-id="92491-142">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="92491-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92491-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92491-143">See also</span></span>

- [<span data-ttu-id="92491-144">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="92491-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="92491-145">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="92491-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
