---
title: "Windows Form 中的滑鼠指標"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fb0e193ccbced719f30ede91cb59cd51dd349a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mouse-pointers-in-windows-forms"></a><span data-ttu-id="a0584-102">Windows Form 中的滑鼠指標</span><span class="sxs-lookup"><span data-stu-id="a0584-102">Mouse Pointers in Windows Forms</span></span>
<span data-ttu-id="a0584-103">滑鼠*指標*，這有時也稱為資料指標，是指定婧鎏鶗懘為使用者輸入，使用滑鼠在螢幕的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="a0584-103">The mouse *pointer*, which is sometimes referred to as the cursor, is a bitmap that specifies a focus point on the screen for user input with the mouse.</span></span> <span data-ttu-id="a0584-104">本主題提供滑鼠指標在 Windows Form 中的概觀，並描述的數種方式來修改和控制滑鼠指標。</span><span class="sxs-lookup"><span data-stu-id="a0584-104">This topic provides an overview of the mouse pointer in Windows Forms and describes some of the ways to modify and control the mouse pointer.</span></span>  
  
## <a name="accessing-the-mouse-pointer"></a><span data-ttu-id="a0584-105">存取滑鼠指標</span><span class="sxs-lookup"><span data-stu-id="a0584-105">Accessing the Mouse Pointer</span></span>  
 <span data-ttu-id="a0584-106">將滑鼠指標由<xref:System.Windows.Forms.Cursor>類別，而每個<xref:System.Windows.Forms.Control>具有<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>屬性，指定該控制項的指標。</span><span class="sxs-lookup"><span data-stu-id="a0584-106">The mouse pointer is represented by the <xref:System.Windows.Forms.Cursor> class, and each <xref:System.Windows.Forms.Control> has a <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> property that specifies the pointer for that control.</span></span> <span data-ttu-id="a0584-107"><xref:System.Windows.Forms.Cursor>類別包含屬性，例如描述指標<xref:System.Windows.Forms.Cursor.Position%2A>和<xref:System.Windows.Forms.Cursor.HotSpot%2A>屬性和方法，例如修改指標的外觀<xref:System.Windows.Forms.Cursor.Show%2A>， <xref:System.Windows.Forms.Cursor.Hide%2A>，和<xref:System.Windows.Forms.Cursor.DrawStretched%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a0584-107">The <xref:System.Windows.Forms.Cursor> class contains properties that describe the pointer, such as the <xref:System.Windows.Forms.Cursor.Position%2A> and <xref:System.Windows.Forms.Cursor.HotSpot%2A> properties, and methods that can modify the appearance of the pointer, such as the <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, and <xref:System.Windows.Forms.Cursor.DrawStretched%2A> methods.</span></span>  
  
## <a name="controlling-the-mouse-pointer"></a><span data-ttu-id="a0584-108">控制滑鼠指標</span><span class="sxs-lookup"><span data-stu-id="a0584-108">Controlling the Mouse Pointer</span></span>  
 <span data-ttu-id="a0584-109">有時您可能想要限制在滑鼠指標可用或變更滑鼠位置的區域。</span><span class="sxs-lookup"><span data-stu-id="a0584-109">Sometimes you may want to limit the area in which the mouse pointer can be used or change the position the mouse.</span></span> <span data-ttu-id="a0584-110">您可以取得或設定目前的位置，使用滑鼠<xref:System.Windows.Forms.Cursor.Position%2A>屬性<xref:System.Windows.Forms.Cursor>。</span><span class="sxs-lookup"><span data-stu-id="a0584-110">You can get or set the current location of the mouse using the <xref:System.Windows.Forms.Cursor.Position%2A> property of the <xref:System.Windows.Forms.Cursor>.</span></span> <span data-ttu-id="a0584-111">此外，您可以限制可以使用滑鼠指標的區域是設定<xref:System.Windows.Forms.Cursor.Clip%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a0584-111">In addition, you can limit the area the mouse pointer can be used be setting the <xref:System.Windows.Forms.Cursor.Clip%2A> property.</span></span> <span data-ttu-id="a0584-112">裁剪區域中的，依預設，會是整個螢幕。</span><span class="sxs-lookup"><span data-stu-id="a0584-112">The clip area, by default, is the entire screen.</span></span>  
  
