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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fca7359888b8b73b2e1cf709ab708d71abf0db6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787890"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="67ab8-102">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="67ab8-103">本主題描述 unmanaged 的介面，可讓編譯器產生供偵錯工具符號資訊。</span><span class="sxs-lookup"><span data-stu-id="67ab8-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67ab8-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="67ab8-104">In This Section</span></span>  
 [<span data-ttu-id="67ab8-105">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="67ab8-106">提供方法，它會顯示執行中應用程式的目前繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="67ab8-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="67ab8-107">IDebugAutoAttach 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="67ab8-108">針對伺服器叫用偵錯工具自動附加，請定義的介面。</span><span class="sxs-lookup"><span data-stu-id="67ab8-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="67ab8-109">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="67ab8-110">宣告方法註冊和取消註冊連接的通知來源。</span><span class="sxs-lookup"><span data-stu-id="67ab8-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="67ab8-111">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="67ab8-112">宣告接收通知的方法。</span><span class="sxs-lookup"><span data-stu-id="67ab8-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="67ab8-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="67ab8-114">宣告設定通知篩選器的方法。</span><span class="sxs-lookup"><span data-stu-id="67ab8-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="67ab8-115">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="67ab8-116">提供 [編輯後繼續] 功能的資訊。</span><span class="sxs-lookup"><span data-stu-id="67ab8-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="67ab8-117">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="67ab8-118">這個介面是讀取對補充[ISymUnmanagedAsyncMethodPropertiesWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="67ab8-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="67ab8-119">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="67ab8-120">可讓每個方法符號的選擇性的非同步方法資訊的定義。</span><span class="sxs-lookup"><span data-stu-id="67ab8-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="67ab8-121">必須使用開啟的方法 (也就是呼叫之間[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)並[CloseMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md))。</span><span class="sxs-lookup"><span data-stu-id="67ab8-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="67ab8-122">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="67ab8-123">表示 unmanaged 程式碼的符號繫結器。</span><span class="sxs-lookup"><span data-stu-id="67ab8-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="67ab8-124">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="67ab8-125">表示 unmanaged 程式碼的符號繫結器，並擴充`ISymUnmanagedBinder`介面。</span><span class="sxs-lookup"><span data-stu-id="67ab8-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="67ab8-126">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="67ab8-127">表示 unmanaged 程式碼的符號繫結器，並擴充`ISymUnmanagedBinder`介面。</span><span class="sxs-lookup"><span data-stu-id="67ab8-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="67ab8-128">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="67ab8-129">提供存取未受管理的常數。</span><span class="sxs-lookup"><span data-stu-id="67ab8-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="67ab8-130">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="67ab8-131">處置 unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="67ab8-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="67ab8-132">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="67ab8-133">代表符號存放區所參考的文件。</span><span class="sxs-lookup"><span data-stu-id="67ab8-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="67ab8-134">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="67ab8-135">提供寫入至符號存放區所參考之文件的方法。</span><span class="sxs-lookup"><span data-stu-id="67ab8-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="67ab8-136">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="67ab8-137">提供方法來 [編輯後繼續] 功能。</span><span class="sxs-lookup"><span data-stu-id="67ab8-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="67ab8-138">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="67ab8-139">代表符號存放區內的方法。</span><span class="sxs-lookup"><span data-stu-id="67ab8-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="67ab8-140">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="67ab8-141">代表命名空間。</span><span class="sxs-lookup"><span data-stu-id="67ab8-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="67ab8-142">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="67ab8-143">表示符號讀取器可存取文件、 方法和符號存放區內的變數。</span><span class="sxs-lookup"><span data-stu-id="67ab8-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="67ab8-144">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="67ab8-145">取得指定方法的語彙基元和編輯複製版本號碼的符號讀取器方法。</span><span class="sxs-lookup"><span data-stu-id="67ab8-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="67ab8-146">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="67ab8-147">提供方法，以取得符號搜尋資訊。</span><span class="sxs-lookup"><span data-stu-id="67ab8-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="67ab8-148">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="67ab8-149">表示在方法內的語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="67ab8-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="67ab8-150">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="67ab8-151">表示語彙範圍內的方法，並擴充`ISymUnmanagedScope`介面會使用範圍內取得定義的常數的相關資訊的方法...</span><span class="sxs-lookup"><span data-stu-id="67ab8-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="67ab8-152">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="67ab8-153">提供來源伺服器資料模組。</span><span class="sxs-lookup"><span data-stu-id="67ab8-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="67ab8-154">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="67ab8-155">提供方法，以取得搜尋路徑的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="67ab8-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="67ab8-156">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="67ab8-157">表示變數，例如參數、 區域變數或欄位。</span><span class="sxs-lookup"><span data-stu-id="67ab8-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="67ab8-158">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="67ab8-159">表示的符號寫入器，並提供方法，以定義文件，序列點、 語彙範圍變數。</span><span class="sxs-lookup"><span data-stu-id="67ab8-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="67ab8-160">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="67ab8-161">表示的符號寫入器，並提供方法，以定義文件，序列點、 語彙範圍變數。</span><span class="sxs-lookup"><span data-stu-id="67ab8-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="67ab8-162">擴充`ISymUnmanagedWriter`介面。</span><span class="sxs-lookup"><span data-stu-id="67ab8-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="67ab8-163">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="67ab8-164">表示的符號寫入器，並提供方法，以定義文件，序列點、 語彙範圍變數。</span><span class="sxs-lookup"><span data-stu-id="67ab8-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="67ab8-165">擴充`ISymUnmanagedWriter`介面。</span><span class="sxs-lookup"><span data-stu-id="67ab8-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="67ab8-166">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="67ab8-167">ISymUnmanagedWriter4 介面。</span><span class="sxs-lookup"><span data-stu-id="67ab8-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="67ab8-168">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="67ab8-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="67ab8-169">ISymUnmanagedWriter5 介面。</span><span class="sxs-lookup"><span data-stu-id="67ab8-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="67ab8-170">相關章節</span><span class="sxs-lookup"><span data-stu-id="67ab8-170">Related Sections</span></span>  
 [<span data-ttu-id="67ab8-171">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="67ab8-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="67ab8-172">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="67ab8-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="67ab8-173">偵錯</span><span class="sxs-lookup"><span data-stu-id="67ab8-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
