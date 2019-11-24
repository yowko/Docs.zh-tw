---
title: 診斷符號存放區介面
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: bdb691570a9a2bf7bd2bb21af500b06c10b0bc53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448533"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="bb367-102">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="bb367-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="bb367-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span><span class="sxs-lookup"><span data-stu-id="bb367-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb367-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="bb367-104">In This Section</span></span>  
 [<span data-ttu-id="bb367-105">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="bb367-106">Provides methods that display current binding information about the running application.</span><span class="sxs-lookup"><span data-stu-id="bb367-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="bb367-107">IDebugAutoAttach 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="bb367-108">Defines the interface for a server-invoked debugger auto attach.</span><span class="sxs-lookup"><span data-stu-id="bb367-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="bb367-109">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="bb367-110">Declares methods for registering and unregistering a connection notification source.</span><span class="sxs-lookup"><span data-stu-id="bb367-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="bb367-111">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="bb367-112">Declares methods for sink notification.</span><span class="sxs-lookup"><span data-stu-id="bb367-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="bb367-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="bb367-114">Declares a method for setting notification filters.</span><span class="sxs-lookup"><span data-stu-id="bb367-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="bb367-115">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="bb367-116">Provides information for the Edit and Continue feature.</span><span class="sxs-lookup"><span data-stu-id="bb367-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="bb367-117">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="bb367-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bb367-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="bb367-119">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="bb367-120">Allows definition of optional async method information per method symbol.</span><span class="sxs-lookup"><span data-stu-id="bb367-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="bb367-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="bb367-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="bb367-122">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="bb367-123">Represents a symbol binder for unmanaged code.</span><span class="sxs-lookup"><span data-stu-id="bb367-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="bb367-124">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="bb367-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="bb367-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="bb367-126">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="bb367-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="bb367-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="bb367-128">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="bb367-129">Provides access to unmanaged constants.</span><span class="sxs-lookup"><span data-stu-id="bb367-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="bb367-130">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="bb367-131">Disposes of unmanaged resources.</span><span class="sxs-lookup"><span data-stu-id="bb367-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="bb367-132">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="bb367-133">代表符號存放區所參考的文件。</span><span class="sxs-lookup"><span data-stu-id="bb367-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="bb367-134">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="bb367-135">提供寫入至符號存放區所參考之文件的方法。</span><span class="sxs-lookup"><span data-stu-id="bb367-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="bb367-136">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="bb367-137">Provides methods for the Edit and Continue feature.</span><span class="sxs-lookup"><span data-stu-id="bb367-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="bb367-138">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="bb367-139">Represents a method within the symbol store.</span><span class="sxs-lookup"><span data-stu-id="bb367-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="bb367-140">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="bb367-141">Represents a namespace.</span><span class="sxs-lookup"><span data-stu-id="bb367-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="bb367-142">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="bb367-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span><span class="sxs-lookup"><span data-stu-id="bb367-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="bb367-144">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="bb367-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span><span class="sxs-lookup"><span data-stu-id="bb367-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="bb367-146">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="bb367-147">Provides methods that get symbol search information.</span><span class="sxs-lookup"><span data-stu-id="bb367-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="bb367-148">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="bb367-149">Represents a lexical scope within a method.</span><span class="sxs-lookup"><span data-stu-id="bb367-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="bb367-150">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="bb367-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span><span class="sxs-lookup"><span data-stu-id="bb367-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="bb367-152">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="bb367-153">Provides source server data for a module.</span><span class="sxs-lookup"><span data-stu-id="bb367-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="bb367-154">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="bb367-155">Provides methods that get information about the search path.</span><span class="sxs-lookup"><span data-stu-id="bb367-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="bb367-156">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="bb367-157">Represents a variable, such as a parameter, a local variable, or a field.</span><span class="sxs-lookup"><span data-stu-id="bb367-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="bb367-158">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="bb367-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span><span class="sxs-lookup"><span data-stu-id="bb367-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="bb367-160">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="bb367-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span><span class="sxs-lookup"><span data-stu-id="bb367-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="bb367-162">Extends the `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="bb367-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="bb367-163">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="bb367-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span><span class="sxs-lookup"><span data-stu-id="bb367-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="bb367-165">Extends the `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="bb367-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="bb367-166">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="bb367-167">ISymUnmanagedWriter4 interface.</span><span class="sxs-lookup"><span data-stu-id="bb367-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="bb367-168">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="bb367-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="bb367-169">ISymUnmanagedWriter5 interface.</span><span class="sxs-lookup"><span data-stu-id="bb367-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bb367-170">相關章節</span><span class="sxs-lookup"><span data-stu-id="bb367-170">Related Sections</span></span>  
 [<span data-ttu-id="bb367-171">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="bb367-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="bb367-172">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="bb367-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="bb367-173">偵錯</span><span class="sxs-lookup"><span data-stu-id="bb367-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
