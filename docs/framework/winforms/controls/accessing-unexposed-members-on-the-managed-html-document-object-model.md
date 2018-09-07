---
title: 存取 Managed HTML 文件物件模型上未公開的成員
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: 8767ef0fb484d43ffad4888affebb9d6bb74cc3a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086799"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="55164-102">存取 Managed HTML 文件物件模型上未公開的成員</span><span class="sxs-lookup"><span data-stu-id="55164-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="55164-103">Managed HTML 文件物件模型 (DOM) 包含類別，稱為<xref:System.Windows.Forms.HtmlElement>公開屬性、 方法和所有 HTML 項目都有共通的事件。</span><span class="sxs-lookup"><span data-stu-id="55164-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="55164-104">有時候，不過，您將需要存取受管理的介面不會直接公開的成員。</span><span class="sxs-lookup"><span data-stu-id="55164-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="55164-105">本主題討論兩種方式來存取未公開的成員，包括[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]以及 Web 網頁內定義的 VBScript 函式。</span><span class="sxs-lookup"><span data-stu-id="55164-105">This topic examines two ways for accessing unexposed members, including [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="55164-106">透過受管理的介面存取未公開的成員</span><span class="sxs-lookup"><span data-stu-id="55164-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="55164-107"><xref:System.Windows.Forms.HtmlDocument> 和<xref:System.Windows.Forms.HtmlElement>提供四種方法可讓您存取未公開的成員。</span><span class="sxs-lookup"><span data-stu-id="55164-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="55164-108">下表顯示的型別以及其對應的方法。</span><span class="sxs-lookup"><span data-stu-id="55164-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="55164-109">成員類型</span><span class="sxs-lookup"><span data-stu-id="55164-109">Member Type</span></span>|<span data-ttu-id="55164-110">方法</span><span class="sxs-lookup"><span data-stu-id="55164-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="55164-111">屬性 (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="55164-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="55164-112">方法</span><span class="sxs-lookup"><span data-stu-id="55164-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="55164-113">事件 (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="55164-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="55164-114">事件 (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="55164-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="55164-115">事件 (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="55164-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="55164-116">當您使用這些方法時，它會假設您有正確的基礎類型的項目。</span><span class="sxs-lookup"><span data-stu-id="55164-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="55164-117">假設您想要聆聽`Submit`事件的`FORM`HTML 項目頁面上，以便您可以在執行某些前置處理`FORM`的值之前的使用者將其提交至伺服器。</span><span class="sxs-lookup"><span data-stu-id="55164-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="55164-118">在理想情況下，如果您有 HTML 的控制，您會定義`FORM`有一個唯一`ID`屬性。</span><span class="sxs-lookup"><span data-stu-id="55164-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
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
  
 <span data-ttu-id="55164-119">載入到這個頁面之後<xref:System.Windows.Forms.WebBrowser>控制項，您可以使用<xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>方法來擷取`FORM`在執行的階段使用`form1`做為引數。</span><span class="sxs-lookup"><span data-stu-id="55164-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="55164-120">存取未受管理的介面</span><span class="sxs-lookup"><span data-stu-id="55164-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="55164-121">您也可以使用 DOM 中的每個類別所公開的 unmanaged 的元件物件模型 (COM) 介面來存取 managed HTML DOM 中未公開的成員。</span><span class="sxs-lookup"><span data-stu-id="55164-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="55164-122">如果您必須呼叫幾個針對未公開的成員，或未公開的成員會傳回其他受管理的 HTML dom。 未包裝的 unmanaged 的介面，這被建議</span><span class="sxs-lookup"><span data-stu-id="55164-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="55164-123">下表顯示所有受管理的 HTML dom。 透過公開的 unmanaged 介面</span><span class="sxs-lookup"><span data-stu-id="55164-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="55164-124">按一下每個連結，以了解其使用方式及範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="55164-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="55164-125">類型</span><span class="sxs-lookup"><span data-stu-id="55164-125">Type</span></span>|<span data-ttu-id="55164-126">未受管理的介面</span><span class="sxs-lookup"><span data-stu-id="55164-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="55164-127">若要使用的 COM 介面的最簡單方式是新增至未受管理的 HTML DOM 文件庫 (MSHTML.dll) 的參考，從您的應用程式，雖然這是不支援。</span><span class="sxs-lookup"><span data-stu-id="55164-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="55164-128">如需詳細資訊，請參閱 <<c0> [ 知識庫文章 934368](https://support.microsoft.com/kb/934368)。</span><span class="sxs-lookup"><span data-stu-id="55164-128">For more information, see [Knowledge Base Article 934368](https://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="55164-129">存取指令碼函式</span><span class="sxs-lookup"><span data-stu-id="55164-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="55164-130">HTML 網頁可以定義一或多個函式，藉由使用指令碼語言，例如[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]或 VBScript。</span><span class="sxs-lookup"><span data-stu-id="55164-130">An HTML page can define one or more functions by using a scripting language such as [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] or VBScript.</span></span> <span data-ttu-id="55164-131">這些函式會放在`SCRIPT`在頁面中，頁面上，而且可以在 DOM 執行依需求或為了回應事件</span><span class="sxs-lookup"><span data-stu-id="55164-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="55164-132">您可以呼叫您定義 HTML 頁面使用的任何指令碼函式<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="55164-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="55164-133">如果指令碼方法傳回的 HTML 項目，您可以使用轉換來轉換這個傳回的結果，加<xref:System.Windows.Forms.HtmlElement>。</span><span class="sxs-lookup"><span data-stu-id="55164-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="55164-134">如需詳細資訊和範例程式碼，請參閱<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>。</span><span class="sxs-lookup"><span data-stu-id="55164-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55164-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55164-135">See Also</span></span>  
 [<span data-ttu-id="55164-136">使用 Managed HTML 文件物件模型</span><span class="sxs-lookup"><span data-stu-id="55164-136">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
