---
title: Freezable 物件概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: 05cd3c27430146f575c23011f53995aa07aaf99e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991488"
---
# <a name="freezable-objects-overview"></a><span data-ttu-id="df812-102">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="df812-102">Freezable Objects Overview</span></span>

<span data-ttu-id="df812-103">本主題描述如何有效地使用和建立<xref:System.Windows.Freezable>物件，以提供可協助改善應用程式效能的特殊功能。</span><span class="sxs-lookup"><span data-stu-id="df812-103">This topic describes how to effectively use and create <xref:System.Windows.Freezable> objects, which provide special features that can help improve application performance.</span></span> <span data-ttu-id="df812-104">凍結物件的範例包括筆刷、畫筆、轉換、幾何和動畫。</span><span class="sxs-lookup"><span data-stu-id="df812-104">Examples of freezable objects include brushes, pens, transformations, geometries, and animations.</span></span>

<a name="whatisafreezable"></a>

## <a name="what-is-a-freezable"></a><span data-ttu-id="df812-105">什麼是可凍結的？</span><span class="sxs-lookup"><span data-stu-id="df812-105">What Is a Freezable?</span></span>

<span data-ttu-id="df812-106"><xref:System.Windows.Freezable>是特殊類型的物件, 有兩種狀態: [未凍結] 和 [已凍結]。</span><span class="sxs-lookup"><span data-stu-id="df812-106">A <xref:System.Windows.Freezable> is a special type of object that has two states: unfrozen and frozen.</span></span> <span data-ttu-id="df812-107">當未凍結時<xref:System.Windows.Freezable> ，的行為就像任何其他物件一樣。</span><span class="sxs-lookup"><span data-stu-id="df812-107">When unfrozen, a <xref:System.Windows.Freezable> appears to behave like any other object.</span></span> <span data-ttu-id="df812-108">當凍結時， <xref:System.Windows.Freezable>就無法再修改。</span><span class="sxs-lookup"><span data-stu-id="df812-108">When frozen, a <xref:System.Windows.Freezable> can no longer be modified.</span></span>

<span data-ttu-id="df812-109"><xref:System.Windows.Freezable> 會<xref:System.Windows.Freezable.Changed>提供事件，以通知觀察者對物件的任何修改。</span><span class="sxs-lookup"><span data-stu-id="df812-109">A <xref:System.Windows.Freezable> provides a <xref:System.Windows.Freezable.Changed> event to notify observers of any modifications to the object.</span></span> <span data-ttu-id="df812-110"><xref:System.Windows.Freezable>凍結可以改善其效能，因為它不再需要花費資源來變更通知。</span><span class="sxs-lookup"><span data-stu-id="df812-110">Freezing a <xref:System.Windows.Freezable> can improve its performance, because it no longer needs to spend resources on change notifications.</span></span> <span data-ttu-id="df812-111">凍結<xref:System.Windows.Freezable>也可以線上程之間共用，而無法凍結<xref:System.Windows.Freezable> 。</span><span class="sxs-lookup"><span data-stu-id="df812-111">A frozen <xref:System.Windows.Freezable> can also be shared across threads, while an unfrozen <xref:System.Windows.Freezable> cannot.</span></span>

<span data-ttu-id="df812-112">雖然類別有許多應用程式，但<xref:System.Windows.Freezable>中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的大部分物件都與圖形子系統相關。 <xref:System.Windows.Freezable></span><span class="sxs-lookup"><span data-stu-id="df812-112">Although the <xref:System.Windows.Freezable> class has many applications, most <xref:System.Windows.Freezable> objects in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] are related to the graphics sub-system.</span></span>

