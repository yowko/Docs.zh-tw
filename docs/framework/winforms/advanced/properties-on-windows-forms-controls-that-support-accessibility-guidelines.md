---
title: 支援可及性方針的 Windows Form 控制項屬性
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: b466dcf42561d8ced7b224215538a807c94b174b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524484"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a><span data-ttu-id="5373f-102">支援可及性方針的 Windows Form 控制項屬性</span><span class="sxs-lookup"><span data-stu-id="5373f-102">Properties on Windows Forms Controls That Support Accessibility Guidelines</span></span>
<span data-ttu-id="5373f-103">控制項 Windows Form 的標準工具箱支援許多協助工具的指導方針，包括鍵盤焦點，而且已公開螢幕項目。</span><span class="sxs-lookup"><span data-stu-id="5373f-103">Controls on the standard toolbox for Windows Forms support many of the accessibility guidelines, including exposing the keyboard focus and exposing the screen elements.</span></span>  
  
## <a name="planning-ahead-for-accessibility"></a><span data-ttu-id="5373f-104">事先規劃協助工具</span><span class="sxs-lookup"><span data-stu-id="5373f-104">Planning Ahead for Accessibility</span></span>  
 <span data-ttu-id="5373f-105">控制項的屬性可以用來支援其他協助工具的指導方針下, 表所示。</span><span class="sxs-lookup"><span data-stu-id="5373f-105">The controls' properties can be used to support other accessibility guidelines as shown in the following table.</span></span> <span data-ttu-id="5373f-106">此外，您應該使用功能表來提供存取權的程式功能。</span><span class="sxs-lookup"><span data-stu-id="5373f-106">Additionally, you should use menus to provide access to program features.</span></span>  
  
|<span data-ttu-id="5373f-107">控制項屬性</span><span class="sxs-lookup"><span data-stu-id="5373f-107">Control Property</span></span>|<span data-ttu-id="5373f-108">協助工具的考量</span><span class="sxs-lookup"><span data-stu-id="5373f-108">Considerations for Accessibility</span></span>|  
|----------------------|--------------------------------------|  
|<span data-ttu-id="5373f-109">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="5373f-109">AccessibleDescription</span></span>|<span data-ttu-id="5373f-110">描述被報告給協助工具，例如螢幕助讀程式。</span><span class="sxs-lookup"><span data-stu-id="5373f-110">The description is reported to accessibility aids such as screen readers.</span></span> <span data-ttu-id="5373f-111">協助工具是特製化的程式和裝置，可以協助殘障人士更有效地使用電腦。</span><span class="sxs-lookup"><span data-stu-id="5373f-111">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span>|  
|<span data-ttu-id="5373f-112">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="5373f-112">AccessibleName</span></span>|<span data-ttu-id="5373f-113">將報告給協助工具的名稱。</span><span class="sxs-lookup"><span data-stu-id="5373f-113">The name that will be reported to the accessibility aids.</span></span>|  
|<span data-ttu-id="5373f-114">AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="5373f-114">AccessibleRole</span></span>|<span data-ttu-id="5373f-115">描述使用在使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="5373f-115">Describes the use of the element in the user interface.</span></span>|  
|<span data-ttu-id="5373f-116">TabIndex</span><span class="sxs-lookup"><span data-stu-id="5373f-116">TabIndex</span></span>|<span data-ttu-id="5373f-117">建立表單直覺式導覽路徑。</span><span class="sxs-lookup"><span data-stu-id="5373f-117">Creates a sensible navigational path through the form.</span></span> <span data-ttu-id="5373f-118">請務必沒有內建函式標記，例如文字方塊中，將其關聯的標籤它們定位順序中之前的控制項。</span><span class="sxs-lookup"><span data-stu-id="5373f-118">It is important for controls without intrinsic labels, such as text boxes, to have their associated label immediately precede them in the tab order.</span></span>|  
|<span data-ttu-id="5373f-119">Text</span><span class="sxs-lookup"><span data-stu-id="5373f-119">Text</span></span>|<span data-ttu-id="5373f-120">您可以使用"&"字元來建立便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="5373f-120">Use the "&" character to create access keys.</span></span> <span data-ttu-id="5373f-121">使用存取金鑰是提供記載的鍵盤存取功能的一部分。</span><span class="sxs-lookup"><span data-stu-id="5373f-121">Using access keys is part of providing documented keyboard access to features.</span></span>|  
|<span data-ttu-id="5373f-122">字型大小</span><span class="sxs-lookup"><span data-stu-id="5373f-122">Font Size</span></span>|<span data-ttu-id="5373f-123">如果字型不是可調整的則它應該設為 10 或更大。</span><span class="sxs-lookup"><span data-stu-id="5373f-123">If the font size is not adjustable, then it should be set to 10 points or larger.</span></span> <span data-ttu-id="5373f-124">一旦設定表單的字型大小，之後加入至表單的所有控制項將會都有相同的大小。</span><span class="sxs-lookup"><span data-stu-id="5373f-124">Once the form's font size is set, all the controls added to the form thereafter will have the same size.</span></span>|  
|<span data-ttu-id="5373f-125">Forecolor</span><span class="sxs-lookup"><span data-stu-id="5373f-125">Forecolor</span></span>|<span data-ttu-id="5373f-126">如果這個屬性設定為預設值，然後將會在表單上使用使用者的色彩設定。</span><span class="sxs-lookup"><span data-stu-id="5373f-126">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="5373f-127">Backcolor</span><span class="sxs-lookup"><span data-stu-id="5373f-127">Backcolor</span></span>|<span data-ttu-id="5373f-128">如果這個屬性設定為預設值，然後將會在表單上使用使用者的色彩設定。</span><span class="sxs-lookup"><span data-stu-id="5373f-128">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="5373f-129">BackgroundImage</span><span class="sxs-lookup"><span data-stu-id="5373f-129">BackgroundImage</span></span>|<span data-ttu-id="5373f-130">將此屬性保留空白，讓文字更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="5373f-130">Leave this property blank to make text more readable.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5373f-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5373f-131">See Also</span></span>  
 [<span data-ttu-id="5373f-132">逐步解說：建立 Windows 架構的協助工具應用程式</span><span class="sxs-lookup"><span data-stu-id="5373f-132">Walkthrough: Creating an Accessible Windows-based Application</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
