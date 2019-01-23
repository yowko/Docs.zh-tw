---
title: LinkLabel 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: b39c682ccb73a71da1752e6e9f3f79e5916d106c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503985"
---
# <a name="linklabel-control-overview-windows-forms"></a><span data-ttu-id="75df1-102">LinkLabel 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="75df1-102">LinkLabel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="75df1-103">Windows Form<xref:System.Windows.Forms.LinkLabel>控制項可讓您將 Web 樣式連結新增至 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="75df1-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to add Web-style links to Windows Forms applications.</span></span> <span data-ttu-id="75df1-104">您可以使用<xref:System.Windows.Forms.LinkLabel>控制項，您可以使用的所有項目<xref:System.Windows.Forms.Label>控制; 您也可以設定文字的一部分為檔案、 資料夾或 Web 網頁的連結。</span><span class="sxs-lookup"><span data-stu-id="75df1-104">You can use the <xref:System.Windows.Forms.LinkLabel> control for everything that you can use the <xref:System.Windows.Forms.Label> control for; you also can set part of the text as a link to a file, folder, or Web page.</span></span>  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a><span data-ttu-id="75df1-105">您可以執行使用 LinkLabel 控制項</span><span class="sxs-lookup"><span data-stu-id="75df1-105">What You Can Do with the LinkLabel Control</span></span>  
 <span data-ttu-id="75df1-106">除了所有屬性、 方法和事件<xref:System.Windows.Forms.Label>控制項，<xref:System.Windows.Forms.LinkLabel>控制項有屬性的超連結和連結的色彩。</span><span class="sxs-lookup"><span data-stu-id="75df1-106">In addition to all the properties, methods, and events of the <xref:System.Windows.Forms.Label> control, the <xref:System.Windows.Forms.LinkLabel> control has properties for hyperlinks and link colors.</span></span> <span data-ttu-id="75df1-107"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性設定會啟用連結的文字區域。</span><span class="sxs-lookup"><span data-stu-id="75df1-107">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property sets the area of the text that activates the link.</span></span> <span data-ttu-id="75df1-108"><xref:System.Windows.Forms.LinkLabel.LinkColor%2A>， <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>，和<xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A>屬性設定為連結的色彩。</span><span class="sxs-lookup"><span data-stu-id="75df1-108">The <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> properties set the colors of the link.</span></span> <span data-ttu-id="75df1-109"><xref:System.Windows.Forms.LinkLabel.LinkClicked>事件可讓您判斷選取的連結文字時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="75df1-109">The <xref:System.Windows.Forms.LinkLabel.LinkClicked> event determines what happens when the link text is selected.</span></span>  
  
 <span data-ttu-id="75df1-110">最簡單的用法<xref:System.Windows.Forms.LinkLabel>控制項是顯示單一連結，使用<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性，但您也可以顯示多個超連結使用<xref:System.Windows.Forms.LinkLabel.Links%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="75df1-110">The simplest use of the <xref:System.Windows.Forms.LinkLabel> control is to display a single link using the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property, but you can also display multiple hyperlinks using the <xref:System.Windows.Forms.LinkLabel.Links%2A> property.</span></span> <span data-ttu-id="75df1-111"><xref:System.Windows.Forms.LinkLabel.Links%2A>屬性可讓您存取連結的集合。</span><span class="sxs-lookup"><span data-stu-id="75df1-111">The <xref:System.Windows.Forms.LinkLabel.Links%2A> property enables you to access a collection of links.</span></span> <span data-ttu-id="75df1-112">您也可以指定中的資料<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>屬性的每個個別<xref:System.Windows.Forms.LinkLabel.Link>物件。</span><span class="sxs-lookup"><span data-stu-id="75df1-112">You can also specify data in the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property of each individual <xref:System.Windows.Forms.LinkLabel.Link> object.</span></span> <span data-ttu-id="75df1-113">值<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>屬性可以用來儲存要顯示之檔案的位置或網站的位址。</span><span class="sxs-lookup"><span data-stu-id="75df1-113">The value of the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property can be used to store the location of a file to display or the address of a Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75df1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75df1-114">See also</span></span>
- <xref:System.Windows.Forms.LinkLabel>
- [<span data-ttu-id="75df1-115">Label 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="75df1-115">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)
- [<span data-ttu-id="75df1-116">如何：連結的物件，或使用 Windows Forms LinkLabel 控制項的網頁</span><span class="sxs-lookup"><span data-stu-id="75df1-116">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="75df1-117">如何：變更 Windows Forms LinkLabel 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="75df1-117">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
