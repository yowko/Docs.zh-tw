---
title: "存取 Managed HTML 文件物件模型上未公開的成員"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dda2581ceed854fa5121076f0c7b9df414bffe52
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="8f9d9-102">存取 Managed HTML 文件物件模型上未公開的成員</span><span class="sxs-lookup"><span data-stu-id="8f9d9-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="8f9d9-103">Managed HTML 文件物件模型 (DOM) 包含一種類別稱為<xref:System.Windows.Forms.HtmlElement>會公開屬性、 方法和所有 HTML 項目都有通用的事件。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="8f9d9-104">有時候，不過，您將需要存取的受管理的介面不會直接公開的成員。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="8f9d9-105">本主題討論兩種方式來存取未公開的成員，包括[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]和網頁內所定義的 VBScript 函式。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-105">This topic examines two ways for accessing unexposed members, including [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="8f9d9-106">透過 Managed 的介面存取未公開的成員</span><span class="sxs-lookup"><span data-stu-id="8f9d9-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="8f9d9-107"><xref:System.Windows.Forms.HtmlDocument>和<xref:System.Windows.Forms.HtmlElement>提供四種方法，以便存取未公開的成員。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="8f9d9-108">下表顯示類型和其對應的方法。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="8f9d9-109">成員類型</span><span class="sxs-lookup"><span data-stu-id="8f9d9-109">Member Type</span></span>|<span data-ttu-id="8f9d9-110">方法</span><span class="sxs-lookup"><span data-stu-id="8f9d9-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8f9d9-111">屬性 (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="8f9d9-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="8f9d9-112">方法</span><span class="sxs-lookup"><span data-stu-id="8f9d9-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="8f9d9-113">事件 (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="8f9d9-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="8f9d9-114">事件 (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="8f9d9-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="8f9d9-115">事件 (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="8f9d9-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="8f9d9-116">當您使用這些方法時，它會假設您有正確的基礎類型的元素。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="8f9d9-117">假設您想要聆聽`Submit`事件`FORM`上 HTML 項目頁面上，以便您可以在執行某些前置處理`FORM`的值之前，使用者將其提交至伺服器。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="8f9d9-118">在理想情況下，如果您有 HTML 的控制，您會定義`FORM`能夠唯一`ID`屬性。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 <span data-ttu-id="8f9d9-119">載入到這個頁面之後<xref:System.Windows.Forms.WebBrowser>控制項，您可以使用<xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>方法來擷取`FORM`在執行的階段使用`form1`做為引數。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="8f9d9-120">存取未受管理的介面</span><span class="sxs-lookup"><span data-stu-id="8f9d9-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="8f9d9-121">您也可以使用每個 DOM 類別所公開的 unmanaged 的元件物件模型 (COM) 介面，以存取 managed HTML DOM 中未公開的成員。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="8f9d9-122">如果您需要進行數次呼叫針對未公開的成員，或是未公開的成員會傳回其他未受管理的 HTML DOM 所包裝的 unmanaged 的介面，這被建議</span><span class="sxs-lookup"><span data-stu-id="8f9d9-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="8f9d9-123">下表顯示所有 managed HTML dom。 透過公開的 unmanaged 介面</span><span class="sxs-lookup"><span data-stu-id="8f9d9-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="8f9d9-124">如需說明其用法及範例程式碼的每個連結上按一下。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="8f9d9-125">類型</span><span class="sxs-lookup"><span data-stu-id="8f9d9-125">Type</span></span>|<span data-ttu-id="8f9d9-126">Unmanaged 的介面</span><span class="sxs-lookup"><span data-stu-id="8f9d9-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="8f9d9-127">若要使用的 COM 介面最簡單方式是加入至未受管理的 HTML DOM 文件庫 (MSHTML.dll) 的參考，從您的應用程式中，雖然這是不支援。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="8f9d9-128">如需詳細資訊，請參閱[知識庫文章 934368](http://support.microsoft.com/kb/934368)。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-128">For more information, see [Knowledge Base Article 934368](http://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="8f9d9-129">存取指令碼函式</span><span class="sxs-lookup"><span data-stu-id="8f9d9-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="8f9d9-130">HTML 網頁可以定義一個或多個函式，利用指令碼語言，例如[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]或 VBScript。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-130">An HTML page can define one or more functions by using a scripting language such as [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] or VBScript.</span></span> <span data-ttu-id="8f9d9-131">這些函式會放在`SCRIPT`頁面的頁面上，並且可以 DOM 上執行依需求或為了回應事件</span><span class="sxs-lookup"><span data-stu-id="8f9d9-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="8f9d9-132">您可以呼叫您定義在 HTML 頁面使用的任何指令碼函式<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="8f9d9-133">如果指令碼方法傳回的 HTML 項目，您可以使用轉型將這個傳回結果至轉換<xref:System.Windows.Forms.HtmlElement>。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="8f9d9-134">如需詳細資訊和範例程式碼，請參閱<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>。</span><span class="sxs-lookup"><span data-stu-id="8f9d9-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f9d9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f9d9-135">See Also</span></span>  
 [<span data-ttu-id="8f9d9-136">使用 Managed HTML 文件物件模型</span><span class="sxs-lookup"><span data-stu-id="8f9d9-136">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
