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
ms.openlocfilehash: 044ed5e08a85442c5a73c123cf51529d2fd3f1fc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442172"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="c3c17-102">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="c3c17-103">本主題描述可讓編譯器產生可供偵錯工具使用之符號資訊的非受控介面。</span><span class="sxs-lookup"><span data-stu-id="c3c17-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3c17-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="c3c17-104">In This Section</span></span>  
 [<span data-ttu-id="c3c17-105">IBindingDisplay 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-105">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="c3c17-106">提供方法，顯示有關執行中應用程式的目前系結資訊。</span><span class="sxs-lookup"><span data-stu-id="c3c17-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="c3c17-107">IDebugAutoAttach 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-107">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="c3c17-108">定義伺服器叫用的偵錯工具自動附加的介面。</span><span class="sxs-lookup"><span data-stu-id="c3c17-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="c3c17-109">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-109">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="c3c17-110">宣告註冊和取消註冊連接通知來源的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="c3c17-111">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-111">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="c3c17-112">宣告接收器通知的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="c3c17-113">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="c3c17-114">宣告用於設定通知篩選準則的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="c3c17-115">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="c3c17-116">提供 [編輯後繼續] 功能的資訊。</span><span class="sxs-lookup"><span data-stu-id="c3c17-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="c3c17-117">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-117">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="c3c17-118">這個介面是[ISymUnmanagedAsyncMethodPropertiesWriter 介面](isymunmanagedasyncmethodpropertieswriter-interface.md)的讀取補數。</span><span class="sxs-lookup"><span data-stu-id="c3c17-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="c3c17-119">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="c3c17-120">針對每個方法符號，允許定義選擇性的非同步方法資訊。</span><span class="sxs-lookup"><span data-stu-id="c3c17-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="c3c17-121">必須搭配已開啟的方法使用（也就是在呼叫[OpenMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)和[CloseMethod 方法](isymunmanagedwriter-closemethod-method.md)之間）。</span><span class="sxs-lookup"><span data-stu-id="c3c17-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="c3c17-122">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-122">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="c3c17-123">表示非受控程式碼的符號系結器。</span><span class="sxs-lookup"><span data-stu-id="c3c17-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="c3c17-124">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-124">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="c3c17-125">表示非受控程式碼的符號系結器，並擴充 `ISymUnmanagedBinder` 介面。</span><span class="sxs-lookup"><span data-stu-id="c3c17-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="c3c17-126">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-126">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="c3c17-127">表示非受控程式碼的符號系結器，並擴充 `ISymUnmanagedBinder` 介面。</span><span class="sxs-lookup"><span data-stu-id="c3c17-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="c3c17-128">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-128">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="c3c17-129">提供非受控常數的存取權。</span><span class="sxs-lookup"><span data-stu-id="c3c17-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="c3c17-130">ISymUnmanagedDispose 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-130">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="c3c17-131">處置非受控資源。</span><span class="sxs-lookup"><span data-stu-id="c3c17-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="c3c17-132">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-132">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="c3c17-133">代表符號存放區所參考的文件。</span><span class="sxs-lookup"><span data-stu-id="c3c17-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="c3c17-134">ISymUnmanagedDocumentWriter 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-134">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="c3c17-135">提供寫入至符號存放區所參考之文件的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="c3c17-136">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-136">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="c3c17-137">提供編輯後繼續功能的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="c3c17-138">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-138">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="c3c17-139">表示符號存放區中的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="c3c17-140">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-140">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="c3c17-141">代表命名空間。</span><span class="sxs-lookup"><span data-stu-id="c3c17-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="c3c17-142">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-142">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="c3c17-143">表示符號讀取器，可讓您存取符號存放區中的檔、方法和變數。</span><span class="sxs-lookup"><span data-stu-id="c3c17-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="c3c17-144">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-144">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="c3c17-145">取得指定方法 token 和編輯和複製版本號碼的符號讀取器方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="c3c17-146">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="c3c17-147">提供取得符號搜尋資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="c3c17-148">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-148">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="c3c17-149">表示方法內的詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="c3c17-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="c3c17-150">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-150">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="c3c17-151">表示方法內的詞法範圍，並 `ISymUnmanagedScope` 使用可取得範圍內所定義常數相關資訊的方法來擴充介面。</span><span class="sxs-lookup"><span data-stu-id="c3c17-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="c3c17-152">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-152">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="c3c17-153">提供模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="c3c17-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="c3c17-154">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="c3c17-155">提供取得搜尋路徑相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="c3c17-156">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-156">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="c3c17-157">表示變數，例如參數、本機變數或欄位。</span><span class="sxs-lookup"><span data-stu-id="c3c17-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="c3c17-158">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-158">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="c3c17-159">表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="c3c17-160">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-160">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="c3c17-161">表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="c3c17-162">擴充 `ISymUnmanagedWriter` 介面。</span><span class="sxs-lookup"><span data-stu-id="c3c17-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="c3c17-163">ISymUnmanagedWriter3 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-163">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="c3c17-164">表示符號寫入器，並提供定義檔、序列點、詞法範圍和變數的方法。</span><span class="sxs-lookup"><span data-stu-id="c3c17-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="c3c17-165">擴充 `ISymUnmanagedWriter` 介面。</span><span class="sxs-lookup"><span data-stu-id="c3c17-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="c3c17-166">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-166">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="c3c17-167">ISymUnmanagedWriter4 介面。</span><span class="sxs-lookup"><span data-stu-id="c3c17-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="c3c17-168">ISymUnmanagedWriter5 介面</span><span class="sxs-lookup"><span data-stu-id="c3c17-168">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="c3c17-169">ISymUnmanagedWriter5 介面。</span><span class="sxs-lookup"><span data-stu-id="c3c17-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c3c17-170">相關章節</span><span class="sxs-lookup"><span data-stu-id="c3c17-170">Related Sections</span></span>  
 [<span data-ttu-id="c3c17-171">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="c3c17-171">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="c3c17-172">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="c3c17-172">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="c3c17-173">偵錯</span><span class="sxs-lookup"><span data-stu-id="c3c17-173">Debugging</span></span>](../debugging/index.md)