<span data-ttu-id="df812-113"><xref:System.Windows.Freezable>類別可讓您更輕鬆地使用特定圖形系統物件，並有助於改善應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="df812-113">The <xref:System.Windows.Freezable> class makes it easier to use certain graphics system objects and can help improve application performance.</span></span> <span data-ttu-id="df812-114">繼承自<xref:System.Windows.Freezable>的類型範例<xref:System.Windows.Media.Brush>包括、 <xref:System.Windows.Media.Transform>和<xref:System.Windows.Media.Geometry>類別。</span><span class="sxs-lookup"><span data-stu-id="df812-114">Examples of types that inherit from <xref:System.Windows.Freezable> include the <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, and <xref:System.Windows.Media.Geometry> classes.</span></span> <span data-ttu-id="df812-115">因為它們包含非受控資源，所以系統必須監視這些物件以進行修改，然後在原始物件變更時，更新其對應的非受控資源。</span><span class="sxs-lookup"><span data-stu-id="df812-115">Because they contain unmanaged resources, the system must monitor these objects for modifications, and then update their corresponding unmanaged resources when there is a change to the original object.</span></span> <span data-ttu-id="df812-116">即使您實際上不修改圖形系統物件，系統仍然必須花一些資源來監視物件，以防您進行變更。</span><span class="sxs-lookup"><span data-stu-id="df812-116">Even if you don't actually modify a graphics system object, the system must still spend some of its resources monitoring the object, in case you do change it.</span></span>

<span data-ttu-id="df812-117">例如，假設您建立<xref:System.Windows.Media.SolidColorBrush>筆刷，並用它來繪製按鈕的背景。</span><span class="sxs-lookup"><span data-stu-id="df812-117">For example, suppose you create a <xref:System.Windows.Media.SolidColorBrush> brush and use it to paint the background of a button.</span></span>

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]

<span data-ttu-id="df812-118">當按鈕呈現時， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]圖形子系統會使用您所提供的資訊來繪製一組圖元，以建立按鈕的外觀。</span><span class="sxs-lookup"><span data-stu-id="df812-118">When the button is rendered, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] graphics sub-system uses the information you provided to paint a group of pixels to create the appearance of a button.</span></span> <span data-ttu-id="df812-119">雖然您使用純色筆刷來描述應該如何繪製按鈕，但是純色筆刷實際上並不會進行繪製。</span><span class="sxs-lookup"><span data-stu-id="df812-119">Although you used a solid color brush to describe how the button should be painted, your solid color brush doesn't actually do the painting.</span></span> <span data-ttu-id="df812-120">圖形系統會針對按鈕和筆刷產生快速、低層級的物件，而這就是實際出現在螢幕上的物件。</span><span class="sxs-lookup"><span data-stu-id="df812-120">The graphics system generates fast, low-level objects for the button and the brush, and it is those objects that actually appear on the screen.</span></span>

<span data-ttu-id="df812-121">如果您要修改筆刷，則必須重新產生那些低層級的物件。</span><span class="sxs-lookup"><span data-stu-id="df812-121">If you were to modify the brush, those low-level objects would have to be regenerated.</span></span> <span data-ttu-id="df812-122">可凍結的類別可讓筆刷能夠尋找其對應產生的低層級物件，並在變更時加以更新。</span><span class="sxs-lookup"><span data-stu-id="df812-122">The freezable class is what gives a brush the ability to find its corresponding generated, low-level objects and to update them when it changes.</span></span> <span data-ttu-id="df812-123">啟用這種功能時，筆刷就稱為「解凍」。</span><span class="sxs-lookup"><span data-stu-id="df812-123">When this ability is enabled, the brush is said to be "unfrozen."</span></span>

<span data-ttu-id="df812-124">可凍結的<xref:System.Windows.Freezable.Freeze%2A>方法可讓您停用此自行更新的功能。</span><span class="sxs-lookup"><span data-stu-id="df812-124">A freezable's <xref:System.Windows.Freezable.Freeze%2A> method enables you to disable this self-updating ability.</span></span> <span data-ttu-id="df812-125">您可以使用這個方法，讓筆刷變成「凍結」或無法修改。</span><span class="sxs-lookup"><span data-stu-id="df812-125">You can use this method to make the brush become "frozen," or unmodifiable.</span></span>

> [!NOTE]
> <span data-ttu-id="df812-126">並非每個可凍結的物件都可以凍結。</span><span class="sxs-lookup"><span data-stu-id="df812-126">Not every Freezable object can be frozen.</span></span> <span data-ttu-id="df812-127">若要避免<xref:System.InvalidOperationException>擲回，請檢查可凍結<xref:System.Windows.Freezable.CanFreeze%2A>物件之屬性的值，以判斷是否可以凍結它，然後再嘗試凍結它。</span><span class="sxs-lookup"><span data-stu-id="df812-127">To avoid throwing an <xref:System.InvalidOperationException>, check the value of the Freezable object's <xref:System.Windows.Freezable.CanFreeze%2A> property to determine whether it can be frozen before attempting to freeze it.</span></span>

