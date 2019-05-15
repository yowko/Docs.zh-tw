---
title: 作法：區分按一下和按兩下
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
ms.openlocfilehash: cff6c283651b5994e869756524a3ee83ecdcfda9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592068"
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a><span data-ttu-id="6af7b-102">HOW TO：區分按一下和按兩下</span><span class="sxs-lookup"><span data-stu-id="6af7b-102">How to: Distinguish Between Clicks and Double-Clicks</span></span>
<span data-ttu-id="6af7b-103">一般而言，單一「按一下」(click) 會啟始使用者介面 (UI) 動作，而「按兩下」(double-click) 會擴充此動作。</span><span class="sxs-lookup"><span data-stu-id="6af7b-103">Typically, a single *click* initiates a user interface (UI) action and a *double-click* extends the action.</span></span> <span data-ttu-id="6af7b-104">例如，按一下通常會選取項目，而按兩下可編輯選取的項目。</span><span class="sxs-lookup"><span data-stu-id="6af7b-104">For example, one click usually selects an item, and a double-click edits the selected item.</span></span> <span data-ttu-id="6af7b-105">不過，Windows Form Click 事件並不輕易滿足按一下和按兩下會執行不相容動作的案例，因為會先執行與 <xref:System.Windows.Forms.Control.Click> 或 <xref:System.Windows.Forms.Control.MouseClick> 事件相關的動作，之後此動作才會與 <xref:System.Windows.Forms.Control.DoubleClick> 或 <xref:System.Windows.Forms.Control.MouseDoubleClick> 事件相關。</span><span class="sxs-lookup"><span data-stu-id="6af7b-105">However, the Windows Forms click events do not easily accommodate a scenario where a click and a double-click perform incompatible actions, because an action tied to the <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> event is performed before the action tied to the <xref:System.Windows.Forms.Control.DoubleClick> or <xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span> <span data-ttu-id="6af7b-106">本主題會示範兩種解決這個問題的方案。</span><span class="sxs-lookup"><span data-stu-id="6af7b-106">This topic demonstrates two solutions to this problem.</span></span> <span data-ttu-id="6af7b-107">一個解決方案是處理按兩下事件，並復原處理 Click 事件的動作。</span><span class="sxs-lookup"><span data-stu-id="6af7b-107">One solution is to handle the double-click event and roll back the actions in the handling of the click event.</span></span> <span data-ttu-id="6af7b-108">在罕見的情況下您可能需要處理 <xref:System.Windows.Forms.Control.MouseDown> 事件並使用 <xref:System.Windows.Forms.SystemInformation> 類別的 <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> 和 <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> 屬性來模擬按一下和按兩下行為。</span><span class="sxs-lookup"><span data-stu-id="6af7b-108">In rare situations you may need to simulate click and double-click behavior by handling the <xref:System.Windows.Forms.Control.MouseDown> event and by using the <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> and <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> properties of the <xref:System.Windows.Forms.SystemInformation> class.</span></span> <span data-ttu-id="6af7b-109">您可測量點擊間隔時間，如果第二個點擊在達到 <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> 的值之前就先發生，且該點擊位於由 <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> 所定義的矩形內，則執行按兩下動作；否則執行按一下動作。</span><span class="sxs-lookup"><span data-stu-id="6af7b-109">You measure the time between clicks and if a second click occurs before the value of <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> is reached and the click is within a rectangle defined by <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, perform the double-click action; otherwise, perform the click action.</span></span>  
  
### <a name="to-roll-back-a-click-action"></a><span data-ttu-id="6af7b-110">復原按一下動作</span><span class="sxs-lookup"><span data-stu-id="6af7b-110">To roll back a click action</span></span>  
  
- <span data-ttu-id="6af7b-111">請確定您正在使用的控制項具有標準的按兩下行為。</span><span class="sxs-lookup"><span data-stu-id="6af7b-111">Ensure that the control you are working with has standard double-click behavior.</span></span> <span data-ttu-id="6af7b-112">如果沒有，請以 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法啟用此控制項。</span><span class="sxs-lookup"><span data-stu-id="6af7b-112">If not, enable the control with the <xref:System.Windows.Forms.Control.SetStyle%2A> method.</span></span> <span data-ttu-id="6af7b-113">處理此按兩下事件，並復原按一下動作，以及復原按兩下動作。</span><span class="sxs-lookup"><span data-stu-id="6af7b-113">Handle the double-click event and roll back the click action as well as the double-click action.</span></span> <span data-ttu-id="6af7b-114">下列程式碼範例示範如何在已啟用按兩下的情況下建立自訂按鈕，以及如何復原按兩下事件處理程式碼中的按一下動作。</span><span class="sxs-lookup"><span data-stu-id="6af7b-114">The following code example demonstrates a how to create a custom button with double-click enabled, as well as how to roll back the click action in the double-click event handling code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a><span data-ttu-id="6af7b-115">區分 MouseDown 事件中的按一下</span><span class="sxs-lookup"><span data-stu-id="6af7b-115">To distinguish between clicks in the MouseDown event</span></span>  
  
- <span data-ttu-id="6af7b-116">請處理 <xref:System.Windows.Forms.Control.MouseDown> 事件，並使用適當的 <xref:System.Windows.Forms.SystemInformation> 屬性和 <xref:System.Windows.Forms.Timer> 元件來決定點擊之間的位置和時間範圍。</span><span class="sxs-lookup"><span data-stu-id="6af7b-116">Handle the <xref:System.Windows.Forms.Control.MouseDown> event and determine the location and time span between clicks using the appropriate <xref:System.Windows.Forms.SystemInformation> properties and a <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="6af7b-117">根據按一下或按兩下進行與否，執行適當的動作。</span><span class="sxs-lookup"><span data-stu-id="6af7b-117">Perform the appropriate action depending on whether a click or double-click takes place.</span></span> <span data-ttu-id="6af7b-118">下列程式碼範例會示範其做法。</span><span class="sxs-lookup"><span data-stu-id="6af7b-118">The following code example demonstrates how this can be done.</span></span>  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6af7b-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6af7b-119">Compiling the Code</span></span>  
 <span data-ttu-id="6af7b-120">這些範例需要：</span><span class="sxs-lookup"><span data-stu-id="6af7b-120">These examples require:</span></span>  
  
- <span data-ttu-id="6af7b-121">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="6af7b-121">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af7b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6af7b-122">See also</span></span>

- [<span data-ttu-id="6af7b-123">Windows Forms 應用程式中的滑鼠輸入</span><span class="sxs-lookup"><span data-stu-id="6af7b-123">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
