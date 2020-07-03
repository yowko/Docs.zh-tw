---
title: 路徑標記語法
description: 瞭解您可以用來在 Windows Presentation Foundation （WPF）中指定精簡路徑幾何的強大且複雜的迷你語言。
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: 6d2778522b622f0b0dcb59673e793a6d772a4b4f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853656"
---
# <a name="path-markup-syntax"></a><span data-ttu-id="1907f-103">路徑標記語法</span><span class="sxs-lookup"><span data-stu-id="1907f-103">Path Markup Syntax</span></span>
<span data-ttu-id="1907f-104">在[WPF 中的圖形和基本繪圖](shapes-and-basic-drawing-in-wpf-overview.md)和[幾何總覽](geometry-overview.md)中會討論路徑，不過，本主題詳細說明您可以使用的強大且複雜的迷你語言，來指定更簡潔地的路徑幾何 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1907f-104">Paths are discussed in [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md) and the [Geometry Overview](geometry-overview.md), however, this topic describes in detail the powerful and complex mini-language you can use to specify path geometries more compactly using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a><span data-ttu-id="1907f-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="1907f-105">Prerequisites</span></span>  
 <span data-ttu-id="1907f-106">若要瞭解本主題，您應該熟悉物件的基本功能 <xref:System.Windows.Media.Geometry> 。</span><span class="sxs-lookup"><span data-stu-id="1907f-106">To understand this topic, you should be familiar with the basic features of <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="1907f-107">如需詳細資訊，請參閱[幾何總覽](geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1907f-107">For more information, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="abouthisdocument"></a>
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a><span data-ttu-id="1907f-108">StreamGeometry 和 PathFigureCollection 迷你語言</span><span class="sxs-lookup"><span data-stu-id="1907f-108">StreamGeometry and PathFigureCollection Mini-Languages</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="1907f-109">提供兩個類別，提供用來描述幾何路徑的迷你語言： <xref:System.Windows.Media.StreamGeometry> 和 <xref:System.Windows.Media.PathFigureCollection> 。</span><span class="sxs-lookup"><span data-stu-id="1907f-109">provides two classes that provide mini-languages for describing geometric paths: <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.PathFigureCollection>.</span></span>  
  
- <span data-ttu-id="1907f-110"><xref:System.Windows.Media.StreamGeometry>當您設定類型的屬性（ <xref:System.Windows.Media.Geometry> 例如的 <xref:System.Windows.UIElement.Clip%2A> 屬性 <xref:System.Windows.UIElement> 或 <xref:System.Windows.Shapes.Path.Data%2A> <xref:System.Windows.Shapes.Path> 專案的屬性）時，會使用迷你語言。</span><span class="sxs-lookup"><span data-stu-id="1907f-110">You use the <xref:System.Windows.Media.StreamGeometry> mini-language when setting a property of type <xref:System.Windows.Media.Geometry>, such as the <xref:System.Windows.UIElement.Clip%2A> property of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Shapes.Path.Data%2A> property of a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="1907f-111">下列範例會使用屬性語法來建立 <xref:System.Windows.Media.StreamGeometry> 。</span><span class="sxs-lookup"><span data-stu-id="1907f-111">The following example uses attribute syntax to create a <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
- <span data-ttu-id="1907f-112">當您設定的屬性時，會使用 <xref:System.Windows.Media.PathFigureCollection> 迷你語言 <xref:System.Windows.Media.PathGeometry.Figures%2A> <xref:System.Windows.Media.PathGeometry> 。</span><span class="sxs-lookup"><span data-stu-id="1907f-112">You use the <xref:System.Windows.Media.PathFigureCollection> mini-language when setting the <xref:System.Windows.Media.PathGeometry.Figures%2A> property of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="1907f-113">下列範例會使用屬性語法來建立的 <xref:System.Windows.Media.PathFigureCollection> <xref:System.Windows.Media.PathGeometry> 。</span><span class="sxs-lookup"><span data-stu-id="1907f-113">The following example uses a attribute syntax to create a <xref:System.Windows.Media.PathFigureCollection> for a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 <span data-ttu-id="1907f-114">在上述範例中，您可以發現這兩個迷你語言非常相似。</span><span class="sxs-lookup"><span data-stu-id="1907f-114">As you can see from the preceding examples, the two mini-languages are very similar.</span></span> <span data-ttu-id="1907f-115"><xref:System.Windows.Media.PathGeometry>在您可以使用的任何情況下，一律可以使用， <xref:System.Windows.Media.StreamGeometry> 因此您應該使用哪一個？</span><span class="sxs-lookup"><span data-stu-id="1907f-115">It's always possible to use a <xref:System.Windows.Media.PathGeometry> in any situation where you could use a <xref:System.Windows.Media.StreamGeometry>; so which one should you use?</span></span> <span data-ttu-id="1907f-116"><xref:System.Windows.Media.StreamGeometry>當您建立後不需要修改路徑時，請使用， <xref:System.Windows.Media.PathGeometry> 如果您需要修改路徑，請使用。</span><span class="sxs-lookup"><span data-stu-id="1907f-116">Use a <xref:System.Windows.Media.StreamGeometry> when you don't need to modify the path after creating it; use a <xref:System.Windows.Media.PathGeometry> if you do need to modify the path.</span></span>  
  
 <span data-ttu-id="1907f-117">如需和物件之間差異的詳細資訊 <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> ，請參閱[幾何總覽](geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1907f-117">For more information about the differences between <xref:System.Windows.Media.PathGeometry> and <xref:System.Windows.Media.StreamGeometry> objects, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
### <a name="a-note-about-white-space"></a><span data-ttu-id="1907f-118">關於空白字元</span><span class="sxs-lookup"><span data-stu-id="1907f-118">A Note about White Space</span></span>  
 <span data-ttu-id="1907f-119">為了簡潔起見，會在後續的語法區段中會顯示單一空格，但是在顯示單一空格的位置也接受多個空格。</span><span class="sxs-lookup"><span data-stu-id="1907f-119">For brevity, a single space is shown in the syntax sections that follow, but multiple spaces are also acceptable wherever a single space is shown.</span></span>  
  
 <span data-ttu-id="1907f-120">兩個數字實際上不需要以逗號或空白字元分隔，但只有在產生的字串不明確時，才可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="1907f-120">Two numbers don’t actually have to be separated by a comma or white space, but this can only be done when the resulting string is unambiguous.</span></span> <span data-ttu-id="1907f-121">比方說， `2..3` 實際上是兩個數字： "2"。</span><span class="sxs-lookup"><span data-stu-id="1907f-121">For instance, `2..3` is actually two numbers: "2."</span></span> <span data-ttu-id="1907f-122">和 ".3"。</span><span class="sxs-lookup"><span data-stu-id="1907f-122">And ".3".</span></span> <span data-ttu-id="1907f-123">同樣地， `2-3` 是 "2" 和 "-3"。</span><span class="sxs-lookup"><span data-stu-id="1907f-123">Similarly, `2-3` is "2" and "-3".</span></span> <span data-ttu-id="1907f-124">命令之前或之後也一樣不需要空格。</span><span class="sxs-lookup"><span data-stu-id="1907f-124">Spaces are not required before or after commands, either.</span></span>  
  
### <a name="syntax"></a><span data-ttu-id="1907f-125">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-125">Syntax</span></span>  
 <span data-ttu-id="1907f-126">的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 屬性使用方式語法 <xref:System.Windows.Media.StreamGeometry> 是由選擇性 <xref:System.Windows.Media.FillRule> 值和一或多個圖表描述所組成。</span><span class="sxs-lookup"><span data-stu-id="1907f-126">The [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribute usage syntax for a <xref:System.Windows.Media.StreamGeometry> is composed of an optional <xref:System.Windows.Media.FillRule> value and one or more figure descriptions.</span></span>  
  
|<span data-ttu-id="1907f-127">StreamGeometry XAML 屬性使用方式</span><span class="sxs-lookup"><span data-stu-id="1907f-127">StreamGeometry XAML Attribute Usage</span></span>|  
|-----------------------------------------|  
|<span data-ttu-id="1907f-128">`<`*物件\*\*屬性* `="` [ `fillRule` ] `figureDescription` [ `figureDescription` ] \*`" ... />`</span><span class="sxs-lookup"><span data-stu-id="1907f-128">`<` *object* *property* `="`[ `fillRule`] `figureDescription`[ `figureDescription`]\* `" ... />`</span></span>|  
  
 <span data-ttu-id="1907f-129">的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 屬性使用方式語法 <xref:System.Windows.Media.PathFigureCollection> 是由一或多個圖表描述所組成。</span><span class="sxs-lookup"><span data-stu-id="1907f-129">The [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribute usage syntax for a <xref:System.Windows.Media.PathFigureCollection> is composed of one or more figure descriptions.</span></span>  
  
|<span data-ttu-id="1907f-130">PathFigureCollection XAML 屬性使用方式</span><span class="sxs-lookup"><span data-stu-id="1907f-130">PathFigureCollection XAML Attribute Usage</span></span>|  
|-----------------------------------------------|  
|<span data-ttu-id="1907f-131">`<`*物件\*\*屬性* `="` `figureDescription` [ `figureDescription` ] \*`" ... />`</span><span class="sxs-lookup"><span data-stu-id="1907f-131">`<` *object* *property* `="` `figureDescription`[ `figureDescription`]\* `" ... />`</span></span>|  
  
|<span data-ttu-id="1907f-132">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-132">Term</span></span>|<span data-ttu-id="1907f-133">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-133">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1907f-134">*fillRule*</span><span class="sxs-lookup"><span data-stu-id="1907f-134">*fillRule*</span></span>|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-135">指定是否 <xref:System.Windows.Media.StreamGeometry> 使用 <xref:System.Windows.Media.FillRule.EvenOdd> 或 <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1907f-135">Specifies whether the <xref:System.Windows.Media.StreamGeometry> uses the <xref:System.Windows.Media.FillRule.EvenOdd> or <xref:System.Windows.Media.FillRule.Nonzero><xref:System.Windows.Media.PathGeometry.FillRule%2A>.</span></span><br /><br /> <span data-ttu-id="1907f-136">-   `F0`指定 <xref:System.Windows.Media.FillRule.EvenOdd> 填滿規則。</span><span class="sxs-lookup"><span data-stu-id="1907f-136">-   `F0` specifies the <xref:System.Windows.Media.FillRule.EvenOdd> fill rule.</span></span><br /><span data-ttu-id="1907f-137">-   `F1`指定 <xref:System.Windows.Media.FillRule.Nonzero> 填滿規則。</span><span class="sxs-lookup"><span data-stu-id="1907f-137">-   `F1` specifies the <xref:System.Windows.Media.FillRule.Nonzero> fill rule.</span></span><br /><br /> <span data-ttu-id="1907f-138">如果您省略此命令，則子路徑會使用預設行為，也就是 <xref:System.Windows.Media.FillRule.EvenOdd> 。</span><span class="sxs-lookup"><span data-stu-id="1907f-138">If you omit this command, the subpath uses the default behavior, which is <xref:System.Windows.Media.FillRule.EvenOdd>.</span></span> <span data-ttu-id="1907f-139">如果您指定此命令，您必須先放置它。</span><span class="sxs-lookup"><span data-stu-id="1907f-139">If you specify this command, you must place it first.</span></span>|  
|<span data-ttu-id="1907f-140">*figureDescription*</span><span class="sxs-lookup"><span data-stu-id="1907f-140">*figureDescription*</span></span>|<span data-ttu-id="1907f-141">由移動命令、繪製命令以及選擇性的關閉命令所組成的圖表。</span><span class="sxs-lookup"><span data-stu-id="1907f-141">A figure composed of a move command, draw commands, and an optional close command.</span></span><br /><br /> <span data-ttu-id="1907f-142">`moveCommand` `drawCommands`  `[` `closeCommand` `]`</span><span class="sxs-lookup"><span data-stu-id="1907f-142">`moveCommand` `drawCommands`  `[` `closeCommand` `]`</span></span>|  
|<span data-ttu-id="1907f-143">*moveCommand*</span><span class="sxs-lookup"><span data-stu-id="1907f-143">*moveCommand*</span></span>|<span data-ttu-id="1907f-144">指定圖表起點的移動命令。</span><span class="sxs-lookup"><span data-stu-id="1907f-144">A move command that specifies the start point of the figure.</span></span> <span data-ttu-id="1907f-145">請參閱[移動命令](#themovecommand)一節。</span><span class="sxs-lookup"><span data-stu-id="1907f-145">See the [Move Command](#themovecommand) section.</span></span>|  
|<span data-ttu-id="1907f-146">*drawCommands*</span><span class="sxs-lookup"><span data-stu-id="1907f-146">*drawCommands*</span></span>|<span data-ttu-id="1907f-147">說明圖表內容的一或多個繪製命令。</span><span class="sxs-lookup"><span data-stu-id="1907f-147">One or more drawing commands that describe the figure's contents.</span></span> <span data-ttu-id="1907f-148">請參閱[繪製命令](#drawcommands)一節。</span><span class="sxs-lookup"><span data-stu-id="1907f-148">See the [Draw Commands](#drawcommands) section.</span></span>|  
|<span data-ttu-id="1907f-149">*closeCommand*</span><span class="sxs-lookup"><span data-stu-id="1907f-149">*closeCommand*</span></span>|<span data-ttu-id="1907f-150">關閉圖表的選擇性關閉命令。</span><span class="sxs-lookup"><span data-stu-id="1907f-150">An optional close command that closes figure.</span></span> <span data-ttu-id="1907f-151">請參閱[關閉命令](#closecommand)一節。</span><span class="sxs-lookup"><span data-stu-id="1907f-151">See the [Close Command](#closecommand) section.</span></span>|  
  
<a name="themovecommand"></a>
## <a name="move-command"></a><span data-ttu-id="1907f-152">移動命令</span><span class="sxs-lookup"><span data-stu-id="1907f-152">Move Command</span></span>  
 <span data-ttu-id="1907f-153">指定新圖表的起點。</span><span class="sxs-lookup"><span data-stu-id="1907f-153">Specifies the start point of a new figure.</span></span>  
  
|<span data-ttu-id="1907f-154">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-154">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="1907f-155">`M`*startPoint*</span><span class="sxs-lookup"><span data-stu-id="1907f-155">`M` *startPoint*</span></span><br /><br /> <span data-ttu-id="1907f-156">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-156">- or -</span></span><br /><br /> <span data-ttu-id="1907f-157">`m`*startPoint*</span><span class="sxs-lookup"><span data-stu-id="1907f-157">`m` *startPoint*</span></span>|  
  
|<span data-ttu-id="1907f-158">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-158">Term</span></span>|<span data-ttu-id="1907f-159">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-159">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1907f-160">*startPoint*</span><span class="sxs-lookup"><span data-stu-id="1907f-160">*startPoint*</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-161">新圖表的起點。</span><span class="sxs-lookup"><span data-stu-id="1907f-161">The start point of a new figure.</span></span>|  
  
 <span data-ttu-id="1907f-162">大寫 `M` 表示 `startPoint` 為絕對值; 小寫表示為上一個 `m` 點的 `startPoint` 位移，如果不存在，則為（0，0）。</span><span class="sxs-lookup"><span data-stu-id="1907f-162">An uppercase `M` indicates that `startPoint` is an absolute value; a lowercase `m` indicates that `startPoint` is an offset to the previous point, or (0,0) if none exists.</span></span> <span data-ttu-id="1907f-163">如果您在移動命令之後列出多個點，則會如您指定線條命令一般，在這些點之間繪製線條。</span><span class="sxs-lookup"><span data-stu-id="1907f-163">If you list multiple points after the move command, a line is drawn to those points though you specified the line command.</span></span>  
  
<a name="drawcommands"></a>
## <a name="draw-commands"></a><span data-ttu-id="1907f-164">繪製命令</span><span class="sxs-lookup"><span data-stu-id="1907f-164">Draw Commands</span></span>  
 <span data-ttu-id="1907f-165">繪製命令可以由數個圖形命令組成。</span><span class="sxs-lookup"><span data-stu-id="1907f-165">A draw command can consist of several shape commands.</span></span> <span data-ttu-id="1907f-166">有下列圖形命令可使用：線條、水平線、垂直線、三次方貝茲曲線、二次方貝茲曲線、平滑三次方貝茲曲線、平滑二次方貝茲曲線，以及橢圓形弧線。</span><span class="sxs-lookup"><span data-stu-id="1907f-166">The following shape commands are available: line, horizontal line, vertical line, cubic Bezier curve, quadratic Bezier curve, smooth cubic Bezier curve, smooth quadratic Bezier curve, and elliptical arc.</span></span>  
  
 <span data-ttu-id="1907f-167">透過使用大寫或小寫字母來輸入每個命令：大寫字母表示絕對值，而小寫字母表示相對值：該區段的控制點相對於先前範例的結束點。</span><span class="sxs-lookup"><span data-stu-id="1907f-167">You enter each command by using either an uppercase or a lowercase letter: uppercase letters denote absolute values and lowercase letters denote relative values: the control points for that segment are relative to the end point of the preceding example.</span></span> <span data-ttu-id="1907f-168">當按序輸入多個相同類型的命令時，您可以省略重複的命令專案;例如， `L 100,200 300,400` 相當於 `L 100,200 L 300,400` 。</span><span class="sxs-lookup"><span data-stu-id="1907f-168">When sequentially entering more than one command of the same type, you can omit the duplicate command entry; for example, `L 100,200 300,400` is equivalent to `L 100,200 L 300,400`.</span></span> <span data-ttu-id="1907f-169">下表說明**move**和**draw**命令。</span><span class="sxs-lookup"><span data-stu-id="1907f-169">The following table describes the **move** and **draw** commands.</span></span>  
  
### <a name="line-command"></a><span data-ttu-id="1907f-170">線條命令</span><span class="sxs-lookup"><span data-stu-id="1907f-170">Line Command</span></span>  
 <span data-ttu-id="1907f-171">在目前的點和指定的點之間建立直線。</span><span class="sxs-lookup"><span data-stu-id="1907f-171">Creates a straight line between the current point and the specified end point.</span></span> <span data-ttu-id="1907f-172">`l 20 30`和 `L 20,30` 是有效**行**命令的範例。</span><span class="sxs-lookup"><span data-stu-id="1907f-172">`l 20 30` and `L 20,30` are examples of valid **line** commands.</span></span>  
  
|<span data-ttu-id="1907f-173">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-173">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="1907f-174">`L`*端點*</span><span class="sxs-lookup"><span data-stu-id="1907f-174">`L` *endPoint*</span></span><br /><br /> <span data-ttu-id="1907f-175">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-175">- or -</span></span><br /><br /> <span data-ttu-id="1907f-176">`l`*端點*</span><span class="sxs-lookup"><span data-stu-id="1907f-176">`l` *endPoint*</span></span>|  
  
|<span data-ttu-id="1907f-177">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-177">Term</span></span>|<span data-ttu-id="1907f-178">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-178">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1907f-179">*左端*</span><span class="sxs-lookup"><span data-stu-id="1907f-179">*endPoint*</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-180">行的結束點。</span><span class="sxs-lookup"><span data-stu-id="1907f-180">The end point of the line.</span></span>|  

<span data-ttu-id="1907f-181">大寫 `L` 表示 `endPoint` 為絕對值; 小寫表示為上一個 `l` 點的 `endPoint` 位移，如果不存在，則為（0，0）。</span><span class="sxs-lookup"><span data-stu-id="1907f-181">An uppercase `L` indicates that `endPoint` is an absolute value; a lowercase `l` indicates that `endPoint` is an offset to the previous point, or (0,0) if none exists.</span></span>

### <a name="horizontal-line-command"></a><span data-ttu-id="1907f-182">水平線命令</span><span class="sxs-lookup"><span data-stu-id="1907f-182">Horizontal Line Command</span></span>  
 <span data-ttu-id="1907f-183">在目前的點和指定的 X 座標之間建立水平線。</span><span class="sxs-lookup"><span data-stu-id="1907f-183">Creates a horizontal line between the current point and the specified x-coordinate.</span></span> <span data-ttu-id="1907f-184">`H 90` 為有效水平線命令的範例。</span><span class="sxs-lookup"><span data-stu-id="1907f-184">`H 90` is an example of a valid horizontal line command.</span></span>

|<span data-ttu-id="1907f-185">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-185">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="1907f-186">`H`  *x*</span><span class="sxs-lookup"><span data-stu-id="1907f-186">`H`  *x*</span></span><br /><br /> <span data-ttu-id="1907f-187">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-187">- or -</span></span><br /><br /> <span data-ttu-id="1907f-188">`h`  *x*</span><span class="sxs-lookup"><span data-stu-id="1907f-188">`h`  *x*</span></span>|  
  
|<span data-ttu-id="1907f-189">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-189">Term</span></span>|<span data-ttu-id="1907f-190">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-190">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1907f-191">*x*</span><span class="sxs-lookup"><span data-stu-id="1907f-191">*x*</span></span>|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-192">線條結束點的 X 座標。</span><span class="sxs-lookup"><span data-stu-id="1907f-192">The x-coordinate of the end point of the line.</span></span>|  
  
<span data-ttu-id="1907f-193">大寫 `H` 表示 `x` 為絕對值; 小寫表示為上一個 `h` 點的 `x` 位移，如果不存在，則為（0，0）。</span><span class="sxs-lookup"><span data-stu-id="1907f-193">An uppercase `H` indicates that `x` is an absolute value; a lowercase `h` indicates that `x` is an offset to the previous point, or (0,0) if none exists.</span></span>
  
### <a name="vertical-line-command"></a><span data-ttu-id="1907f-194">垂直線命令</span><span class="sxs-lookup"><span data-stu-id="1907f-194">Vertical Line Command</span></span>  
 <span data-ttu-id="1907f-195">在目前的點和指定的 Y 座標之間建立垂直線。</span><span class="sxs-lookup"><span data-stu-id="1907f-195">Creates a vertical line between the current point and the specified y-coordinate.</span></span> <span data-ttu-id="1907f-196">`v 90` 為有效垂直線命令的範例。</span><span class="sxs-lookup"><span data-stu-id="1907f-196">`v 90` is an example of a valid vertical line command.</span></span>

|<span data-ttu-id="1907f-197">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-197">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="1907f-198">`V`  *y*</span><span class="sxs-lookup"><span data-stu-id="1907f-198">`V`  *y*</span></span><br /><br /> <span data-ttu-id="1907f-199">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-199">- or -</span></span><br /><br /> <span data-ttu-id="1907f-200">`v`  *y*</span><span class="sxs-lookup"><span data-stu-id="1907f-200">`v`  *y*</span></span>|  
  
|<span data-ttu-id="1907f-201">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-201">Term</span></span>|<span data-ttu-id="1907f-202">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-202">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1907f-203">*y*</span><span class="sxs-lookup"><span data-stu-id="1907f-203">*y*</span></span>|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-204">線條結束點的 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="1907f-204">The y-coordinate of the end point of the line.</span></span>|  

<span data-ttu-id="1907f-205">大寫 `V` 表示 `y` 為絕對值; 小寫表示為上一個 `v` 點的 `y` 位移，如果不存在，則為（0，0）。</span><span class="sxs-lookup"><span data-stu-id="1907f-205">An uppercase `V` indicates that `y` is an absolute value; a lowercase `v` indicates that `y` is an offset to the previous point, or (0,0) if none exists.</span></span>  

### <a name="cubic-bezier-curve-command"></a><span data-ttu-id="1907f-206">三次方貝茲曲線命令</span><span class="sxs-lookup"><span data-stu-id="1907f-206">Cubic Bezier Curve Command</span></span>  
 <span data-ttu-id="1907f-207">使用兩個指定的控制點（ `controlPoint` 1 和2），在目前的點和指定的結束點之間建立三次方貝茲曲線 `controlPoint` 。</span><span class="sxs-lookup"><span data-stu-id="1907f-207">Creates a cubic Bezier curve between the current point and the specified end point by using the two specified control points (`controlPoint`1 and `controlPoint`2).</span></span> <span data-ttu-id="1907f-208">`C 100,200 200,400 300,200` 為有效曲線命令的範例。</span><span class="sxs-lookup"><span data-stu-id="1907f-208">`C 100,200 200,400 300,200` is an example of a valid curve command.</span></span>  
  
|<span data-ttu-id="1907f-209">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-209">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="1907f-210">`C``controlPoint`1 `controlPoint` 2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="1907f-210">`C` `controlPoint`1`controlPoint`2`endPoint`</span></span><br /><br /> <span data-ttu-id="1907f-211">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-211">- or -</span></span><br /><br /> <span data-ttu-id="1907f-212">`c``controlPoint`1 `controlPoint` 2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="1907f-212">`c` `controlPoint`1`controlPoint`2`endPoint`</span></span>|  
  
|<span data-ttu-id="1907f-213">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-213">Term</span></span>|<span data-ttu-id="1907f-214">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-214">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1907f-215">`controlPoint`1</span><span class="sxs-lookup"><span data-stu-id="1907f-215">`controlPoint`1</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-216">曲線的第一個控制點，它能決定曲線的起始正切函數。</span><span class="sxs-lookup"><span data-stu-id="1907f-216">The first control point of the curve, which determines the starting tangent of the curve.</span></span>|  
|<span data-ttu-id="1907f-217">`controlPoint`2</span><span class="sxs-lookup"><span data-stu-id="1907f-217">`controlPoint`2</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-218">曲線的第二個控制點，它能決定曲線的結束正切函數。</span><span class="sxs-lookup"><span data-stu-id="1907f-218">The second control point of the curve, which determines the ending tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-219">曲線要繪製到的點。</span><span class="sxs-lookup"><span data-stu-id="1907f-219">The point to which the curve is drawn.</span></span>|  
  
### <a name="quadratic-bezier-curve-command"></a><span data-ttu-id="1907f-220">二次方貝茲曲線命令</span><span class="sxs-lookup"><span data-stu-id="1907f-220">Quadratic Bezier Curve Command</span></span>  
 <span data-ttu-id="1907f-221">使用指定的控制點（），在目前的點和指定的結束點之間建立二次方貝茲曲線 `controlPoint` 。</span><span class="sxs-lookup"><span data-stu-id="1907f-221">Creates a quadratic Bezier curve between the current point and the specified end point by using the specified control point (`controlPoint`).</span></span> <span data-ttu-id="1907f-222">`q 100,200 300,200` 為有效二次方貝茲曲線命令的範例。</span><span class="sxs-lookup"><span data-stu-id="1907f-222">`q 100,200 300,200` is an example of a valid quadratic Bezier curve command.</span></span>  
  
|<span data-ttu-id="1907f-223">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-223">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="1907f-224">`Q` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="1907f-224">`Q` `controlPoint` `endPoint`</span></span><br /><br /> <span data-ttu-id="1907f-225">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-225">- or -</span></span><br /><br /> <span data-ttu-id="1907f-226">`q` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="1907f-226">`q` `controlPoint` `endPoint`</span></span>|  
  
|<span data-ttu-id="1907f-227">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-227">Term</span></span>|<span data-ttu-id="1907f-228">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-228">Description</span></span>|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-229">曲線的控制點，它能決定曲線的起始正切函數和結束正切函數。</span><span class="sxs-lookup"><span data-stu-id="1907f-229">The control point of the curve, which determines the starting and ending tangents of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-230">曲線要繪製到的點。</span><span class="sxs-lookup"><span data-stu-id="1907f-230">The point to which the curve is drawn.</span></span>|  
  
### <a name="smooth-cubic-bezier-curve-command"></a><span data-ttu-id="1907f-231">平滑三次方貝茲曲線命令</span><span class="sxs-lookup"><span data-stu-id="1907f-231">Smooth cubic Bezier curve Command</span></span>  
 <span data-ttu-id="1907f-232">在目前的點和指定的結束點之間建立三次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="1907f-232">Creates a cubic Bezier curve between the current point and the specified end point.</span></span> <span data-ttu-id="1907f-233">第一個控制點會假設為 (相對於目前的點) 上一個命令之第二個控制點的反映。</span><span class="sxs-lookup"><span data-stu-id="1907f-233">The first control point is assumed to be the reflection of the second control point of the previous command relative to the current point.</span></span> <span data-ttu-id="1907f-234">如果沒有上一個命令，或者上一個命令不是三次方貝茲曲線命令或平滑三次方貝茲曲線命令，則會假設第一個控制點和目前的點一致。</span><span class="sxs-lookup"><span data-stu-id="1907f-234">If there is no previous command or if the previous command was not a cubic Bezier curve command or a smooth cubic Bezier curve command, assume the first control point is coincident with the current point.</span></span> <span data-ttu-id="1907f-235">第二個控制點是曲線結尾的控制點，是由 `controlPoint` 2 指定。</span><span class="sxs-lookup"><span data-stu-id="1907f-235">The second control point, the control point for the end of the curve, is specified by `controlPoint`2.</span></span> <span data-ttu-id="1907f-236">例如， `S 100,200 200,300` 是有效的平滑三次方貝茲曲線命令。</span><span class="sxs-lookup"><span data-stu-id="1907f-236">For example, `S 100,200 200,300` is a valid smooth cubic Bezier curve command.</span></span>  
  
|<span data-ttu-id="1907f-237">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-237">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="1907f-238">`S` `controlPoint`2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="1907f-238">`S` `controlPoint`2`endPoint`</span></span><br /><br /> <span data-ttu-id="1907f-239">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-239">- or -</span></span><br /><br /> <span data-ttu-id="1907f-240">`s` `controlPoint`2`endPoint`</span><span class="sxs-lookup"><span data-stu-id="1907f-240">`s` `controlPoint`2`endPoint`</span></span>|  
  
|<span data-ttu-id="1907f-241">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-241">Term</span></span>|<span data-ttu-id="1907f-242">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-242">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1907f-243">`controlPoint`2</span><span class="sxs-lookup"><span data-stu-id="1907f-243">`controlPoint`2</span></span>|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-244">曲線的控制點，它能決定曲線的結束正切函數。</span><span class="sxs-lookup"><span data-stu-id="1907f-244">The control point of the curve, which determines the ending tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-245">曲線要繪製到的點。</span><span class="sxs-lookup"><span data-stu-id="1907f-245">The point to which the curve is drawn.</span></span>|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a><span data-ttu-id="1907f-246">平滑二次方貝茲曲線命令</span><span class="sxs-lookup"><span data-stu-id="1907f-246">Smooth quadratic Bezier curve Command</span></span>  
 <span data-ttu-id="1907f-247">在目前的點和指定的結束點之間建立二次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="1907f-247">Creates a quadratic Bezier curve between the current point and the specified end point.</span></span> <span data-ttu-id="1907f-248">控制點會假設為 (相對於目前的點) 上一個命令之控制點的反映。</span><span class="sxs-lookup"><span data-stu-id="1907f-248">The control point is assumed to be the reflection of the control point of the previous command relative to the current point.</span></span> <span data-ttu-id="1907f-249">如果沒有上一個命令，或者上一個命令不是二次方貝茲曲線命令或平滑二次方貝茲曲線命令，則控制點和目前的點一致。</span><span class="sxs-lookup"><span data-stu-id="1907f-249">If there is no previous command or if the previous command was not a quadratic Bezier curve command or a smooth quadratic Bezier curve command, the control point is coincident with the current point.</span></span>  
  
|<span data-ttu-id="1907f-250">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-250">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="1907f-251">`T` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="1907f-251">`T` `controlPoint` `endPoint`</span></span><br /><br /> <span data-ttu-id="1907f-252">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-252">- or -</span></span><br /><br /> <span data-ttu-id="1907f-253">`t` `controlPoint` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="1907f-253">`t` `controlPoint` `endPoint`</span></span>|  
  
|<span data-ttu-id="1907f-254">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-254">Term</span></span>|<span data-ttu-id="1907f-255">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-255">Description</span></span>|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-256">曲線的控制點，它能決定曲線的起始正切函數。</span><span class="sxs-lookup"><span data-stu-id="1907f-256">The control point of the curve, which determines the starting and tangent of the curve.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-257">曲線要繪製到的點。</span><span class="sxs-lookup"><span data-stu-id="1907f-257">The point to which the curve is drawn.</span></span>|  
  
### <a name="elliptical-arc-command"></a><span data-ttu-id="1907f-258">橢圓形弧線命令</span><span class="sxs-lookup"><span data-stu-id="1907f-258">Elliptical Arc Command</span></span>  
 <span data-ttu-id="1907f-259">在目前的點和指定的結束點之間建立橢圓形弧線。</span><span class="sxs-lookup"><span data-stu-id="1907f-259">Creates an elliptical arc between the current point and the specified end point.</span></span>  
  
|<span data-ttu-id="1907f-260">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-260">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="1907f-261">`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="1907f-261">`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span></span><br /><br /> <span data-ttu-id="1907f-262">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-262">- or -</span></span><br /><br /> <span data-ttu-id="1907f-263">`a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span><span class="sxs-lookup"><span data-stu-id="1907f-263">`a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`</span></span>|  
  
|<span data-ttu-id="1907f-264">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-264">Term</span></span>|<span data-ttu-id="1907f-265">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-265">Description</span></span>|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-266">弧線的半徑 X 和 Y。</span><span class="sxs-lookup"><span data-stu-id="1907f-266">The x- and y-radius of the arc.</span></span>|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-267">橢圓形的旋轉 (以角度為單位)。</span><span class="sxs-lookup"><span data-stu-id="1907f-267">The rotation of the ellipse, in degrees.</span></span>|  
|`isLargeArcFlag`|<span data-ttu-id="1907f-268">如果弧線的角度應該為 180 度或大於 180 度，則設定為 1；否則，請設定為 0。</span><span class="sxs-lookup"><span data-stu-id="1907f-268">Set to 1 if the angle of the arc should be 180 degrees or greater; otherwise, set to 0.</span></span>|  
|`sweepDirectionFlag`|<span data-ttu-id="1907f-269">如果弧線是以正值角度的方向繪製，則設定為 1；否則，請設定為 0。</span><span class="sxs-lookup"><span data-stu-id="1907f-269">Set to 1 if the arc is drawn in a positive-angle direction; otherwise, set to 0.</span></span>|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-270">弧線要繪製到的點。</span><span class="sxs-lookup"><span data-stu-id="1907f-270">The point to which the arc is drawn.</span></span>|  
  
<a name="closecommand"></a>
## <a name="the-close-command"></a><span data-ttu-id="1907f-271">關閉命令</span><span class="sxs-lookup"><span data-stu-id="1907f-271">The Close Command</span></span>  
 <span data-ttu-id="1907f-272">結束目前的圖表，並建立連接目前的點和圖表起點的線條。</span><span class="sxs-lookup"><span data-stu-id="1907f-272">Ends the current figure and creates a line that connects the current point to the starting point of the figure.</span></span> <span data-ttu-id="1907f-273">此命令會在圖表的最後一個區段和第一個區段之間建立線條聯結 (邊角)。</span><span class="sxs-lookup"><span data-stu-id="1907f-273">This command creates a line-join (corner) between the last segment and the first segment of the figure.</span></span>  
  
|<span data-ttu-id="1907f-274">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-274">Syntax</span></span>|  
|------------|  
|`Z`<br /><br /> <span data-ttu-id="1907f-275">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-275">- or -</span></span><br /><br /> `z`|  

<a name="pointsyntax"></a>
## <a name="point-syntax"></a><span data-ttu-id="1907f-276">點語法</span><span class="sxs-lookup"><span data-stu-id="1907f-276">Point Syntax</span></span>  
 <span data-ttu-id="1907f-277">描述點的 x 和 y 座標，其中（0，0）是左上角。</span><span class="sxs-lookup"><span data-stu-id="1907f-277">Describes the x- and y-coordinates of a point where (0,0) is the top left corner.</span></span>
  
|<span data-ttu-id="1907f-278">語法</span><span class="sxs-lookup"><span data-stu-id="1907f-278">Syntax</span></span>|  
|------------|  
|<span data-ttu-id="1907f-279">`x` `,` `y`</span><span class="sxs-lookup"><span data-stu-id="1907f-279">`x` `,` `y`</span></span><br /><br /> <span data-ttu-id="1907f-280">- 或 -</span><span class="sxs-lookup"><span data-stu-id="1907f-280">- or -</span></span><br /><br /> <span data-ttu-id="1907f-281">`x` `y`</span><span class="sxs-lookup"><span data-stu-id="1907f-281">`x` `y`</span></span>|  
  
|<span data-ttu-id="1907f-282">詞彙</span><span class="sxs-lookup"><span data-stu-id="1907f-282">Term</span></span>|<span data-ttu-id="1907f-283">描述</span><span class="sxs-lookup"><span data-stu-id="1907f-283">Description</span></span>|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-284">點的 X 座標。</span><span class="sxs-lookup"><span data-stu-id="1907f-284">The x-coordinate of the point.</span></span>|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1907f-285">點的 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="1907f-285">The y-coordinate of the point.</span></span>|  
  
<a name="specialvalues"></a>
## <a name="special-values"></a><span data-ttu-id="1907f-286">特殊值</span><span class="sxs-lookup"><span data-stu-id="1907f-286">Special Values</span></span>  
 <span data-ttu-id="1907f-287">除了標準數值，您也可以使用下列特殊值。</span><span class="sxs-lookup"><span data-stu-id="1907f-287">Instead of a standard numerical value, you can also use the following special values.</span></span> <span data-ttu-id="1907f-288">這些值會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="1907f-288">These values are case-sensitive.</span></span>  
  
 <span data-ttu-id="1907f-289">無限</span><span class="sxs-lookup"><span data-stu-id="1907f-289">Infinity</span></span>  
 <span data-ttu-id="1907f-290">表示 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1907f-290">Represents <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="1907f-291">-Infinity</span><span class="sxs-lookup"><span data-stu-id="1907f-291">-Infinity</span></span>  
 <span data-ttu-id="1907f-292">表示 <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1907f-292">Represents <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="1907f-293">NaN</span><span class="sxs-lookup"><span data-stu-id="1907f-293">NaN</span></span>  
 <span data-ttu-id="1907f-294">表示 <xref:System.Double.NaN?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1907f-294">Represents <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="1907f-295">您也可以使用科學記號標記法。</span><span class="sxs-lookup"><span data-stu-id="1907f-295">You may also use scientific notation.</span></span> <span data-ttu-id="1907f-296">例如，`+1.e17` 是有效的值。</span><span class="sxs-lookup"><span data-stu-id="1907f-296">For example, `+1.e17` is a valid value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1907f-297">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1907f-297">See also</span></span>

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [<span data-ttu-id="1907f-298">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="1907f-298">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="1907f-299">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="1907f-299">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="1907f-300">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="1907f-300">How-to Topics</span></span>](geometries-how-to-topics.md)
