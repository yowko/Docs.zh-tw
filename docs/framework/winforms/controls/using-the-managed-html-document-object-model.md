---
title: 使用 Managed HTML 文件物件模型
ms.date: 03/30/2017
helpviewer_keywords:
- managed HTML DOM
ms.assetid: a017dd5c-cd7b-47e4-952c-f4f54cb48409
ms.openlocfilehash: 7800311895d1c0fac43577076226a68712164f60
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878745"
---
# <a name="using-the-managed-html-document-object-model"></a><span data-ttu-id="4559a-102">使用 Managed HTML 文件物件模型</span><span class="sxs-lookup"><span data-stu-id="4559a-102">Using the Managed HTML Document Object Model</span></span>
<span data-ttu-id="4559a-103">受管理的 HTML 文件物件模型 (DOM) 提供的包裝函式，根據[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]HTML 類別公開的 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="4559a-103">The managed HTML document object model (DOM) provides a wrapper based on the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] for the HTML classes exposed by Internet Explorer.</span></span> <span data-ttu-id="4559a-104">使用這些類別來操作中裝載的 HTML 網頁<xref:System.Windows.Forms.WebBrowser>控制項，或建置新的頁面，從一開始。</span><span class="sxs-lookup"><span data-stu-id="4559a-104">Use these classes to manipulate HTML pages hosted in the <xref:System.Windows.Forms.WebBrowser> control, or to build new pages from the beginning.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4559a-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="4559a-105">In This Section</span></span>  
 [<span data-ttu-id="4559a-106">操作說明：存取 Managed HTML 文件物件模型</span><span class="sxs-lookup"><span data-stu-id="4559a-106">How to: Access the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-managed-html-document-object-model.md)  
 <span data-ttu-id="4559a-107">說明如何取得有效的執行個體的<xref:System.Windows.Forms.HtmlDocument>從 Windows Form 應用程式或<xref:System.Windows.Forms.UserControl>裝載於 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="4559a-107">Describes how to obtain a valid instance of <xref:System.Windows.Forms.HtmlDocument> from either a Windows Forms application or a <xref:System.Windows.Forms.UserControl> hosted in Internet Explorer.</span></span>  
  
 [<span data-ttu-id="4559a-108">操作說明：存取 Managed HTML 文件物件模型中的 HTML 原始檔</span><span class="sxs-lookup"><span data-stu-id="4559a-108">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-html-source-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="4559a-109">描述濆爧髍孮原始、 未修改的 HTML 原始檔，以及如何取得的 「 即時 」 的來源，以反映 DOM 的目前狀態</span><span class="sxs-lookup"><span data-stu-id="4559a-109">Describes how to obtain the original, unmodified HTML source, and how to obtain the "live" source that reflects the current state of the DOM.</span></span>  
  
 [<span data-ttu-id="4559a-110">操作說明：變更 Managed HTML 文件物件模型中的元素樣式</span><span class="sxs-lookup"><span data-stu-id="4559a-110">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-change-styles-on-an-element-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="4559a-111">描述如何管理樣式，可用來控制視覺顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="4559a-111">Describes how to manipulate styles, which are used to control the visual display of elements.</span></span>  
  
 [<span data-ttu-id="4559a-112">存取 Managed HTML 文件物件模型中的框架</span><span class="sxs-lookup"><span data-stu-id="4559a-112">Accessing Frames in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-frames-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="4559a-113">描述框架和框架是什麼，以及如何存取框架的 DOM。</span><span class="sxs-lookup"><span data-stu-id="4559a-113">Describes what frames and framesets are, and how to access the DOM of a frame.</span></span>  
  
 [<span data-ttu-id="4559a-114">存取 Managed HTML 文件物件模型上未公開的成員</span><span class="sxs-lookup"><span data-stu-id="4559a-114">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-unexposed-members-on-the-managed-html-document-object-model.md)  
 <span data-ttu-id="4559a-115">描述如何存取基礎 DOM 的受管理的對等項目沒有的成員。</span><span class="sxs-lookup"><span data-stu-id="4559a-115">Describes how to access members of the underlying DOM that do not have a managed equivalent.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4559a-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="4559a-116">Reference</span></span>  
 <xref:System.Windows.Forms.HtmlDocument>  
  
 <xref:System.Windows.Forms.HtmlElement>  
  
 <xref:System.Windows.Forms.HtmlWindow>  
  
## <a name="related-sections"></a><span data-ttu-id="4559a-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="4559a-117">Related Sections</span></span>  
 [<span data-ttu-id="4559a-118">WebBrowser 控制項</span><span class="sxs-lookup"><span data-stu-id="4559a-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
  
## <a name="see-also"></a><span data-ttu-id="4559a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4559a-119">See Also</span></span>  
 [<span data-ttu-id="4559a-120">關於 DHTML 物件模型</span><span class="sxs-lookup"><span data-stu-id="4559a-120">About the DHTML Object Model</span></span>](https://msdn.microsoft.com/library/default.asp?url=/workshop/author/om/doc_object.asp)
