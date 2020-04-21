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
ms.openlocfilehash: 3e8607644c858ae804e384c974b5e81c1786c6a1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739514"
---
# <a name="linklabel-control-overview-windows-forms"></a><span data-ttu-id="e1c26-102">LinkLabel 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="e1c26-102">LinkLabel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="e1c26-103">Windows 表<xref:System.Windows.Forms.LinkLabel>單元件允許您向 Windows 窗體應用程式添加 Web 樣式的連結。</span><span class="sxs-lookup"><span data-stu-id="e1c26-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to add Web-style links to Windows Forms applications.</span></span> <span data-ttu-id="e1c26-104">您可以將控制項<xref:System.Windows.Forms.LinkLabel>用於可<xref:System.Windows.Forms.Label>用於控制件的所有內容;還可以將文本的一部分設置為指向檔、資料夾或網頁的連結。</span><span class="sxs-lookup"><span data-stu-id="e1c26-104">You can use the <xref:System.Windows.Forms.LinkLabel> control for everything that you can use the <xref:System.Windows.Forms.Label> control for; you can also set part of the text as a link to a file, folder, or Web page.</span></span>  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a><span data-ttu-id="e1c26-105">使用連結標籤控制項可以做什麼</span><span class="sxs-lookup"><span data-stu-id="e1c26-105">What You Can Do with the LinkLabel Control</span></span>  
 <span data-ttu-id="e1c26-106">除了<xref:System.Windows.Forms.Label>控制式所有屬性、方法和事件外,<xref:System.Windows.Forms.LinkLabel>控制項還具有超連結和連結顏色的屬性。</span><span class="sxs-lookup"><span data-stu-id="e1c26-106">In addition to all the properties, methods, and events of the <xref:System.Windows.Forms.Label> control, the <xref:System.Windows.Forms.LinkLabel> control has properties for hyperlinks and link colors.</span></span> <span data-ttu-id="e1c26-107">屬性<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>設置啟動連結的文本區域。</span><span class="sxs-lookup"><span data-stu-id="e1c26-107">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property sets the area of the text that activates the link.</span></span> <span data-ttu-id="e1c26-108"><xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>和<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>屬性設置<xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A>連結的顏色。</span><span class="sxs-lookup"><span data-stu-id="e1c26-108">The <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> properties set the colors of the link.</span></span> <span data-ttu-id="e1c26-109">該<xref:System.Windows.Forms.LinkLabel.LinkClicked>事件確定選擇連結文本時會發生什麼情況。</span><span class="sxs-lookup"><span data-stu-id="e1c26-109">The <xref:System.Windows.Forms.LinkLabel.LinkClicked> event determines what happens when the link text is selected.</span></span>  
  
 <span data-ttu-id="e1c26-110">控制項最簡單的用處<xref:System.Windows.Forms.LinkLabel>是使用<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>屬性 顯示單個連結,但<xref:System.Windows.Forms.LinkLabel.Links%2A>也可以使用 屬性 顯示多個超連結。</span><span class="sxs-lookup"><span data-stu-id="e1c26-110">The simplest use of the <xref:System.Windows.Forms.LinkLabel> control is to display a single link using the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property, but you can also display multiple hyperlinks using the <xref:System.Windows.Forms.LinkLabel.Links%2A> property.</span></span> <span data-ttu-id="e1c26-111">該<xref:System.Windows.Forms.LinkLabel.Links%2A>屬性使您能夠訪問連結的集合。</span><span class="sxs-lookup"><span data-stu-id="e1c26-111">The <xref:System.Windows.Forms.LinkLabel.Links%2A> property enables you to access a collection of links.</span></span> <span data-ttu-id="e1c26-112">您還可以在每個單個<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A><xref:System.Windows.Forms.LinkLabel.Link>物件的屬性中指定數據。</span><span class="sxs-lookup"><span data-stu-id="e1c26-112">You can also specify data in the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property of each individual <xref:System.Windows.Forms.LinkLabel.Link> object.</span></span> <span data-ttu-id="e1c26-113"><xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>屬性的值可用於存儲要顯示的檔案的位置或網站的位址。</span><span class="sxs-lookup"><span data-stu-id="e1c26-113">The value of the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property can be used to store the location of a file to display or the address of a Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c26-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1c26-114">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel>
- [<span data-ttu-id="e1c26-115">Label 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e1c26-115">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="e1c26-116">操作說明：使用 Windows Forms LinkLabel 控制項連結至物件或網頁</span><span class="sxs-lookup"><span data-stu-id="e1c26-116">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [<span data-ttu-id="e1c26-117">操作說明：變更 Windows Forms LinkLabel 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="e1c26-117">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
