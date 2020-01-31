---
title: 控制項的協助工具屬性
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: 73d81f5b5f656ed5ef90bdd9b6fe1b3293123f97
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743431"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a><span data-ttu-id="0f113-102">支援可及性方針的 Windows Form 控制項屬性</span><span class="sxs-lookup"><span data-stu-id="0f113-102">Properties on Windows Forms Controls That Support Accessibility Guidelines</span></span>
<span data-ttu-id="0f113-103">Windows Forms 的標準工具箱上的控制項支援許多協助工具方針，包括公開鍵盤焦點及公開螢幕元素。</span><span class="sxs-lookup"><span data-stu-id="0f113-103">Controls on the standard toolbox for Windows Forms support many of the accessibility guidelines, including exposing the keyboard focus and exposing the screen elements.</span></span>  
  
## <a name="planning-ahead-for-accessibility"></a><span data-ttu-id="0f113-104">向前規劃協助工具</span><span class="sxs-lookup"><span data-stu-id="0f113-104">Planning Ahead for Accessibility</span></span>  
 <span data-ttu-id="0f113-105">控制項的屬性可以用來支援其他協助工具方針，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="0f113-105">The controls' properties can be used to support other accessibility guidelines as shown in the following table.</span></span> <span data-ttu-id="0f113-106">此外，您應該使用功能表來提供程式功能的存取權。</span><span class="sxs-lookup"><span data-stu-id="0f113-106">Additionally, you should use menus to provide access to program features.</span></span>  
  
|<span data-ttu-id="0f113-107">控制項屬性</span><span class="sxs-lookup"><span data-stu-id="0f113-107">Control Property</span></span>|<span data-ttu-id="0f113-108">協助工具的考慮</span><span class="sxs-lookup"><span data-stu-id="0f113-108">Considerations for Accessibility</span></span>|  
|----------------------|--------------------------------------|  
|<span data-ttu-id="0f113-109">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="0f113-109">AccessibleDescription</span></span>|<span data-ttu-id="0f113-110">描述會回報給協助工具輔助，例如螢幕讀取器。</span><span class="sxs-lookup"><span data-stu-id="0f113-110">The description is reported to accessibility aids such as screen readers.</span></span> <span data-ttu-id="0f113-111">協助工具是特製化的程式和裝置，可以協助殘障人士更有效地使用電腦。</span><span class="sxs-lookup"><span data-stu-id="0f113-111">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span>|  
|<span data-ttu-id="0f113-112">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="0f113-112">AccessibleName</span></span>|<span data-ttu-id="0f113-113">將報告給協助工具輔助的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f113-113">The name that will be reported to the accessibility aids.</span></span>|  
|<span data-ttu-id="0f113-114">AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="0f113-114">AccessibleRole</span></span>|<span data-ttu-id="0f113-115">描述在使用者介面中使用元素的方式。</span><span class="sxs-lookup"><span data-stu-id="0f113-115">Describes the use of the element in the user interface.</span></span>|  
|<span data-ttu-id="0f113-116">TabIndex</span><span class="sxs-lookup"><span data-stu-id="0f113-116">TabIndex</span></span>|<span data-ttu-id="0f113-117">透過表單建立合理的導覽路徑。</span><span class="sxs-lookup"><span data-stu-id="0f113-117">Creates a sensible navigational path through the form.</span></span> <span data-ttu-id="0f113-118">對於沒有內建標籤的控制項（例如文字方塊）而言，其相關聯的標籤會立即在定位順序中的前面加上，這是很重要的。</span><span class="sxs-lookup"><span data-stu-id="0f113-118">It is important for controls without intrinsic labels, such as text boxes, to have their associated label immediately precede them in the tab order.</span></span>|  
|<span data-ttu-id="0f113-119">文字</span><span class="sxs-lookup"><span data-stu-id="0f113-119">Text</span></span>|<span data-ttu-id="0f113-120">使用 "&" 字元來建立存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="0f113-120">Use the "&" character to create access keys.</span></span> <span data-ttu-id="0f113-121">使用存取金鑰是提供已記載的鍵盤存取功能的一部分。</span><span class="sxs-lookup"><span data-stu-id="0f113-121">Using access keys is part of providing documented keyboard access to features.</span></span>|  
|<span data-ttu-id="0f113-122">字型大小</span><span class="sxs-lookup"><span data-stu-id="0f113-122">Font Size</span></span>|<span data-ttu-id="0f113-123">如果無法調整字型大小，則應該將它設定為10點或更大的值。</span><span class="sxs-lookup"><span data-stu-id="0f113-123">If the font size is not adjustable, then it should be set to 10 points or larger.</span></span> <span data-ttu-id="0f113-124">一旦設定表單的字型大小，此後加入表單的所有控制項都會有相同的大小。</span><span class="sxs-lookup"><span data-stu-id="0f113-124">Once the form's font size is set, all the controls added to the form thereafter will have the same size.</span></span>|  
|<span data-ttu-id="0f113-125">Forecolor</span><span class="sxs-lookup"><span data-stu-id="0f113-125">Forecolor</span></span>|<span data-ttu-id="0f113-126">如果此屬性設為預設值，則會在表單上使用使用者的色彩喜好設定。</span><span class="sxs-lookup"><span data-stu-id="0f113-126">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="0f113-127">Backcolor</span><span class="sxs-lookup"><span data-stu-id="0f113-127">Backcolor</span></span>|<span data-ttu-id="0f113-128">如果此屬性設為預設值，則會在表單上使用使用者的色彩喜好設定。</span><span class="sxs-lookup"><span data-stu-id="0f113-128">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="0f113-129">BackgroundImage</span><span class="sxs-lookup"><span data-stu-id="0f113-129">BackgroundImage</span></span>|<span data-ttu-id="0f113-130">將此屬性保留空白，讓文字更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="0f113-130">Leave this property blank to make text more readable.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f113-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f113-131">See also</span></span>

- [<span data-ttu-id="0f113-132">逐步解說：建立 Windows 架構的協助工具應用程式</span><span class="sxs-lookup"><span data-stu-id="0f113-132">Walkthrough: Creating an Accessible Windows-based Application</span></span>](walkthrough-creating-an-accessible-windows-based-application.md)
