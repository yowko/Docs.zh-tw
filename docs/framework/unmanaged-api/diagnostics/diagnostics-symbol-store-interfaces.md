---
title: "診斷符號存放區介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 50ef54c90609bf8ef1e3a943664daef95f50d926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="4c595-102">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="4c595-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="4c595-103">本主題描述 unmanaged 的介面，可讓編譯器產生供偵錯工具符號資訊。</span><span class="sxs-lookup"><span data-stu-id="4c595-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c595-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="4c595-104">In This Section</span></span>  
 [<span data-ttu-id="4c595-105">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="4c595-106">提供方法，顯示執行中應用程式的目前繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="4c595-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="4c595-107">IDebugAutoAttach 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="4c595-108">定義介面，伺服器叫用偵錯工具自動附加。</span><span class="sxs-lookup"><span data-stu-id="4c595-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="4c595-109">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="4c595-110">宣告方法註冊及取消註冊連接的通知來源。</span><span class="sxs-lookup"><span data-stu-id="4c595-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="4c595-111">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="4c595-112">宣告接收通知的方法。</span><span class="sxs-lookup"><span data-stu-id="4c595-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="4c595-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="4c595-114">宣告設定通知篩選器的方法。</span><span class="sxs-lookup"><span data-stu-id="4c595-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="4c595-115">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="4c595-116">提供 [編輯後繼續] 功能的資訊。</span><span class="sxs-lookup"><span data-stu-id="4c595-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="4c595-117">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="4c595-118">這個介面是讀取補數[ISymUnmanagedAsyncMethodPropertiesWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="4c595-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="4c595-119">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="4c595-120">可讓選擇性的非同步方法資訊方法符號的定義。</span><span class="sxs-lookup"><span data-stu-id="4c595-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="4c595-121">必須使用開啟的方法 (也就是呼叫之間[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)和[CloseMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md))。</span><span class="sxs-lookup"><span data-stu-id="4c595-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="4c595-122">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="4c595-123">表示 unmanaged 程式碼的符號繫結器。</span><span class="sxs-lookup"><span data-stu-id="4c595-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="4c595-124">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="4c595-125">表示 unmanaged 程式碼的符號繫結器，並擴充`ISymUnmanagedBinder`介面。</span><span class="sxs-lookup"><span data-stu-id="4c595-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="4c595-126">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="4c595-127">表示 unmanaged 程式碼的符號繫結器，並擴充`ISymUnmanagedBinder`介面。</span><span class="sxs-lookup"><span data-stu-id="4c595-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="4c595-128">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="4c595-129">存取未受管理的常數。</span><span class="sxs-lookup"><span data-stu-id="4c595-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="4c595-130">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="4c595-131">處置 unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="4c595-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="4c595-132">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="4c595-133">代表符號存放區所參考的文件。</span><span class="sxs-lookup"><span data-stu-id="4c595-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="4c595-134">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="4c595-135">提供寫入至符號存放區所參考之文件的方法。</span><span class="sxs-lookup"><span data-stu-id="4c595-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="4c595-136">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="4c595-137">提供方法讓 [編輯後繼續] 功能。</span><span class="sxs-lookup"><span data-stu-id="4c595-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="4c595-138">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="4c595-139">代表符號存放區內的方法。</span><span class="sxs-lookup"><span data-stu-id="4c595-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="4c595-140">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="4c595-141">代表命名空間。</span><span class="sxs-lookup"><span data-stu-id="4c595-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="4c595-142">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="4c595-143">代表符號讀取器可存取文件、 方法和符號存放區內的變數。</span><span class="sxs-lookup"><span data-stu-id="4c595-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="4c595-144">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="4c595-145">取得符號讀取器方法，指定方法語彙基元和編輯複製版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4c595-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="4c595-146">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="4c595-147">提供方法，以取得符號搜尋資訊。</span><span class="sxs-lookup"><span data-stu-id="4c595-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="4c595-148">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="4c595-149">表示在方法內的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="4c595-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="4c595-150">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="4c595-151">代表語彙範圍內的方法，並擴充`ISymUnmanagedScope`介面與方法，以取得範圍內定義的常數的相關資訊...</span><span class="sxs-lookup"><span data-stu-id="4c595-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="4c595-152">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="4c595-153">提供模組中的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="4c595-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="4c595-154">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="4c595-155">提供方法，以取得搜尋路徑的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4c595-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="4c595-156">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="4c595-157">表示變數，例如參數、 區域變數或欄位。</span><span class="sxs-lookup"><span data-stu-id="4c595-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="4c595-158">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="4c595-159">代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。</span><span class="sxs-lookup"><span data-stu-id="4c595-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="4c595-160">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="4c595-161">代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。</span><span class="sxs-lookup"><span data-stu-id="4c595-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="4c595-162">擴充`ISymUnmanagedWriter`介面。</span><span class="sxs-lookup"><span data-stu-id="4c595-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="4c595-163">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="4c595-164">代表符號寫入器，並提供方法來定義文件，序列點、 語彙範圍和變數。</span><span class="sxs-lookup"><span data-stu-id="4c595-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="4c595-165">擴充`ISymUnmanagedWriter`介面。</span><span class="sxs-lookup"><span data-stu-id="4c595-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="4c595-166">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="4c595-167">ISymUnmanagedWriter4 介面。</span><span class="sxs-lookup"><span data-stu-id="4c595-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="4c595-168">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="4c595-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="4c595-169">ISymUnmanagedWriter5 介面。</span><span class="sxs-lookup"><span data-stu-id="4c595-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4c595-170">相關章節</span><span class="sxs-lookup"><span data-stu-id="4c595-170">Related Sections</span></span>  
 [<span data-ttu-id="4c595-171">診斷符號存放區列舉型別</span><span class="sxs-lookup"><span data-stu-id="4c595-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="4c595-172">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="4c595-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="4c595-173">偵錯</span><span class="sxs-lookup"><span data-stu-id="4c595-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
