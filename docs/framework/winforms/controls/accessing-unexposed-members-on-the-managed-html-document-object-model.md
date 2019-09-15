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
ms.openlocfilehash: 525ef52ecbbc61fba787fa8286c56c638d837faf
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988395"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="5a0e3-102">存取 Managed HTML 文件物件模型上未公開的成員</span><span class="sxs-lookup"><span data-stu-id="5a0e3-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="5a0e3-103">Managed HTML 檔案物件模型（DOM）包含一個名<xref:System.Windows.Forms.HtmlElement>為的類別，它會公開所有 HTML 元素通用的屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="5a0e3-104">不過，有時候您需要存取 managed 介面不會直接公開的成員。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="5a0e3-105">本主題將探討兩種存取未公開成員的方式，包括在網頁內定義的 JScript 和 VBScript 函式。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-105">This topic examines two ways for accessing unexposed members, including JScript and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="5a0e3-106">透過 Managed 介面存取未公開的成員</span><span class="sxs-lookup"><span data-stu-id="5a0e3-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="5a0e3-107"><xref:System.Windows.Forms.HtmlDocument>和<xref:System.Windows.Forms.HtmlElement>提供四種方法，可讓您存取未公開的成員。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="5a0e3-108">下表顯示類型及其對應的方法。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="5a0e3-109">成員類型</span><span class="sxs-lookup"><span data-stu-id="5a0e3-109">Member Type</span></span>|<span data-ttu-id="5a0e3-110">方法</span><span class="sxs-lookup"><span data-stu-id="5a0e3-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5a0e3-111">屬性（<xref:System.Windows.Forms.HtmlElement>）</span><span class="sxs-lookup"><span data-stu-id="5a0e3-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="5a0e3-112">方法</span><span class="sxs-lookup"><span data-stu-id="5a0e3-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="5a0e3-113">事件（<xref:System.Windows.Forms.HtmlDocument>）</span><span class="sxs-lookup"><span data-stu-id="5a0e3-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="5a0e3-114">事件（<xref:System.Windows.Forms.HtmlElement>）</span><span class="sxs-lookup"><span data-stu-id="5a0e3-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="5a0e3-115">事件（<xref:System.Windows.Forms.HtmlWindow>）</span><span class="sxs-lookup"><span data-stu-id="5a0e3-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="5a0e3-116">當您使用這些方法時，會假設您有正確基礎類型的元素。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="5a0e3-117">假設您想要接聽`Submit` HTML 網頁上專案`FORM`的事件，讓您可以在使用者將其提交至伺服器之前，對`FORM`的值執行一些前置處理。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="5a0e3-118">在理想的情況下，如果您可以控制 HTML，您會`FORM`將定義為具有`ID`唯一的屬性。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
```html  
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
  
 <span data-ttu-id="5a0e3-119">將此頁面<xref:System.Windows.Forms.WebBrowser>載入控制項之後，您可以<xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>使用方法， `FORM`在執行時間使用`form1`當做引數來取出。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="5a0e3-120">存取未受管理的介面</span><span class="sxs-lookup"><span data-stu-id="5a0e3-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="5a0e3-121">您也可以使用每個 DOM 類別所公開的非受控元件物件模型（COM）介面，來存取 managed HTML DOM 上未公開的成員。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="5a0e3-122">如果您必須對未公開的成員進行數個呼叫，或未公開的成員傳回 managed HTML DOM 未包裝的其他非受控介面，則建議使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="5a0e3-123">下表顯示所有透過 managed HTML DOM 公開的非受控介面。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="5a0e3-124">按一下每個連結以取得其使用方式的說明，以及範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="5a0e3-125">類型</span><span class="sxs-lookup"><span data-stu-id="5a0e3-125">Type</span></span>|<span data-ttu-id="5a0e3-126">非受控介面</span><span class="sxs-lookup"><span data-stu-id="5a0e3-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="5a0e3-127">使用 COM 介面最簡單的方式，就是從您的應用程式加入非受控 HTML DOM 程式庫（MSHTML）的參考，不過這是不支援的作法。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="5a0e3-128">如需詳細資訊，請參閱[知識庫文章 934368](https://support.microsoft.com/kb/934368)。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-128">For more information, see [Knowledge Base Article 934368](https://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="5a0e3-129">存取腳本函式</span><span class="sxs-lookup"><span data-stu-id="5a0e3-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="5a0e3-130">HTML 網頁可以使用指令碼語言（例如 JScript 或 VBScript）來定義一或多個函式。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-130">An HTML page can define one or more functions by using a scripting language such as JScript or VBScript.</span></span> <span data-ttu-id="5a0e3-131">這些函式會放在頁面`SCRIPT`的頁面內，而且可以視需要執行，或是回應 DOM 上的事件。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="5a0e3-132">您可以使用<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>方法，呼叫您在 HTML 網頁中定義的任何腳本函數。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="5a0e3-133">如果腳本方法傳回 HTML 專案，您可以使用 cast 將這個傳回結果<xref:System.Windows.Forms.HtmlElement>轉換成。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="5a0e3-134">如需詳細資訊和範例程式<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>代碼，請參閱。</span><span class="sxs-lookup"><span data-stu-id="5a0e3-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a0e3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a0e3-135">See also</span></span>

- [<span data-ttu-id="5a0e3-136">使用 Managed HTML 文件物件模型</span><span class="sxs-lookup"><span data-stu-id="5a0e3-136">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
