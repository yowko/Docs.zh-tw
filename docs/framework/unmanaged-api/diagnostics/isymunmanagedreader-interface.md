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
ms.openlocfilehash: 7ae978f5d2c9f7e90f4549c15a3935b441eabf04
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434003"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="7309c-102">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="7309c-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="7309c-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span><span class="sxs-lookup"><span data-stu-id="7309c-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7309c-104">方法</span><span class="sxs-lookup"><span data-stu-id="7309c-104">Methods</span></span>  
  
|<span data-ttu-id="7309c-105">方法</span><span class="sxs-lookup"><span data-stu-id="7309c-105">Method</span></span>|<span data-ttu-id="7309c-106">描述</span><span class="sxs-lookup"><span data-stu-id="7309c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7309c-107">GetDocument 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="7309c-108">Finds a document.</span><span class="sxs-lookup"><span data-stu-id="7309c-108">Finds a document.</span></span>|  
|[<span data-ttu-id="7309c-109">GetDocuments 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="7309c-110">Returns an array of all the documents defined in the symbol store.</span><span class="sxs-lookup"><span data-stu-id="7309c-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="7309c-111">GetDocumentVersion 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="7309c-112">Gets the specified version of the specified document.</span><span class="sxs-lookup"><span data-stu-id="7309c-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="7309c-113">GetGlobalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="7309c-114">Returns all global variables.</span><span class="sxs-lookup"><span data-stu-id="7309c-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="7309c-115">GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="7309c-116">Gets a symbol reader method, given a method token.</span><span class="sxs-lookup"><span data-stu-id="7309c-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="7309c-117">GetMethodByVersion 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="7309c-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span><span class="sxs-lookup"><span data-stu-id="7309c-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="7309c-119">GetMethodFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="7309c-120">Returns the method that contains the breakpoint at the given position in a document.</span><span class="sxs-lookup"><span data-stu-id="7309c-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="7309c-121">GetMethodsFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="7309c-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span><span class="sxs-lookup"><span data-stu-id="7309c-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="7309c-123">GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="7309c-124">Gets the method version.</span><span class="sxs-lookup"><span data-stu-id="7309c-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="7309c-125">GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="7309c-126">Gets the namespaces defined at global scope within this symbol store.</span><span class="sxs-lookup"><span data-stu-id="7309c-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="7309c-127">GetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="7309c-128">Gets a custom attribute based upon its name.</span><span class="sxs-lookup"><span data-stu-id="7309c-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="7309c-129">GetSymbolStoreFileName 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="7309c-130">Provides the on-disk file name of the symbol store.</span><span class="sxs-lookup"><span data-stu-id="7309c-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="7309c-131">GetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="7309c-132">Returns the method that was specified as the user entry point for the module, if any.</span><span class="sxs-lookup"><span data-stu-id="7309c-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="7309c-133">GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="7309c-134">Return a non-local variable, given its parent and name.</span><span class="sxs-lookup"><span data-stu-id="7309c-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="7309c-135">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="7309c-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span><span class="sxs-lookup"><span data-stu-id="7309c-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="7309c-137">ReplaceSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="7309c-138">以差異符號存放區來取代現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="7309c-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="7309c-139">UpdateSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="7309c-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="7309c-140">以差異符號存放區來更新現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="7309c-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7309c-141">需求</span><span class="sxs-lookup"><span data-stu-id="7309c-141">Requirements</span></span>  
 <span data-ttu-id="7309c-142">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7309c-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7309c-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="7309c-143">See also</span></span>

- [<span data-ttu-id="7309c-144">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="7309c-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7309c-145">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="7309c-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