[!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
[!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]

<span data-ttu-id="df812-128">當您不再需要修改可凍結的時，凍結它可提供效能優勢。</span><span class="sxs-lookup"><span data-stu-id="df812-128">When you no longer need to modify a freezable, freezing it provides performance benefits.</span></span> <span data-ttu-id="df812-129">如果您在此範例中凍結筆刷，圖形系統就不再需要監視它是否有變更。</span><span class="sxs-lookup"><span data-stu-id="df812-129">If you were to freeze the brush in this example, the graphics system would no longer need to monitor it for changes.</span></span> <span data-ttu-id="df812-130">圖形系統也可以進行其他優化，因為它知道筆刷不會變更。</span><span class="sxs-lookup"><span data-stu-id="df812-130">The graphics system can also make other optimizations, because it knows the brush won't change.</span></span>

> [!NOTE]
> <span data-ttu-id="df812-131">為了方便起見，除非您明確凍結，否則可凍結的物件會保持未凍結。</span><span class="sxs-lookup"><span data-stu-id="df812-131">For convenience, freezable objects remain unfrozen unless you explicitly freeze them.</span></span>

<a name="frozenfreezables"></a>

## <a name="using-freezables"></a><span data-ttu-id="df812-132">使用 Freezable</span><span class="sxs-lookup"><span data-stu-id="df812-132">Using Freezables</span></span>

<span data-ttu-id="df812-133">使用未凍結的可凍結，就像使用任何其他類型的物件。</span><span class="sxs-lookup"><span data-stu-id="df812-133">Using an unfrozen freezable is like using any other type of object.</span></span> <span data-ttu-id="df812-134">在下列範例中，的色彩<xref:System.Windows.Media.SolidColorBrush>在用來繪製按鈕的背景之後，會從黃色變更為紅色。</span><span class="sxs-lookup"><span data-stu-id="df812-134">In the following example, the color of a <xref:System.Windows.Media.SolidColorBrush> is changed from yellow to red after it's used to paint the background of a button.</span></span> <span data-ttu-id="df812-135">圖形系統會在幕後運作，以在下一次重新整理螢幕時，自動將按鈕從黃色變更為紅色。</span><span class="sxs-lookup"><span data-stu-id="df812-135">The graphics system works behind the scenes to automatically change the button from yellow to red the next time the screen is refreshed.</span></span>

[!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
[!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]

### <a name="freezing-a-freezable"></a><span data-ttu-id="df812-136">凍結凍結的</span><span class="sxs-lookup"><span data-stu-id="df812-136">Freezing a Freezable</span></span>

<span data-ttu-id="df812-137">若要使<xref:System.Windows.Freezable>無法修改，請呼叫<xref:System.Windows.Freezable.Freeze%2A>其方法。</span><span class="sxs-lookup"><span data-stu-id="df812-137">To make a <xref:System.Windows.Freezable> unmodifiable, you call its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span> <span data-ttu-id="df812-138">當您凍結包含可凍結物件的物件時，也會凍結那些物件。</span><span class="sxs-lookup"><span data-stu-id="df812-138">When you freeze an object that contains freezable objects, those objects are frozen as well.</span></span> <span data-ttu-id="df812-139">例如，如果您凍結<xref:System.Windows.Media.PathGeometry>，它所包含的圖形和區段也會凍結。</span><span class="sxs-lookup"><span data-stu-id="df812-139">For example, if you freeze a <xref:System.Windows.Media.PathGeometry>, the figures and segments it contains would be frozen too.</span></span>

<span data-ttu-id="df812-140">如果下列任一條件成立，就**無法**凍結可凍結的：</span><span class="sxs-lookup"><span data-stu-id="df812-140">A Freezable **can't** be frozen if any of the following are true:</span></span>

- <span data-ttu-id="df812-141">它具有動畫或資料系結屬性。</span><span class="sxs-lookup"><span data-stu-id="df812-141">It has animated or data bound properties.</span></span>

- <span data-ttu-id="df812-142">它具有動態資源所設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="df812-142">It has properties set by a dynamic resource.</span></span> <span data-ttu-id="df812-143">（如需動態資源的詳細資訊，請參閱[XAML 資源](xaml-resources.md)）。</span><span class="sxs-lookup"><span data-stu-id="df812-143">(See the [XAML Resources](xaml-resources.md) for more information about dynamic resources.)</span></span>

- <span data-ttu-id="df812-144">它包含<xref:System.Windows.Freezable>無法凍結的子物件。</span><span class="sxs-lookup"><span data-stu-id="df812-144">It contains <xref:System.Windows.Freezable> sub-objects that can't be frozen.</span></span>

<span data-ttu-id="df812-145">如果這些條件為 false，而且您不打算修改<xref:System.Windows.Freezable>，則您應該凍結它以取得先前所述的效能優勢。</span><span class="sxs-lookup"><span data-stu-id="df812-145">If these conditions are false, and you don't intend to modify the <xref:System.Windows.Freezable>, then you should freeze it to gain the performance benefits described earlier.</span></span>

<span data-ttu-id="df812-146">一旦呼叫可凍結的<xref:System.Windows.Freezable.Freeze%2A>方法之後，就無法再修改它。</span><span class="sxs-lookup"><span data-stu-id="df812-146">Once you call a freezable's <xref:System.Windows.Freezable.Freeze%2A> method, it can no longer be modified.</span></span> <span data-ttu-id="df812-147">嘗試修改凍結的物件會導致<xref:System.InvalidOperationException>擲回。</span><span class="sxs-lookup"><span data-stu-id="df812-147">Attempting to modify a frozen object causes an <xref:System.InvalidOperationException> to be thrown.</span></span> <span data-ttu-id="df812-148">下列程式碼會擲回例外狀況，因為我們嘗試在凍結之後修改筆刷。</span><span class="sxs-lookup"><span data-stu-id="df812-148">The following code throws an exception, because we attempt to modify the brush after it's been frozen.</span></span>

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]

<span data-ttu-id="df812-149">若要避免擲回這個例外狀況，您<xref:System.Windows.Freezable.IsFrozen%2A>可以使用方法來判斷<xref:System.Windows.Freezable>是否已凍結。</span><span class="sxs-lookup"><span data-stu-id="df812-149">To avoid throwing this exception, you can use the <xref:System.Windows.Freezable.IsFrozen%2A> method to determine whether a <xref:System.Windows.Freezable> is frozen.</span></span>

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

<span data-ttu-id="df812-150">在上述程式碼範例中，會使用<xref:System.Windows.Freezable.Clone%2A>方法，以已凍結的物件製作可修改的複本。</span><span class="sxs-lookup"><span data-stu-id="df812-150">In the preceding code example, a modifiable copy was made of a frozen object using the <xref:System.Windows.Freezable.Clone%2A> method.</span></span> <span data-ttu-id="df812-151">下一節會更詳細地討論複製。</span><span class="sxs-lookup"><span data-stu-id="df812-151">The next section discusses cloning in more detail.</span></span>

> [!NOTE]
> <span data-ttu-id="df812-152">由於凍結的可凍結無法繪製動畫，因此當您嘗試以動畫顯示<xref:System.Windows.Freezable> <xref:System.Windows.Media.Animation.Storyboard>時，動畫系統會自動建立凍結物件的可修改複本。</span><span class="sxs-lookup"><span data-stu-id="df812-152">Because a frozen freezable cannot be animated, the animation system will automatically create modifiable clones of frozen <xref:System.Windows.Freezable> objects when you try to animate them with a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="df812-153">若要消除複製所造成的效能額外負荷，如果您想要以動畫顯示物件，請將它保留為未凍結。</span><span class="sxs-lookup"><span data-stu-id="df812-153">To eliminate the performance overhead caused by cloning, leave an object unfrozen if you intend to animate it.</span></span> <span data-ttu-id="df812-154">如需使用分鏡腳本製作動畫的詳細資訊，請參閱分鏡腳本[總覽](../graphics-multimedia/storyboards-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="df812-154">For more information about animating with storyboards, see the [Storyboards Overview](../graphics-multimedia/storyboards-overview.md).</span></span>

### <a name="freezing-from-markup"></a><span data-ttu-id="df812-155">從標記凍結</span><span class="sxs-lookup"><span data-stu-id="df812-155">Freezing from Markup</span></span>

<span data-ttu-id="df812-156">若要凍結<xref:System.Windows.Freezable>標記中宣告的物件，您可以`PresentationOptions:Freeze`使用屬性。</span><span class="sxs-lookup"><span data-stu-id="df812-156">To freeze a <xref:System.Windows.Freezable> object declared in markup, you use the `PresentationOptions:Freeze` attribute.</span></span> <span data-ttu-id="df812-157">在下列範例中， <xref:System.Windows.Media.SolidColorBrush>會宣告為頁面資源並凍結。</span><span class="sxs-lookup"><span data-stu-id="df812-157">In the following example, a <xref:System.Windows.Media.SolidColorBrush> is declared as a page resource and frozen.</span></span> <span data-ttu-id="df812-158">然後，它會用來設定按鈕的背景。</span><span class="sxs-lookup"><span data-stu-id="df812-158">It is then used to set the background of a button.</span></span>

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]

<span data-ttu-id="df812-159">若要使用`Freeze`屬性，您必須對應至展示選項命名空間： `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`。</span><span class="sxs-lookup"><span data-stu-id="df812-159">To use the `Freeze` attribute, you must map to the presentation options namespace: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`.</span></span> <span data-ttu-id="df812-160">`PresentationOptions`是對應此命名空間的建議前置詞：</span><span class="sxs-lookup"><span data-stu-id="df812-160">`PresentationOptions` is the recommended prefix for mapping this namespace:</span></span>

```xaml
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
```

<span data-ttu-id="df812-161">由於並非所有的 XAML 讀取器都會辨識此屬性，因此建議您使用[mc：可忽略的屬性](mc-ignorable-attribute.md)，將`Presentation:Freeze`屬性標記為可忽略：</span><span class="sxs-lookup"><span data-stu-id="df812-161">Because not all XAML readers recognize this attribute, it's recommended that you use the [mc:Ignorable Attribute](mc-ignorable-attribute.md) to mark the `Presentation:Freeze` attribute as ignorable:</span></span>

```xaml
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="PresentationOptions"
```

<span data-ttu-id="df812-162">如需詳細資訊，請參閱[mc：可忽略屬性](mc-ignorable-attribute.md)頁面。</span><span class="sxs-lookup"><span data-stu-id="df812-162">For more information, see the [mc:Ignorable Attribute](mc-ignorable-attribute.md) page.</span></span>

### <a name="unfreezing-a-freezable"></a><span data-ttu-id="df812-163">"解除凍結" 是一個凍結的</span><span class="sxs-lookup"><span data-stu-id="df812-163">"Unfreezing" a Freezable</span></span>

<span data-ttu-id="df812-164">凍結之後，永遠<xref:System.Windows.Freezable>無法修改或解除凍結，不過，您可以<xref:System.Windows.Freezable.Clone%2A>使用或<xref:System.Windows.Freezable.CloneCurrentValue%2A>方法來建立未凍結的複製。</span><span class="sxs-lookup"><span data-stu-id="df812-164">Once frozen, a <xref:System.Windows.Freezable> can never be modified or unfrozen; however, you can create an unfrozen clone using the <xref:System.Windows.Freezable.Clone%2A> or <xref:System.Windows.Freezable.CloneCurrentValue%2A> method.</span></span>

<span data-ttu-id="df812-165">在下列範例中，按鈕的背景是以筆刷設定的，該筆刷會被凍結。</span><span class="sxs-lookup"><span data-stu-id="df812-165">In the following example, the button's background is set with a brush and that brush is then frozen.</span></span> <span data-ttu-id="df812-166">未凍結的複本是由使用<xref:System.Windows.Freezable.Clone%2A>方法的筆刷所組成。</span><span class="sxs-lookup"><span data-stu-id="df812-166">An unfrozen copy is made of the brush using the <xref:System.Windows.Freezable.Clone%2A> method.</span></span> <span data-ttu-id="df812-167">複製已修改，並用於將按鈕的背景從黃色變更為紅色。</span><span class="sxs-lookup"><span data-stu-id="df812-167">The clone is modified and used to change the button's background from yellow to red.</span></span>

[!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
[!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]

> [!NOTE]
> <span data-ttu-id="df812-168">不論您使用哪一種複製方法，動畫永遠不會複製到<xref:System.Windows.Freezable>新的。</span><span class="sxs-lookup"><span data-stu-id="df812-168">Regardless of which clone method you use, animations are never copied to the new <xref:System.Windows.Freezable>.</span></span>

<span data-ttu-id="df812-169"><xref:System.Windows.Freezable.Clone%2A> 和<xref:System.Windows.Freezable.CloneCurrentValue%2A>方法會產生能凍結的深層複本。</span><span class="sxs-lookup"><span data-stu-id="df812-169">The <xref:System.Windows.Freezable.Clone%2A> and <xref:System.Windows.Freezable.CloneCurrentValue%2A> methods produce deep copies of the freezable.</span></span> <span data-ttu-id="df812-170">如果可凍結的包含其他已凍結的無法凍結物件，它們也會進行複製並加以修改。</span><span class="sxs-lookup"><span data-stu-id="df812-170">If the freezable contains other frozen freezable objects, they are also cloned and made modifiable.</span></span> <span data-ttu-id="df812-171">例如，如果您複製凍結<xref:System.Windows.Media.PathGeometry> ，使其成為可修改的，則它所包含的圖形和區段也會一併複製並成為可修改的。</span><span class="sxs-lookup"><span data-stu-id="df812-171">For example, if you clone a frozen <xref:System.Windows.Media.PathGeometry> to make it modifiable, the figures and segments it contains are also copied and made modifiable.</span></span>

<a name="createyourownfreezableclass"></a>

## <a name="creating-your-own-freezable-class"></a><span data-ttu-id="df812-172">建立您自己的無法凍結類別</span><span class="sxs-lookup"><span data-stu-id="df812-172">Creating Your Own Freezable Class</span></span>

<span data-ttu-id="df812-173">衍生自<xref:System.Windows.Freezable>的類別會取得下列功能。</span><span class="sxs-lookup"><span data-stu-id="df812-173">A class that derives from <xref:System.Windows.Freezable> gains the following features.</span></span>

- <span data-ttu-id="df812-174">特殊狀態：唯讀（凍結）和可寫入的狀態。</span><span class="sxs-lookup"><span data-stu-id="df812-174">Special states: a read-only (frozen) and a writable state.</span></span>

- <span data-ttu-id="df812-175">執行緒安全：凍結<xref:System.Windows.Freezable>可以線上程之間共用。</span><span class="sxs-lookup"><span data-stu-id="df812-175">Thread safety: a frozen <xref:System.Windows.Freezable> can be shared across threads.</span></span>

- <span data-ttu-id="df812-176">詳細的變更通知：不同于<xref:System.Windows.DependencyObject>其他，當子屬性值變更時，可凍結的物件會提供變更通知。</span><span class="sxs-lookup"><span data-stu-id="df812-176">Detailed change notification: Unlike other <xref:System.Windows.DependencyObject>s, Freezable objects provide change notifications when sub-property values change.</span></span>

- <span data-ttu-id="df812-177">輕鬆複製：可凍結的類別已經執行數個可產生深層複製的方法。</span><span class="sxs-lookup"><span data-stu-id="df812-177">Easy cloning: the Freezable class has already implemented several methods that produce deep clones.</span></span>

<span data-ttu-id="df812-178"><xref:System.Windows.Freezable>是的<xref:System.Windows.DependencyObject>類型，因此會使用相依性屬性系統。</span><span class="sxs-lookup"><span data-stu-id="df812-178">A <xref:System.Windows.Freezable> is a type of <xref:System.Windows.DependencyObject>, and therefore uses the dependency property system.</span></span> <span data-ttu-id="df812-179">您的<xref:System.Windows.Freezable>類別屬性不一定要是相依性屬性，但使用相依性屬性將會減少您必須撰寫的程式碼數量，因為類別是設計成考慮相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="df812-179">Your class properties don't have to be dependency properties, but using dependency properties will reduce the amount of code you have to write, because the <xref:System.Windows.Freezable> class was designed with dependency properties in mind.</span></span> <span data-ttu-id="df812-180">如需相依性屬性系統的詳細資訊，請參閱相依性[屬性總覽](dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="df812-180">For more information about the dependency property system, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span>

<span data-ttu-id="df812-181">每<xref:System.Windows.Freezable>個子類別都<xref:System.Windows.Freezable.CreateInstanceCore%2A>必須覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="df812-181">Every <xref:System.Windows.Freezable> subclass must override the <xref:System.Windows.Freezable.CreateInstanceCore%2A> method.</span></span> <span data-ttu-id="df812-182">如果您的類別使用相依性屬性來取得其所有資料，您就已完成。</span><span class="sxs-lookup"><span data-stu-id="df812-182">If your class uses dependency properties for all its data, you're finished.</span></span>

<span data-ttu-id="df812-183">如果您的類別包含非相依性屬性資料成員，您也必須覆寫下列方法：</span><span class="sxs-lookup"><span data-stu-id="df812-183">If your class contains non-dependency property data members, you must also override the following methods:</span></span>

- <xref:System.Windows.Freezable.CloneCore%2A>

- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>

- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>

- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>

- <xref:System.Windows.Freezable.FreezeCore%2A>

<span data-ttu-id="df812-184">您也必須觀察下列用來存取和寫入非相依性屬性之資料成員的規則：</span><span class="sxs-lookup"><span data-stu-id="df812-184">You must also observe the following rules for accessing and writing to data members that are not dependency properties:</span></span>

- <span data-ttu-id="df812-185">在讀取非相依性屬性資料成員的任何 API 開頭，呼叫<xref:System.Windows.Freezable.ReadPreamble%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="df812-185">At the beginning of any API that reads non-dependency property data members, call the <xref:System.Windows.Freezable.ReadPreamble%2A> method.</span></span>

- <span data-ttu-id="df812-186">在寫入非相依性屬性資料成員的任何 API 開始時，呼叫<xref:System.Windows.Freezable.WritePreamble%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="df812-186">At the beginning of any API that writes non-dependency property data members, call the <xref:System.Windows.Freezable.WritePreamble%2A> method.</span></span> <span data-ttu-id="df812-187">（在 API 中呼叫<xref:System.Windows.Freezable.WritePreamble%2A>之後， <xref:System.Windows.Freezable.ReadPreamble%2A>如果您也讀取非相依性屬性資料成員，則不需要對進行額外的呼叫）。</span><span class="sxs-lookup"><span data-stu-id="df812-187">(Once you've called <xref:System.Windows.Freezable.WritePreamble%2A> in an API, you don't need to make an additional call to <xref:System.Windows.Freezable.ReadPreamble%2A> if you also read non-dependency property data members.)</span></span>

- <span data-ttu-id="df812-188">先呼叫<xref:System.Windows.Freezable.WritePostscript%2A>方法，再結束寫入非相依性屬性資料成員的方法。</span><span class="sxs-lookup"><span data-stu-id="df812-188">Call the <xref:System.Windows.Freezable.WritePostscript%2A> method before exiting methods that write to non-dependency property data members.</span></span>

<span data-ttu-id="df812-189">如果您的類別包含屬於<xref:System.Windows.DependencyObject>物件的非相依性屬性資料成員，則您也必須在每次變更其中一個值時<xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A>呼叫方法，即使您要將成員設定為`null`也一樣。</span><span class="sxs-lookup"><span data-stu-id="df812-189">If your class contains non-dependency-property data members that are <xref:System.Windows.DependencyObject> objects, you must also call the <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> method each time you change one of their values, even if you're setting the member to `null`.</span></span>

> [!NOTE]
> <span data-ttu-id="df812-190">請務必使用基底實作為呼叫<xref:System.Windows.Freezable>來開始覆寫的每個方法。</span><span class="sxs-lookup"><span data-stu-id="df812-190">It's very important that you begin each <xref:System.Windows.Freezable> method you override with a call to the base implementation.</span></span>

<span data-ttu-id="df812-191">如需自訂<xref:System.Windows.Freezable>類別的範例，請參閱[自訂動畫範例](https://go.microsoft.com/fwlink/?LinkID=159981)。</span><span class="sxs-lookup"><span data-stu-id="df812-191">For an example of a custom <xref:System.Windows.Freezable> class, see the [Custom Animation Sample](https://go.microsoft.com/fwlink/?LinkID=159981).</span></span>

## <a name="see-also"></a><span data-ttu-id="df812-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df812-192">See also</span></span>

- <xref:System.Windows.Freezable>
- [<span data-ttu-id="df812-193">自訂動畫範例</span><span class="sxs-lookup"><span data-stu-id="df812-193">Custom Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159981)
- [<span data-ttu-id="df812-194">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="df812-194">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="df812-195">自訂相依性屬性</span><span class="sxs-lookup"><span data-stu-id="df812-195">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
