---
title: UI 自動化和畫面縮放比例
description: 閱讀 Windows 和消費者介面自動化如何處理螢幕縮放。 DWM 會針對所有應用程式進行預設縮放，消費者介面自動化用戶端應用程式必須考慮這些應用程式。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: cf8069f26b85318994aeeb47d42ad28a3a33834a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262524"
---
# <a name="ui-automation-and-screen-scaling"></a><span data-ttu-id="a807d-104">UI 自動化和畫面縮放比例</span><span class="sxs-lookup"><span data-stu-id="a807d-104">UI Automation and Screen Scaling</span></span>

> [!NOTE]
> <span data-ttu-id="a807d-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="a807d-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a807d-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="a807d-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
<span data-ttu-id="a807d-107">從 Windows Vista 開始，Windows 可讓使用者變更每英寸的點 (DPI) 設定，如此一來，大部分的使用者介面 (UI) 畫面上的元素就會變得更大。</span><span class="sxs-lookup"><span data-stu-id="a807d-107">Starting with Windows Vista, Windows enables users to change the dots per inch (dpi) setting so that most user interface (UI) elements on the screen appear larger.</span></span> <span data-ttu-id="a807d-108">雖然 Windows 已有很長的時間可以使用這項功能，但在舊版中，調整必須由應用程式來執行。</span><span class="sxs-lookup"><span data-stu-id="a807d-108">Although this feature has long been available in Windows, in previous versions the scaling had to be implemented by applications.</span></span> <span data-ttu-id="a807d-109">從 Windows Vista 開始，桌面視窗管理員對所有不會處理自己調整規模的應用程式執行預設調整。</span><span class="sxs-lookup"><span data-stu-id="a807d-109">Starting with Windows Vista, the Desktop Window Manager performs default scaling for all applications that do not handle their own scaling.</span></span> <span data-ttu-id="a807d-110">使用者介面自動化用戶端應用程式必須將這項功能納入考量。</span><span class="sxs-lookup"><span data-stu-id="a807d-110">UI Automation client applications must take this feature into account.</span></span>  
  
<a name="Scaling_in_Windows_Vista"></a>

