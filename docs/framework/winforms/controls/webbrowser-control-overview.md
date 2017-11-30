---
title: "WebBrowser 控制項概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c2dfae4cbd7f583ce69ff5591c24a573db0d4e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="webbrowser-control-overview"></a><span data-ttu-id="54770-102">WebBrowser 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="54770-102">WebBrowser Control Overview</span></span>
<span data-ttu-id="54770-103"><xref:System.Windows.Forms.WebBrowser>控制項提供 WebBrowser ActiveX 控制項 managed 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="54770-103">The <xref:System.Windows.Forms.WebBrowser> control provides a managed wrapper for the WebBrowser ActiveX control.</span></span> <span data-ttu-id="54770-104">Managed 包裝函式可讓您在 Windows Form 用戶端應用程式中顯示網頁。</span><span class="sxs-lookup"><span data-stu-id="54770-104">The managed wrapper lets you display Web pages in your Windows Forms client applications.</span></span> <span data-ttu-id="54770-105">您可以使用<xref:System.Windows.Forms.WebBrowser>控制項複製 Internet Explorer Web 瀏覽功能，您的應用程式，或者您可以停用預設的 Internet Explorer 功能和控制項做為簡單的 HTML 文件檢視器。</span><span class="sxs-lookup"><span data-stu-id="54770-105">You can use the <xref:System.Windows.Forms.WebBrowser> control to duplicate Internet Explorer Web browsing functionality in your application or you can disable default Internet Explorer functionality and use the control as a simple HTML document viewer.</span></span> <span data-ttu-id="54770-106">您也可以使用此控制項將 DHTML 為基礎的使用者介面項目加入至表單，隱藏的事實，它們會裝載在<xref:System.Windows.Forms.WebBrowser>控制項。</span><span class="sxs-lookup"><span data-stu-id="54770-106">You can also use the control to add DHTML-based user interface elements to your form and hide the fact that they are hosted in the <xref:System.Windows.Forms.WebBrowser> control.</span></span> <span data-ttu-id="54770-107">這種方法可讓您順暢地結合到單一應用程式的 Windows Form 控制項使用的 Web 控制項。</span><span class="sxs-lookup"><span data-stu-id="54770-107">This approach lets you seamlessly combine Web controls with Windows Forms controls in a single application.</span></span>  
  
## <a name="frequently-used-properties-methods-and-events"></a><span data-ttu-id="54770-108">常用的屬性、 方法和事件</span><span class="sxs-lookup"><span data-stu-id="54770-108">Frequently Used Properties, Methods, and Events</span></span>  
 <span data-ttu-id="54770-109"><xref:System.Windows.Forms.WebBrowser>控制項有數個屬性、 方法和事件，您可以用來實作控制項，Internet Explorer 中。</span><span class="sxs-lookup"><span data-stu-id="54770-109">The <xref:System.Windows.Forms.WebBrowser> control has several properties, methods, and events that you can use to implement controls found in Internet Explorer.</span></span> <span data-ttu-id="54770-110">例如，您可以使用`Navigate`方法，以實作網址列中，而`GoBack`， `GoForward`， `Stop`，和`Refresh`方法來實作工具列上的 瀏覽按鈕。</span><span class="sxs-lookup"><span data-stu-id="54770-110">For example, you can use the `Navigate` method to implement an address bar, and the `GoBack`, `GoForward`, `Stop`, and `Refresh` methods to implement navigation buttons on a toolbar.</span></span> <span data-ttu-id="54770-111">您可以處理`Navigated`事件，以更新其值為 [網址] 列`Url`屬性和標題列的值與`DocumentTitle`屬性。</span><span class="sxs-lookup"><span data-stu-id="54770-111">You can handle the `Navigated` event to update the address bar with the value of the `Url` property and the title bar with the value of the `DocumentTitle` property.</span></span>  
  
 <span data-ttu-id="54770-112">如果您想要產生您自己的網頁內容應用程式中，您可以設定`DocumentText`屬性。</span><span class="sxs-lookup"><span data-stu-id="54770-112">If you want to generate your own page content within your application, you can set the `DocumentText` property.</span></span> <span data-ttu-id="54770-113">如果您是熟悉 HTML 文件物件模型 (DOM)，您也可以處理透過目前網頁的內容`Document`屬性。</span><span class="sxs-lookup"><span data-stu-id="54770-113">If you are familiar with the HTML document object model (DOM), you can also manipulate the contents of the current Web page through the `Document` property.</span></span> <span data-ttu-id="54770-114">具有此屬性，您可以儲存和修改記憶體，而不在檔案之間巡覽的文件。</span><span class="sxs-lookup"><span data-stu-id="54770-114">With this property, you can store and modify documents in memory instead of navigating among files.</span></span>  
  
 <span data-ttu-id="54770-115">`Document`屬性也可讓您呼叫在網頁指令碼從用戶端應用程式程式碼中實作的方法。</span><span class="sxs-lookup"><span data-stu-id="54770-115">The `Document` property also lets you call methods implemented in Web page scripting code from your client application code.</span></span> <span data-ttu-id="54770-116">若要從指令碼程式碼存取您的用戶端應用程式程式碼，設定`ObjectForScripting`屬性。</span><span class="sxs-lookup"><span data-stu-id="54770-116">To access your client application code from your scripting code, set the `ObjectForScripting` property.</span></span> <span data-ttu-id="54770-117">您指定的物件可以存取您的指令碼，做為`window.external`物件。</span><span class="sxs-lookup"><span data-stu-id="54770-117">The object that you specify can be accessed by your script code as the `window.external` object.</span></span>  
  
