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
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="48047-102">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="48047-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="48047-103">本主題描述可讓編譯器產生可供偵錯工具使用之符號資訊的非受控介面。</span><span class="sxs-lookup"><span data-stu-id="48047-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48047-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="48047-104">In This Section</span></span>  
 [<span data-ttu-id="48047-105">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="48047-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="48047-106">提供方法，顯示有關執行中應用程式的目前系結資訊。</span><span class="sxs-lookup"><span data-stu-id="48047-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="48047-107">IDebugAutoAttach 介面</span><span class="sxs-lookup"><span data-stu-id="48047-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="48047-108">定義伺服器叫用的偵錯工具自動附加的介面。</span><span class="sxs-lookup"><span data-stu-id="48047-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="48047-109">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="48047-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="48047-110">宣告註冊和取消註冊連接通知來源的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="48047-111">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="48047-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="48047-112">宣告接收器通知的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="48047-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="48047-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="48047-114">宣告用於設定通知篩選準則的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="48047-115">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="48047-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="48047-116">提供 [編輯後繼續] 功能的資訊。</span><span class="sxs-lookup"><span data-stu-id="48047-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="48047-117">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="48047-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="48047-118">這個介面是[ISymUnmanagedAsyncMethodPropertiesWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)的讀取補數。</span><span class="sxs-lookup"><span data-stu-id="48047-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="48047-119">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="48047-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="48047-120">針對每個方法符號，允許定義選擇性的非同步方法資訊。</span><span class="sxs-lookup"><span data-stu-id="48047-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="48047-121">必須搭配已開啟的方法使用（也就是在呼叫[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)和[CloseMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)之間）。</span><span class="sxs-lookup"><span data-stu-id="48047-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="48047-122">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="48047-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="48047-123">表示非受控程式碼的符號系結器。</span><span class="sxs-lookup"><span data-stu-id="48047-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="48047-124">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="48047-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="48047-125">表示非受控程式碼的符號系結器，並擴充 `ISymUnmanagedBinder` 介面。</span><span class="sxs-lookup"><span data-stu-id="48047-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="48047-126">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="48047-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="48047-127">表示非受控程式碼的符號系結器，並擴充 `ISymUnmanagedBinder` 介面。</span><span class="sxs-lookup"><span data-stu-id="48047-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="48047-128">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="48047-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="48047-129">提供非受控常數的存取權。</span><span class="sxs-lookup"><span data-stu-id="48047-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="48047-130">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="48047-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="48047-131">處置非受控資源。</span><span class="sxs-lookup"><span data-stu-id="48047-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="48047-132">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="48047-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="48047-133">代表符號存放區所參考的文件。</span><span class="sxs-lookup"><span data-stu-id="48047-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="48047-134">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="48047-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="48047-135">提供寫入至符號存放區所參考之文件的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="48047-136">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="48047-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="48047-137">提供編輯後繼續功能的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="48047-138">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="48047-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="48047-139">表示符號存放區中的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="48047-140">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="48047-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="48047-141">代表命名空間。</span><span class="sxs-lookup"><span data-stu-id="48047-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="48047-142">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="48047-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="48047-143">表示符號讀取器，可讓您存取符號存放區中的檔、方法和變數。</span><span class="sxs-lookup"><span data-stu-id="48047-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="48047-144">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="48047-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="48047-145">取得指定方法 token 和編輯和複製版本號碼的符號讀取器方法。</span><span class="sxs-lookup"><span data-stu-id="48047-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="48047-146">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="48047-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="48047-147">提供取得符號搜尋資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="48047-148">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="48047-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="48047-149">表示方法內的詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="48047-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="48047-150">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="48047-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="48047-151">表示方法內的詞法範圍，並使用可取得範圍內所定義常數相關資訊的方法來擴充 `ISymUnmanagedScope` 介面。</span><span class="sxs-lookup"><span data-stu-id="48047-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="48047-152">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="48047-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="48047-153">提供模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="48047-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="48047-154">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="48047-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="48047-155">提供取得搜尋路徑相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="48047-156">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="48047-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="48047-157">表示變數，例如參數、本機變數或欄位。</span><span class="sxs-lookup"><span data-stu-id="48047-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="48047-158">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="48047-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="48047-159">表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="48047-160">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="48047-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="48047-161">表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="48047-162">擴充 `ISymUnmanagedWriter` 介面。</span><span class="sxs-lookup"><span data-stu-id="48047-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="48047-163">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="48047-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="48047-164">表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。</span><span class="sxs-lookup"><span data-stu-id="48047-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="48047-165">擴充 `ISymUnmanagedWriter` 介面。</span><span class="sxs-lookup"><span data-stu-id="48047-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="48047-166">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="48047-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="48047-167">ISymUnmanagedWriter4 介面。</span><span class="sxs-lookup"><span data-stu-id="48047-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="48047-168">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="48047-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="48047-169">ISymUnmanagedWriter5 介面。</span><span class="sxs-lookup"><span data-stu-id="48047-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="48047-170">相關章節</span><span class="sxs-lookup"><span data-stu-id="48047-170">Related Sections</span></span>  
 [<span data-ttu-id="48047-171">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="48047-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="48047-172">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="48047-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="48047-173">偵錯</span><span class="sxs-lookup"><span data-stu-id="48047-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