## <a name="scaling-in-windows-vista"></a><span data-ttu-id="a807d-111">Windows Vista 中的縮放比例</span><span class="sxs-lookup"><span data-stu-id="a807d-111">Scaling in Windows Vista</span></span>  

 <span data-ttu-id="a807d-112">預設的 DPI 設定為96，這表示96圖元佔用一個名義英寸的寬度或高度。</span><span class="sxs-lookup"><span data-stu-id="a807d-112">The default dpi setting is 96, which means that 96 pixels occupy a width or height of one notional inch.</span></span> <span data-ttu-id="a807d-113">「英吋」的確切測量值取決於監視器的大小和實體解析度。</span><span class="sxs-lookup"><span data-stu-id="a807d-113">The exact measure of an "inch" depends on the size and physical resolution of the monitor.</span></span> <span data-ttu-id="a807d-114">例如，在 12 英吋寬、1280 像素水平解析度的監視器上，96 像素的水平線長度約一英吋的 9/10。</span><span class="sxs-lookup"><span data-stu-id="a807d-114">For example, on a monitor 12 inches wide, at a horizontal resolution of 1280 pixels, a horizontal line of 96 pixels extends about 9/10 of an inch.</span></span>  
  
 <span data-ttu-id="a807d-115">變更 DPI 設定與變更螢幕解析度不同。</span><span class="sxs-lookup"><span data-stu-id="a807d-115">Changing the dpi setting is not the same as changing the screen resolution.</span></span> <span data-ttu-id="a807d-116">在 DPI 縮放比例中，螢幕上的實體圖元數目會維持不變。</span><span class="sxs-lookup"><span data-stu-id="a807d-116">With dpi scaling, the number of physical pixels on the screen remains the same.</span></span> <span data-ttu-id="a807d-117">不過，縮放比例會套用至 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="a807d-117">However, scaling is applied to the size and location of [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="a807d-118">針對未明確要求不縮放的桌面和應用程式，桌面視窗管理員 (DWM) 會自動執行縮放。</span><span class="sxs-lookup"><span data-stu-id="a807d-118">This scaling can be performed automatically by the Desktop Window Manager (DWM) for the desktop and for applications that do not explicitly ask not to be scaled.</span></span>  
  
 <span data-ttu-id="a807d-119">實際上，當使用者將縮放比例設定為 120 DPI 時，螢幕上的垂直或水準英寸會變大25%。</span><span class="sxs-lookup"><span data-stu-id="a807d-119">In effect, when the user sets the scale factor to 120 dpi, a vertical or horizontal inch on the screen becomes bigger by 25 percent.</span></span> <span data-ttu-id="a807d-120">所有維度都會因此調整。</span><span class="sxs-lookup"><span data-stu-id="a807d-120">All dimensions are scaled accordingly.</span></span> <span data-ttu-id="a807d-121">來自畫面上方和左邊緣的應用程式視窗位移會增加 25%。</span><span class="sxs-lookup"><span data-stu-id="a807d-121">The offset of an application window from the top and left edges of the screen increases by 25 percent.</span></span> <span data-ttu-id="a807d-122">如果應用程式調整已啟用，且應用程式不是 DPI 感知，則視窗的大小會以相同比例增加，以及其所包含之所有元素的位移和大小 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a807d-122">If application scaling is enabled and the application is not dpi-aware, the size of the window increases in the same proportion, along with the offsets and sizes of all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements it contains.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a807d-123">根據預設，當使用者將 DPI 設定為120時，DWM 不會執行非 DPI 感知應用程式的縮放比例，但當 DPI 設定為自訂值144或更高時，則會執行此工作。</span><span class="sxs-lookup"><span data-stu-id="a807d-123">By default, the DWM does not perform scaling for non-dpi-aware applications when the user sets the dpi to 120, but does perform it when the dpi is set to a custom value of 144 or higher.</span></span> <span data-ttu-id="a807d-124">不過，使用者可以覆寫此預設行為。</span><span class="sxs-lookup"><span data-stu-id="a807d-124">However, the user can override the default behavior.</span></span>  
  
 <span data-ttu-id="a807d-125">針對重視畫面座標的應用程式，畫面縮放比例會產生新挑戰。</span><span class="sxs-lookup"><span data-stu-id="a807d-125">Screen scaling creates new challenges for applications that are concerned in any way with screen coordinates.</span></span> <span data-ttu-id="a807d-126">畫面現在包含兩個座標系統：實體和邏輯。</span><span class="sxs-lookup"><span data-stu-id="a807d-126">The screen now contains two coordinate systems: physical and logical.</span></span> <span data-ttu-id="a807d-127">點的實體座標是來自原點左上方的實際位移 (以像素為單位)。</span><span class="sxs-lookup"><span data-stu-id="a807d-127">The physical coordinates of a point are the actual offset in pixels from the top left of the origin.</span></span> <span data-ttu-id="a807d-128">邏輯座標則是像素本身縮放時，跟著縮放的位移。</span><span class="sxs-lookup"><span data-stu-id="a807d-128">The logical coordinates are the offsets as they would be if the pixels themselves were scaled.</span></span>  
  
 <span data-ttu-id="a807d-129">假設您設計的對話方塊在座標 (100, 48) 上有一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="a807d-129">Suppose you design a dialog box with a button at coordinates (100, 48).</span></span> <span data-ttu-id="a807d-130">當此對話方塊顯示為預設 96 DPI 時，此按鈕會位於 (100，48) 的實體座標。</span><span class="sxs-lookup"><span data-stu-id="a807d-130">When this dialog box is displayed at the default 96 dpi, the button is located at physical coordinates of (100, 48).</span></span> <span data-ttu-id="a807d-131">以 120 DPI 為單位，位於 (125，60) 的實體座標。</span><span class="sxs-lookup"><span data-stu-id="a807d-131">At 120 dpi, it is located at physical coordinates of (125, 60).</span></span> <span data-ttu-id="a807d-132">但是在任何 DPI 設定中，邏輯座標都相同： (100、48) 。</span><span class="sxs-lookup"><span data-stu-id="a807d-132">But the logical coordinates are the same at any dpi setting: (100, 48).</span></span>  
  
 <span data-ttu-id="a807d-133">邏輯座標很重要，因為它們會讓作業系統和應用程式的行為保持一致，而不論 DPI 設定為何。</span><span class="sxs-lookup"><span data-stu-id="a807d-133">Logical coordinates are important, because they make the behavior of the operating system and applications consistent regardless of the dpi setting.</span></span> <span data-ttu-id="a807d-134">例如， <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> 一般會傳回邏輯座標。</span><span class="sxs-lookup"><span data-stu-id="a807d-134">For example, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normally returns the logical coordinates.</span></span> <span data-ttu-id="a807d-135">如果您將游標移到對話方塊中的專案上方，則會傳回相同的座標，不論 DPI 設定為何。</span><span class="sxs-lookup"><span data-stu-id="a807d-135">If you move the cursor over an element in a dialog box, the same coordinates are returned regardless of the dpi setting.</span></span> <span data-ttu-id="a807d-136">如果您在 (100、100) 繪製控制項，則會將它繪製至這些邏輯座標，而且會佔用與任何 DPI 設定相同的相對位置。</span><span class="sxs-lookup"><span data-stu-id="a807d-136">If you draw a control at (100, 100), it is drawn to those logical coordinates, and will occupy the same relative position at any dpi setting.</span></span>  
  
<a name="Scaling_in_UI_Automation_Clients"></a>

## <a name="scaling-in-ui-automation-clients"></a><span data-ttu-id="a807d-137">使用者介面自動化用戶端中的縮放比例</span><span class="sxs-lookup"><span data-stu-id="a807d-137">Scaling in UI Automation Clients</span></span>  

 <span data-ttu-id="a807d-138">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]API 不會使用邏輯座標。</span><span class="sxs-lookup"><span data-stu-id="a807d-138">The [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API does not use logical coordinates.</span></span> <span data-ttu-id="a807d-139">下列方法和屬性會傳回實體座標或採用它們做為參數。</span><span class="sxs-lookup"><span data-stu-id="a807d-139">The following methods and properties either return physical coordinates or take them as parameters.</span></span>  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 <span data-ttu-id="a807d-140">根據預設，在非 96 DPI 環境中執行的消費者介面自動化用戶端應用程式將無法從這些方法和屬性取得正確的結果。</span><span class="sxs-lookup"><span data-stu-id="a807d-140">By default, a UI Automation client application running in a non-96- dpi environment will not be able to obtain correct results from these methods and properties.</span></span> <span data-ttu-id="a807d-141">例如，因為游標位置是在邏輯座標中，用戶端無法單純地將這些座標傳遞至 <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> ，以取得游標下的項目。</span><span class="sxs-lookup"><span data-stu-id="a807d-141">For example, because the cursor position is in logical coordinates, the client cannot simply pass these coordinates to <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> to obtain the element that is under the cursor.</span></span> <span data-ttu-id="a807d-142">此外，應用程式也將無法在其用戶端區域之外正確放置視窗。</span><span class="sxs-lookup"><span data-stu-id="a807d-142">In addition, the application will not be able to correctly place windows outside its client area.</span></span>  
  
 <span data-ttu-id="a807d-143">解決方法分為兩個部分。</span><span class="sxs-lookup"><span data-stu-id="a807d-143">The solution is in two parts.</span></span>  
  
1. <span data-ttu-id="a807d-144">首先，將用戶端應用程式設為 DPI 感知。</span><span class="sxs-lookup"><span data-stu-id="a807d-144">First, make the client application dpi-aware.</span></span> <span data-ttu-id="a807d-145">若要這樣做，請 `SetProcessDPIAware` 在啟動時呼叫 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="a807d-145">To do this, call the Win32 function `SetProcessDPIAware` at startup.</span></span> <span data-ttu-id="a807d-146">以 Managed 程式碼的下列宣告，讓這個函式成為可用的。</span><span class="sxs-lookup"><span data-stu-id="a807d-146">In managed code, the following declaration makes this function available.</span></span>  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     <span data-ttu-id="a807d-147">這個函式會讓整個進程具有 DPI 感知，這表示所有屬於進程的視窗都是無比例的。</span><span class="sxs-lookup"><span data-stu-id="a807d-147">This function makes the entire process dpi-aware, meaning that all windows that belong to the process are unscaled.</span></span> <span data-ttu-id="a807d-148">例如，在 [螢光筆範例](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)中，構成反白顯示矩形的四個視窗位於從消費者介面自動化取得的實體座標，而非邏輯座標。</span><span class="sxs-lookup"><span data-stu-id="a807d-148">In the [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), for instance, the four windows that make up the highlight rectangle are located at the physical coordinates obtained from UI Automation, not the logical coordinates.</span></span> <span data-ttu-id="a807d-149">如果範例不是 DPI 感知，就會在桌面的邏輯座標上繪製反白顯示，這會導致非 96 DPI 環境中的放置不正確。</span><span class="sxs-lookup"><span data-stu-id="a807d-149">If the sample were not dpi-aware, the highlight would be drawn at the logical coordinates on the desktop, which would result in incorrect placement in a non-96- dpi environment.</span></span>  
  
2. <span data-ttu-id="a807d-150">若要取得資料指標座標，請呼叫 Win32 函數 `GetPhysicalCursorPos` 。</span><span class="sxs-lookup"><span data-stu-id="a807d-150">To get cursor coordinates, call the Win32 function `GetPhysicalCursorPos`.</span></span> <span data-ttu-id="a807d-151">下列範例顯示如何宣告及使用這個函式。</span><span class="sxs-lookup"><span data-stu-id="a807d-151">The following example shows how to declare and use this function.</span></span>  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> <span data-ttu-id="a807d-152">請勿使用 <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a807d-152">Do not use <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a807d-153">這個屬性在縮放環境中用戶端視窗之外的行為是未定義的。</span><span class="sxs-lookup"><span data-stu-id="a807d-153">The behavior of this property outside client windows in a scaled environment is undefined.</span></span>  
  
 <span data-ttu-id="a807d-154">如果您的應用程式執行與非 DPI 感知應用程式的直接跨進程通訊，您可能會使用 Win32 函數和來轉換邏輯和實體座標 `PhysicalToLogicalPoint` `LogicalToPhysicalPoint` 。</span><span class="sxs-lookup"><span data-stu-id="a807d-154">If your application performs direct cross-process communication with non- dpi-aware applications, you may have convert between logical and physical coordinates by using the Win32 functions `PhysicalToLogicalPoint` and `LogicalToPhysicalPoint`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a807d-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a807d-155">See also</span></span>

- [<span data-ttu-id="a807d-156">Highlighter Sample</span><span class="sxs-lookup"><span data-stu-id="a807d-156">Highlighter Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
