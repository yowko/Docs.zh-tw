---
title: LinkLabel 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 9837902bf56a402d623adbcf41558dcc568b7105
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745219"
---
# <a name="linklabel-control-overview-windows-forms"></a><span data-ttu-id="45b62-102">LinkLabel 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="45b62-102">LinkLabel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="45b62-103">Windows Forms <xref:System.Windows.Forms.LinkLabel> 控制項可讓您將 Web 樣式的連結新增至 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="45b62-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to add Web-style links to Windows Forms applications.</span></span> <span data-ttu-id="45b62-104">您可以針對可以使用 <xref:System.Windows.Forms.Label> 控制項的所有專案使用 <xref:System.Windows.Forms.LinkLabel> 控制項;您也可以將部分文字設定為檔案、資料夾或網頁的連結。</span><span class="sxs-lookup"><span data-stu-id="45b62-104">You can use the <xref:System.Windows.Forms.LinkLabel> control for everything that you can use the <xref:System.Windows.Forms.Label> control for; you also can set part of the text as a link to a file, folder, or Web page.</span></span>  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a><span data-ttu-id="45b62-105">您可以使用 LinkLabel 控制項執行的動作</span><span class="sxs-lookup"><span data-stu-id="45b62-105">What You Can Do with the LinkLabel Control</span></span>  
 <span data-ttu-id="45b62-106">除了 <xref:System.Windows.Forms.Label> 控制項的所有屬性、方法和事件之外，<xref:System.Windows.Forms.LinkLabel> 控制項也具有超連結和連結色彩的屬性。</span><span class="sxs-lookup"><span data-stu-id="45b62-106">In addition to all the properties, methods, and events of the <xref:System.Windows.Forms.Label> control, the <xref:System.Windows.Forms.LinkLabel> control has properties for hyperlinks and link colors.</span></span> <span data-ttu-id="45b62-107"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性會設定啟動連結之文字的區域。</span><span class="sxs-lookup"><span data-stu-id="45b62-107">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property sets the area of the text that activates the link.</span></span> <span data-ttu-id="45b62-108">[<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>]、[<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>] 和 [<xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A>] 屬性會設定連結的色彩。</span><span class="sxs-lookup"><span data-stu-id="45b62-108">The <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> properties set the colors of the link.</span></span> <span data-ttu-id="45b62-109"><xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件會決定當選取連結文字時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="45b62-109">The <xref:System.Windows.Forms.LinkLabel.LinkClicked> event determines what happens when the link text is selected.</span></span>  
  
 <span data-ttu-id="45b62-110"><xref:System.Windows.Forms.LinkLabel> 控制項最簡單的用法是使用 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 屬性來顯示單一連結，但您也可以使用 <xref:System.Windows.Forms.LinkLabel.Links%2A> 屬性來顯示多個超連結。</span><span class="sxs-lookup"><span data-stu-id="45b62-110">The simplest use of the <xref:System.Windows.Forms.LinkLabel> control is to display a single link using the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property, but you can also display multiple hyperlinks using the <xref:System.Windows.Forms.LinkLabel.Links%2A> property.</span></span> <span data-ttu-id="45b62-111"><xref:System.Windows.Forms.LinkLabel.Links%2A> 屬性可讓您存取連結的集合。</span><span class="sxs-lookup"><span data-stu-id="45b62-111">The <xref:System.Windows.Forms.LinkLabel.Links%2A> property enables you to access a collection of links.</span></span> <span data-ttu-id="45b62-112">您也可以在每個個別 <xref:System.Windows.Forms.LinkLabel.Link> 物件的 <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> 屬性中指定資料。</span><span class="sxs-lookup"><span data-stu-id="45b62-112">You can also specify data in the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property of each individual <xref:System.Windows.Forms.LinkLabel.Link> object.</span></span> <span data-ttu-id="45b62-113"><xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> 屬性的值可以用來儲存要顯示的檔案位置或網站的位址。</span><span class="sxs-lookup"><span data-stu-id="45b62-113">The value of the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property can be used to store the location of a file to display or the address of a Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b62-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45b62-114">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel>
- [<span data-ttu-id="45b62-115">Label 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="45b62-115">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="45b62-116">操作說明：使用 Windows Forms LinkLabel 控制項連結至物件或網頁</span><span class="sxs-lookup"><span data-stu-id="45b62-116">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="45b62-117">操作說明：變更 Windows Forms LinkLabel 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="45b62-117">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