## <a name="changing-the-mouse-pointer"></a><span data-ttu-id="a0584-113">變更滑鼠指標</span><span class="sxs-lookup"><span data-stu-id="a0584-113">Changing the Mouse Pointer</span></span>  
 <span data-ttu-id="a0584-114">變更滑鼠指標是一個重要方法的意見反應提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="a0584-114">Changing the mouse pointer is an important way of providing feedback to the user.</span></span> <span data-ttu-id="a0584-115">例如，可以修改滑鼠指標的處理常式中<xref:System.Windows.Forms.Control.MouseEnter>和<xref:System.Windows.Forms.Control.MouseLeave>事件發生的計算，告訴使用者，並限制使用者在控制項中的互動。</span><span class="sxs-lookup"><span data-stu-id="a0584-115">For example, the mouse pointer can be modified in the handlers of the <xref:System.Windows.Forms.Control.MouseEnter> and <xref:System.Windows.Forms.Control.MouseLeave> events to tell the user that computations are occurring and to limit user interaction in the control.</span></span> <span data-ttu-id="a0584-116">有時候，滑鼠指標會變更，因為系統事件，例如，當您的應用程式參與拖放作業。</span><span class="sxs-lookup"><span data-stu-id="a0584-116">Sometimes, the mouse pointer will change because of system events, such as when your application is involved in a drag-and-drop operation.</span></span>  
  
 <span data-ttu-id="a0584-117">若要變更滑鼠指標的主要方式是藉由設定<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.Control.DefaultCursor%2A>至新的控制項屬性<xref:System.Windows.Forms.Cursor>。</span><span class="sxs-lookup"><span data-stu-id="a0584-117">The primary way to change the mouse pointer is by setting the <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.Control.DefaultCursor%2A> property of a control to a new <xref:System.Windows.Forms.Cursor>.</span></span> <span data-ttu-id="a0584-118">範例變更滑鼠指標，請參閱中的程式碼範例<xref:System.Windows.Forms.Cursor>類別。</span><span class="sxs-lookup"><span data-stu-id="a0584-118">For examples of changing the mouse pointer, see the code example in the <xref:System.Windows.Forms.Cursor> class.</span></span> <span data-ttu-id="a0584-119">此外，<xref:System.Windows.Forms.Cursors>類別會公開一組<xref:System.Windows.Forms.Cursor>許多不同類型的指標，例如類似手形指標的物件。</span><span class="sxs-lookup"><span data-stu-id="a0584-119">In addition, the <xref:System.Windows.Forms.Cursors> class exposes a set of <xref:System.Windows.Forms.Cursor> objects for many different types of pointers, such as a pointer that resembles a hand.</span></span> <span data-ttu-id="a0584-120">若要顯示等待指標，這類似於以沙漏來表示，，每當滑鼠指標位於控制項上時，使用<xref:System.Windows.Forms.Control.UseWaitCursor%2A>屬性<xref:System.Windows.Forms.Control>類別。</span><span class="sxs-lookup"><span data-stu-id="a0584-120">To display the wait pointer, which resembles an hourglass, whenever the mouse pointer is on the control, use the <xref:System.Windows.Forms.Control.UseWaitCursor%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0584-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0584-121">See Also</span></span>  
 <xref:System.Windows.Forms.Cursor>  
 [<span data-ttu-id="a0584-122">Windows Forms 應用程式中的滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="a0584-122">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="a0584-123">Windows Forms 中的拖放功能</span><span class="sxs-lookup"><span data-stu-id="a0584-123">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
