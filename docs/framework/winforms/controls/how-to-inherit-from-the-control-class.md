---
title: 作法：繼承控制項類別
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02c40e310778bd476742f62ee8b9d8598b084a53
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015846"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="ef8f2-102">作法：繼承控制項類別</span><span class="sxs-lookup"><span data-stu-id="ef8f2-102">How to: Inherit from the Control Class</span></span>

<span data-ttu-id="ef8f2-103">如果您想要建立完全自訂的控制項以在 Windows Form 上使用, 您應該繼承<xref:System.Windows.Forms.Control>自類別。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="ef8f2-104">從<xref:System.Windows.Forms.Control>類別繼承時, 需要您執行更多規劃和實作為, 同時也會提供您最大範圍的選項。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="ef8f2-105">當繼承自<xref:System.Windows.Forms.Control>時, 您會繼承可讓控制項運作的非常基本功能。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="ef8f2-106"><xref:System.Windows.Forms.Control>類別中固有的功能會透過鍵盤和滑鼠來處理使用者輸入、定義控制項的界限和大小、提供 windows 控制碼, 以及提供訊息處理和安全性。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="ef8f2-107">它不會併入任何繪製功能 (在此例中是控制項圖形化介面的實際轉譯)，也不會併入任何特定的使用者互動功能。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="ef8f2-108">您必須透過自訂程式碼來提供上述一切。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-108">You must provide all of these aspects through custom code.</span></span>

## <a name="to-create-a-custom-control"></a><span data-ttu-id="ef8f2-109">建立自訂控制項</span><span class="sxs-lookup"><span data-stu-id="ef8f2-109">To create a custom control</span></span>

1. <span data-ttu-id="ef8f2-110">在 Visual Studio 中, 建立新的**Windows 應用程式**或**Windows 控制項程式庫**專案。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-110">In Visual Studio, create a new **Windows Application** or **Windows Control Library** project.</span></span>

2. <span data-ttu-id="ef8f2-111">從 [專案] 功能表中，選擇 [新增類別]。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-111">From the **Project** menu, choose **Add Class**.</span></span>

3. <span data-ttu-id="ef8f2-112">在 [新增項目] 對話方塊中，按一下 [自訂控制項]。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-112">In the **Add New Item** dialog box, click **Custom Control**.</span></span>

   <span data-ttu-id="ef8f2-113">新的自訂控制項會新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="ef8f2-114">按**F7**以開啟自訂控制項的程式**代碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-114">Press **F7** to open the **Code Editor** for your custom control.</span></span>

5. <span data-ttu-id="ef8f2-115">找出<xref:System.Windows.Forms.Control.OnPaint%2A>方法, 這會是空的, 但不包括呼叫<xref:System.Windows.Forms.Control.OnPaint%2A>基類的方法。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-115">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>

6. <span data-ttu-id="ef8f2-116">修改程式碼，以併入您要用於控制項的任何自訂繪製功能。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-116">Modify the code to incorporate any custom painting you want for your control.</span></span>

   <span data-ttu-id="ef8f2-117">如需撰寫程式碼來轉譯控制項圖形的相關資訊，請參閱[自訂控制項繪製和轉譯](custom-control-painting-and-rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-117">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

7. <span data-ttu-id="ef8f2-118">實作您的控制項將併入的任何自訂方法、屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-118">Implement any custom methods, properties, or events that your control will incorporate.</span></span>

8. <span data-ttu-id="ef8f2-119">儲存並測試您的控制項。</span><span class="sxs-lookup"><span data-stu-id="ef8f2-119">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef8f2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef8f2-120">See also</span></span>

- [<span data-ttu-id="ef8f2-121">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="ef8f2-121">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="ef8f2-122">如何：繼承自 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="ef8f2-122">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="ef8f2-123">如何：繼承自現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ef8f2-123">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="ef8f2-124">如何：Windows Forms 的作者控制項</span><span class="sxs-lookup"><span data-stu-id="ef8f2-124">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="ef8f2-125">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="ef8f2-125">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="ef8f2-126">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ef8f2-126">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
