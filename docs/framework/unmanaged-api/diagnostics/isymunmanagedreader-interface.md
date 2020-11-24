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
ms.openlocfilehash: bca84fdba575ed9bfe572b9fd7a5869620962de6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675863"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="0a3f4-102">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="0a3f4-102">ISymUnmanagedReader Interface</span></span>

<span data-ttu-id="0a3f4-103">代表可讓您存取符號存放區內文件、方法和變數的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a3f4-104">方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-104">Methods</span></span>  
  
|<span data-ttu-id="0a3f4-105">方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-105">Method</span></span>|<span data-ttu-id="0a3f4-106">描述</span><span class="sxs-lookup"><span data-stu-id="0a3f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a3f4-107">GetDocument 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-107">GetDocument Method</span></span>](isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="0a3f4-108">尋找檔。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-108">Finds a document.</span></span>|  
|[<span data-ttu-id="0a3f4-109">GetDocuments 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-109">GetDocuments Method</span></span>](isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="0a3f4-110">傳回符號存放區中定義的所有檔的陣列。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="0a3f4-111">GetDocumentVersion 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-111">GetDocumentVersion Method</span></span>](isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="0a3f4-112">取得指定之檔的指定版本。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="0a3f4-113">GetGlobalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-113">GetGlobalVariables Method</span></span>](isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="0a3f4-114">傳回所有全域變數。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="0a3f4-115">GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-115">GetMethod Method</span></span>](isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="0a3f4-116">取得符號讀取器方法（指定方法標記）。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="0a3f4-117">GetMethodByVersion 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-117">GetMethodByVersion Method</span></span>](isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="0a3f4-118">取得符號讀取器方法，指定方法 token 和編輯和複製版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="0a3f4-119">GetMethodFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-119">GetMethodFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="0a3f4-120">傳回方法，這個方法會在檔中的指定位置包含中斷點。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="0a3f4-121">GetMethodsFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-121">GetMethodsFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="0a3f4-122">傳回方法的陣列，其中每一個都包含檔中指定位置的中斷點。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="0a3f4-123">GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-123">GetMethodVersion Method</span></span>](isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="0a3f4-124">取得方法版本。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="0a3f4-125">GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-125">GetNamespaces Method</span></span>](isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="0a3f4-126">取得在此符號存放區內的全域範圍中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="0a3f4-127">GetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-127">GetSymAttribute Method</span></span>](isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="0a3f4-128">根據名稱，取得自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="0a3f4-129">GetSymbolStoreFileName 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-129">GetSymbolStoreFileName Method</span></span>](isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="0a3f4-130">提供符號存放區的磁片上檔案名。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="0a3f4-131">GetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-131">GetUserEntryPoint Method</span></span>](isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="0a3f4-132">傳回指定為模組的使用者進入點的方法（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="0a3f4-133">GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-133">GetVariables Method</span></span>](isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="0a3f4-134">傳回非區域變數，並指定其父系和名稱。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="0a3f4-135">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-135">Initialize Method</span></span>](isymunmanagedreader-initialize-method.md)|<span data-ttu-id="0a3f4-136">使用這個讀取器將與其相關聯的中繼資料匯入工具介面，以及模組的檔案名，初始化符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="0a3f4-137">ReplaceSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-137">ReplaceSymbolStore Method</span></span>](isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="0a3f4-138">以差異符號存放區來取代現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="0a3f4-139">UpdateSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="0a3f4-139">UpdateSymbolStore Method</span></span>](isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="0a3f4-140">以差異符號存放區來更新現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="0a3f4-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a3f4-141">需求</span><span class="sxs-lookup"><span data-stu-id="0a3f4-141">Requirements</span></span>  

 <span data-ttu-id="0a3f4-142">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="0a3f4-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3f4-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a3f4-143">See also</span></span>

- [<span data-ttu-id="0a3f4-144">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="0a3f4-144">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0a3f4-145">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="0a3f4-145">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
