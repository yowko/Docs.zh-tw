---
title: "編碼方式和 Windows Form 全球化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f25f4f7206b68e961f3c09a488af643ad5d0a4fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="encoding-and-windows-forms-globalization"></a><span data-ttu-id="acd29-102">編碼方式和 Windows Form 全球化</span><span class="sxs-lookup"><span data-stu-id="acd29-102">Encoding and Windows Forms Globalization</span></span>
<span data-ttu-id="acd29-103">Windows Forms 應用程式完全支援 Unicode，這表示不論是何種平台、程式或語言，每個字元都會以唯一號碼來表示。</span><span class="sxs-lookup"><span data-stu-id="acd29-103">Windows Forms applications are entirely Unicode-enabled, meaning that each character is represented by a unique number, no matter what the platform, program, or language.</span></span> <span data-ttu-id="acd29-104">如需有關 Unicode 的詳細資訊，請參閱[Unicode 協會網站](http://www.unicode.org)。</span><span class="sxs-lookup"><span data-stu-id="acd29-104">For more information about Unicode, see the [Unicode consortium Web site](http://www.unicode.org).</span></span>  
  
## <a name="benefits-of-unicode"></a><span data-ttu-id="acd29-105">Unicode 的優點</span><span class="sxs-lookup"><span data-stu-id="acd29-105">Benefits of Unicode</span></span>  
 <span data-ttu-id="acd29-106">支援 Unicode 之表單的優點包括能夠使用僅限 Unicode 的字集，例如印度文。</span><span class="sxs-lookup"><span data-stu-id="acd29-106">The benefits of Unicode-enabled forms include the ability to work with scripts that are Unicode-only, such as Hindi.</span></span> <span data-ttu-id="acd29-107">此外，您可以在單一表單上使用多種語言。</span><span class="sxs-lookup"><span data-stu-id="acd29-107">In addition, you can use multiple languages on a single form.</span></span> <span data-ttu-id="acd29-108">在 Unicode 中，所有字元的長度都是兩個位元組，因此不需要特別表示雙位元組字元。</span><span class="sxs-lookup"><span data-stu-id="acd29-108">In Unicode, all characters are two bytes long, so no special effort is needed to represent double-byte characters.</span></span> <span data-ttu-id="acd29-109">您也可以撰寫一組可在所有平台上運作的字碼。</span><span class="sxs-lookup"><span data-stu-id="acd29-109">You can also write a single set of code that will work on all platforms.</span></span> <span data-ttu-id="acd29-110">這與舊版 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 不同，之前您必須為不同平台 (例如 Windows NT 和 [!INCLUDE[win98](../../../../includes/win98-md.md)]) 撰寫字碼。</span><span class="sxs-lookup"><span data-stu-id="acd29-110">This is a change from previous versions of [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], in which you had to write different code for different platforms, such as Windows NT and [!INCLUDE[win98](../../../../includes/win98-md.md)].</span></span>  
  
 <span data-ttu-id="acd29-111">不過，在 [!INCLUDE[win98](../../../../includes/win98-md.md)] 和 Windows Millennium Edition 中，有些控制項並不支援 Unicode。</span><span class="sxs-lookup"><span data-stu-id="acd29-111">However, certain controls do not support Unicode in [!INCLUDE[win98](../../../../includes/win98-md.md)] and Windows Millennium Edition.</span></span> <span data-ttu-id="acd29-112">這些控制項全部都是繼承自通用控制項，並會使用 Windows 字碼頁將資料處理成 [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="acd29-112">These controls, all of which inherit from the common control, will process data with the Windows code pages, as [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)].</span></span> <span data-ttu-id="acd29-113">這些控制項包括：<xref:System.Windows.Forms.TabControl>、<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.DateTimePicker>、<xref:System.Windows.Forms.MonthCalendar>、<xref:System.Windows.Forms.TrackBar>、<xref:System.Windows.Forms.ProgressBar>、<xref:System.Windows.Forms.ImageList>、<xref:System.Windows.Forms.ToolBar> 和 <xref:System.Windows.Forms.StatusBar>。</span><span class="sxs-lookup"><span data-stu-id="acd29-113">These controls are: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, and <xref:System.Windows.Forms.StatusBar>.</span></span> <span data-ttu-id="acd29-114">因此在前述平台上，您無法在這些控制項中顯示 Unicode 資料。</span><span class="sxs-lookup"><span data-stu-id="acd29-114">As a result, you cannot display Unicode data in these controls on the listed platforms.</span></span> <span data-ttu-id="acd29-115">例如，您無法在英文版的 [!INCLUDE[win98](../../../../includes/win98-md.md)] 作業系統上顯示日文字元。</span><span class="sxs-lookup"><span data-stu-id="acd29-115">For example, you cannot display Japanese characters on an English [!INCLUDE[win98](../../../../includes/win98-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="acd29-116">如需 <xref:System.Windows.Forms.ToolBar> 和 <xref:System.Windows.Forms.StatusBar> 控制項的 Unicode 感知替代方式，請使用 <xref:System.Windows.Forms.ToolStrip> 和 <xref:System.Windows.Forms.StatusStrip> 控制項來取代這些舊版控制項。</span><span class="sxs-lookup"><span data-stu-id="acd29-116">For Unicode-aware alternatives to the <xref:System.Windows.Forms.ToolBar> and <xref:System.Windows.Forms.StatusBar> controls, use the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip> controls, which replace these older controls.</span></span> <span data-ttu-id="acd29-117">若要維持應用程式中不同視覺項目的外觀和風格類似，請使用 <xref:System.Windows.Forms.MenuStrip> 控制項來呈現功能表，而不是使用 <xref:System.Windows.Forms.MainMenu>。</span><span class="sxs-lookup"><span data-stu-id="acd29-117">To maintain a similar look and feel between visual elements in your application, use the <xref:System.Windows.Forms.MenuStrip> control for rendering menus instead of <xref:System.Windows.Forms.MainMenu>.</span></span> <span data-ttu-id="acd29-118">如同 <xref:System.Windows.Forms.ToolStrip> 和 <xref:System.Windows.Forms.StatusStrip>，<xref:System.Windows.Forms.MenuStrip> 也可以處理及顯示 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="acd29-118">Like <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> can also process and display Unicode characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd29-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="acd29-119">See Also</span></span>  
 [<span data-ttu-id="acd29-120">全球化 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="acd29-120">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
