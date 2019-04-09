---
title: HOW TO：建立顯示進度的 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 1f457d6e2b0eb73da7a16dc93ea80a14ddb4b2c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202010"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="ed1f4-102">HOW TO：建立顯示進度的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ed1f4-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="ed1f4-103">下列程式碼範例會顯示稱為 `FlashTrackBar` 的自訂控制項，其可用來對使用者顯示應用程式的層級或進度。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="ed1f4-104">它會使用漸層來以視覺方式表示進度。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="ed1f4-105">`FlashTrackBar` 控制項可說明下列概念︰</span><span class="sxs-lookup"><span data-stu-id="ed1f4-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
-   <span data-ttu-id="ed1f4-106">定義自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-106">Defining custom properties.</span></span>  
  
-   <span data-ttu-id="ed1f4-107">定義自訂事件。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-107">Defining custom events.</span></span> <span data-ttu-id="ed1f4-108">(`FlashTrackBar` 會定義 `ValueChanged` 事件。)</span><span class="sxs-lookup"><span data-stu-id="ed1f4-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
-   <span data-ttu-id="ed1f4-109">覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法，以提供繪製控制項的邏輯。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
-   <span data-ttu-id="ed1f4-110">計算區域可用於繪製控制項使用其<xref:System.Windows.Forms.Control.ClientRectangle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> `FlashTrackBar` <span data-ttu-id="ed1f4-111">這會以其`OptimizedInvalidate`方法。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-111">does this in its `OptimizedInvalidate` method.</span></span>  
  
-   <span data-ttu-id="ed1f4-112">在 Windows Forms 設計工具中變更屬性時，請實作該屬性的序列化或持續性。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> `FlashTrackBar` <span data-ttu-id="ed1f4-113">定義`ShouldSerializeStartColor`並`ShouldSerializeEndColor`方法來序列化其`StartColor`和`EndColor`屬性。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-113">defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="ed1f4-114">下表顯示 `FlashTrackBar` 所定義的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="ed1f4-115">屬性</span><span class="sxs-lookup"><span data-stu-id="ed1f4-115">Property</span></span>|<span data-ttu-id="ed1f4-116">描述</span><span class="sxs-lookup"><span data-stu-id="ed1f4-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="ed1f4-117">指出使用者是否可藉由按一下並拖曳快速追蹤列來變更其值。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="ed1f4-118">指定追蹤列的結束色彩。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="ed1f4-119">指定要將有關前景漸層的背景加深的程度。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="ed1f4-120">指定追蹤列的最大值。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="ed1f4-121">指定追蹤列的最小值。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="ed1f4-122">指定漸層的開始色彩。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="ed1f4-123">指出是否要顯示漸層的百分比。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="ed1f4-124">指出是否要顯示漸層的目前值。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="ed1f4-125">表示追蹤列是否應顯示色彩漸層，以顯示目前的值。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="ed1f4-126">指定追蹤列的目前值。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="ed1f4-127">下表顯示 `FlashTrackBar:` 所定義的其他成員：引發事件的屬性變更事件和方法。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="ed1f4-128">成員</span><span class="sxs-lookup"><span data-stu-id="ed1f4-128">Member</span></span>|<span data-ttu-id="ed1f4-129">描述</span><span class="sxs-lookup"><span data-stu-id="ed1f4-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="ed1f4-130">當追蹤列的 `Value` 屬性變更時所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="ed1f4-131">引發 `ValueChanged` 事件的方法。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
>  `FlashTrackBar` <span data-ttu-id="ed1f4-132">會使用<xref:System.EventArgs>事件資料的類別和<xref:System.EventHandler>事件委派。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-132">uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="ed1f4-133">為了處理對應*EventName*事件`FlashTrackBar`覆寫下列方法，它繼承自<xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="ed1f4-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="ed1f4-134">為了處理對應的屬性變更事件，`FlashTrackBar`覆寫下列方法，它繼承自<xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="ed1f4-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="ed1f4-135">範例</span><span class="sxs-lookup"><span data-stu-id="ed1f4-135">Example</span></span>  
 <span data-ttu-id="ed1f4-136">`FlashTrackBar` 控制項會定義兩個 UI 類型編輯器：`FlashTrackBarValueEditor` 和 `FlashTrackBarDarkenByEditor`，兩者均顯示於下列程式碼清單中。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="ed1f4-137">`HostApp` 類別會在 Windows Form 上使用 `FlashTrackBar` 控制項。</span><span class="sxs-lookup"><span data-stu-id="ed1f4-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="ed1f4-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed1f4-138">See also</span></span>

- [<span data-ttu-id="ed1f4-139">擴充設計階段支援</span><span class="sxs-lookup"><span data-stu-id="ed1f4-139">Extending Design-Time Support</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [<span data-ttu-id="ed1f4-140">Windows Form 控制項開發的基本概念</span><span class="sxs-lookup"><span data-stu-id="ed1f4-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