|<span data-ttu-id="54770-118">名稱</span><span class="sxs-lookup"><span data-stu-id="54770-118">Name</span></span>|<span data-ttu-id="54770-119">描述</span><span class="sxs-lookup"><span data-stu-id="54770-119">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="54770-120"><xref:System.Windows.Forms.WebBrowser.Document%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="54770-120"><xref:System.Windows.Forms.WebBrowser.Document%2A> property</span></span>|<span data-ttu-id="54770-121">取得物件，提供受管理的存取權，目前網頁的 HTML 文件物件模型 (DOM)。</span><span class="sxs-lookup"><span data-stu-id="54770-121">Gets an object that provides managed access to the HTML document object model (DOM) of the current Web page.</span></span>|  
|<span data-ttu-id="54770-122"><xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件</span><span class="sxs-lookup"><span data-stu-id="54770-122"><xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event</span></span>|<span data-ttu-id="54770-123">當網頁載入完畢時，就會發生。</span><span class="sxs-lookup"><span data-stu-id="54770-123">Occurs when a Web page finishes loading.</span></span>|  
|<span data-ttu-id="54770-124"><xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="54770-124"><xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property</span></span>|<span data-ttu-id="54770-125">取得或設定內容的目前網頁的 HTML。</span><span class="sxs-lookup"><span data-stu-id="54770-125">Gets or sets the HTML content of the current Web page.</span></span>|  
|<span data-ttu-id="54770-126"><xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="54770-126"><xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> property</span></span>|<span data-ttu-id="54770-127">取得目前網頁的標題。</span><span class="sxs-lookup"><span data-stu-id="54770-127">Gets the title of the current Web page.</span></span>|  
|<span data-ttu-id="54770-128"><xref:System.Windows.Forms.WebBrowser.GoBack%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="54770-128"><xref:System.Windows.Forms.WebBrowser.GoBack%2A> method</span></span>|<span data-ttu-id="54770-129">巡覽至歷程記錄中的上一頁。</span><span class="sxs-lookup"><span data-stu-id="54770-129">Navigates to the previous page in history.</span></span>|  
|<span data-ttu-id="54770-130"><xref:System.Windows.Forms.WebBrowser.GoForward%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="54770-130"><xref:System.Windows.Forms.WebBrowser.GoForward%2A> method</span></span>|<span data-ttu-id="54770-131">巡覽至歷程記錄的下一個頁面。</span><span class="sxs-lookup"><span data-stu-id="54770-131">Navigates to the next page in history.</span></span>|  
|<span data-ttu-id="54770-132"><xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="54770-132"><xref:System.Windows.Forms.WebBrowser.Navigate%2A> method</span></span>|<span data-ttu-id="54770-133">巡覽至指定的 URL。</span><span class="sxs-lookup"><span data-stu-id="54770-133">Navigates to the specified URL.</span></span>|  
|<span data-ttu-id="54770-134"><xref:System.Windows.Forms.WebBrowser.Navigating>事件</span><span class="sxs-lookup"><span data-stu-id="54770-134"><xref:System.Windows.Forms.WebBrowser.Navigating> event</span></span>|<span data-ttu-id="54770-135">發生於之前瀏覽開始，啟用取消的動作。</span><span class="sxs-lookup"><span data-stu-id="54770-135">Occurs before navigation begins, enabling the action to be canceled.</span></span>|  
|<span data-ttu-id="54770-136"><xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="54770-136"><xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property</span></span>|<span data-ttu-id="54770-137">取得或設定指令碼的網頁可以用來與您的應用程式通訊的物件。</span><span class="sxs-lookup"><span data-stu-id="54770-137">Gets or sets an object that Web page scripting code can use to communicate with your application.</span></span>|  
|<span data-ttu-id="54770-138"><xref:System.Windows.Forms.WebBrowser.Print%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="54770-138"><xref:System.Windows.Forms.WebBrowser.Print%2A> method</span></span>|<span data-ttu-id="54770-139">列印目前頁面。</span><span class="sxs-lookup"><span data-stu-id="54770-139">Prints the current Web page.</span></span>|  
|<span data-ttu-id="54770-140"><xref:System.Windows.Forms.WebBrowser.Refresh%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="54770-140"><xref:System.Windows.Forms.WebBrowser.Refresh%2A> method</span></span>|<span data-ttu-id="54770-141">重新載入目前頁面。</span><span class="sxs-lookup"><span data-stu-id="54770-141">Reloads the current Web page.</span></span>|  
|<span data-ttu-id="54770-142"><xref:System.Windows.Forms.WebBrowser.Stop%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="54770-142"><xref:System.Windows.Forms.WebBrowser.Stop%2A> method</span></span>|<span data-ttu-id="54770-143">中止目前的巡覽和停止音效及動畫等動態頁面項目。</span><span class="sxs-lookup"><span data-stu-id="54770-143">Halts the current navigation and stops dynamic page elements such as sounds and animation.</span></span>|  
|<span data-ttu-id="54770-144"><xref:System.Windows.Forms.WebBrowser.Url%2A> 屬性</span><span class="sxs-lookup"><span data-stu-id="54770-144"><xref:System.Windows.Forms.WebBrowser.Url%2A> property</span></span>|<span data-ttu-id="54770-145">取得或設定目前網頁的 URL。</span><span class="sxs-lookup"><span data-stu-id="54770-145">Gets or sets the URL of the current Web page.</span></span> <span data-ttu-id="54770-146">設定這個屬性可巡覽至新的 URL 控制項。</span><span class="sxs-lookup"><span data-stu-id="54770-146">Setting this property navigates the control to the new URL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54770-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54770-147">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserEncryptionLevel>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>  
 <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserReadyState>  
 <xref:System.Windows.Forms.WebBrowserRefreshOption>  
 [<span data-ttu-id="54770-148">操作說明：使用 WebBrowser 控制項巡覽至 URL</span><span class="sxs-lookup"><span data-stu-id="54770-148">How to: Navigate to a URL with the WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [<span data-ttu-id="54770-149">操作說明：使用 WebBrowser 控制項列印</span><span class="sxs-lookup"><span data-stu-id="54770-149">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)  
 [<span data-ttu-id="54770-150">操作說明：將 Web 瀏覽器功能加入至 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="54770-150">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)  
 [<span data-ttu-id="54770-151">操作說明：在 Windows Forms 應用程式中建立 HTML 文件檢視器</span><span class="sxs-lookup"><span data-stu-id="54770-151">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)  
 [<span data-ttu-id="54770-152">操作說明：實作 DHTML 程式碼和用戶端應用程式程式碼之間的雙向通訊</span><span class="sxs-lookup"><span data-stu-id="54770-152">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)  
 [<span data-ttu-id="54770-153">WebBrowser 安全性</span><span class="sxs-lookup"><span data-stu-id="54770-153">WebBrowser Security</span></span>](../../../../docs/framework/winforms/controls/webbrowser-security.md)
