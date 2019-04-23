---
title: XAML 2009 語言功能
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: 05f811cd0d95f7605963dae851430fb6bf0e9f7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162276"
---
# <a name="xaml-2009-language-features"></a><span data-ttu-id="efe4d-102">XAML 2009 語言功能</span><span class="sxs-lookup"><span data-stu-id="efe4d-102">XAML 2009 Language Features</span></span>
<span data-ttu-id="efe4d-103">XAML 2009 是新 XAML 語言功能的縮寫詞彙，可擴充現有的 XAML 語言規格。</span><span class="sxs-lookup"><span data-stu-id="efe4d-103">XAML 2009 is the shorthand term for new XAML language features that extend the existing XAML language specification.</span></span> <span data-ttu-id="efe4d-104">XAML 2009 引進了數個新的指示詞和建構。</span><span class="sxs-lookup"><span data-stu-id="efe4d-104">XAML 2009 introduces several new directives and constructs.</span></span> <span data-ttu-id="efe4d-105">其中包括[X:arguments 指示詞](x-arguments-directive.md); [X:factorymethod 指示詞](x-factorymethod-directive.md); [X:reference 標記延伸](x-reference-markup-extension.md); [X:typearguments 指示詞](x-typearguments-directive.md); 和通用語言基本類型的內建類型 (例如`x:Char`)。</span><span class="sxs-lookup"><span data-stu-id="efe4d-105">These include the [x:Arguments Directive](x-arguments-directive.md); the [x:FactoryMethod Directive](x-factorymethod-directive.md); the [x:Reference Markup Extension](x-reference-markup-extension.md); the [x:TypeArguments Directive](x-typearguments-directive.md); and built-in types for common language primitives (for example `x:Char`).</span></span>  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a><span data-ttu-id="efe4d-106">WPF 和 Visual Studio 中的 XAML 2009 支援</span><span class="sxs-lookup"><span data-stu-id="efe4d-106">XAML 2009 Support in WPF and Visual Studio</span></span>  
 <span data-ttu-id="efe4d-107">在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未編譯 WPF 標記的 XAML。</span><span class="sxs-lookup"><span data-stu-id="efe4d-107">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="efe4d-108">編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 語言關鍵字和功能。</span><span class="sxs-lookup"><span data-stu-id="efe4d-108">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>  
  
 <span data-ttu-id="efe4d-109">請注意，對於 CLR 類型和類型系統，在 WPF 中載入鬆散 XAML 的現有技術，可能也會有比編譯標記的 XAML 更嚴格的安全性和存取限制。</span><span class="sxs-lookup"><span data-stu-id="efe4d-109">Note that existing techniques for loading loose XAML in WPF also have possible security and access restrictions to CLR types and the type system that are more restrictive than for markup-compiled XAML.</span></span> <span data-ttu-id="efe4d-110">如需詳細資訊，請參閱 [安全性 (WPF)](../wpf/security-wpf.md) 或 [WPF 安全性策略 - 平台安全性](../wpf/wpf-security-strategy-platform-security.md)。</span><span class="sxs-lookup"><span data-stu-id="efe4d-110">For more information, see [Security (WPF)](../wpf/security-wpf.md) or [WPF Security Strategy - Platform Security](../wpf/wpf-security-strategy-platform-security.md).</span></span>  
  
 <span data-ttu-id="efe4d-111">XAML 2009 也引進了額外的功能，可修改先前的 XAML 2006 建構或修改基本標記形式。</span><span class="sxs-lookup"><span data-stu-id="efe4d-111">XAML 2009 also introduces additional features that either modify the previous XAML 2006 constructs or that modify the basic markup forms.</span></span>  
  
### <a name="xkey-as-an-object-element"></a><span data-ttu-id="efe4d-112">x:Key 做為物件項目</span><span class="sxs-lookup"><span data-stu-id="efe4d-112">x:Key as an Object Element</span></span>  
 <span data-ttu-id="efe4d-113">XAML 2009 可支援 `x:Key` 做為物件 (具有物件項目值的屬性 (Property) 項目)，但 XAML 2006 僅支援 `x:Key` 做為屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="efe4d-113">XAML 2009 can support `x:Key` as an object (a property element that has object element value); however, XAML 2006 only supported `x:Key` as an attribute.</span></span> <span data-ttu-id="efe4d-114">請參閱 [x:Key Directive](x-key-directive.md)的＜XAML 2009＞一節。</span><span class="sxs-lookup"><span data-stu-id="efe4d-114">See the "XAML 2009" section of [x:Key Directive](x-key-directive.md).</span></span>  
  
### <a name="xmlns-on-property-elements"></a><span data-ttu-id="efe4d-115">屬性項目上的 xmlns</span><span class="sxs-lookup"><span data-stu-id="efe4d-115">xmlns on Property Elements</span></span>  
 <span data-ttu-id="efe4d-116">XAML 2009 可支援屬性項目的 XAML 命名空間 (xmlns) 定義，但 XAML 2006 僅支援物件項目上的 xmlns 定義。</span><span class="sxs-lookup"><span data-stu-id="efe4d-116">XAML 2009 can support XAML namespace (xmlns) definitions on property elements; however, XAML 2006 only supports xmlns definitions on object elements.</span></span>  
  
### <a name="event-attributes"></a><span data-ttu-id="efe4d-117">事件屬性</span><span class="sxs-lookup"><span data-stu-id="efe4d-117">Event Attributes</span></span>  
 <span data-ttu-id="efe4d-118">針對事件所支援的屬性，XAML 2006 會假定標記編譯與將事件送出到標記編譯有關。</span><span class="sxs-lookup"><span data-stu-id="efe4d-118">For attributes that are backed by events, XAML 2006 presumes that markup compilation is involved and submits the events to markup compilation.</span></span> <span data-ttu-id="efe4d-119">XAML 2009 支援類似標記延伸的標記形式，這會將事件連接延遲到 XAML 的執行階段剖析和載入。</span><span class="sxs-lookup"><span data-stu-id="efe4d-119">XAML 2009 supports a markup form that resembles a markup extension, which defers the event wiring until run-time parsing and loading of the XAML.</span></span> <span data-ttu-id="efe4d-120">不過，WPF 應用程式和 WPF UI 的 XAML 情節通常不會使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="efe4d-120">However, WPF applications and XAML scenarios for WPF UI generally do not use this capability.</span></span> <span data-ttu-id="efe4d-121">WPF 及其 XAML 2006 實作會使用事件處理常式連接組合進行在 <xref:System.Windows.UIElement> 層級定義的路由事件，並使用其標記編譯器步驟進行大部分的事件屬性處理。</span><span class="sxs-lookup"><span data-stu-id="efe4d-121">WPF and its XAML 2006 implementation uses the combination of event handler wiring for routed events defined at the <xref:System.Windows.UIElement> level and its markup compiler step for much of its event attribute processing.</span></span> <span data-ttu-id="efe4d-122">標記編譯器也會前置處理在 XAML 中找到的任何事件屬性，建置動作會在此 XAML 中宣告使用標記編譯器。</span><span class="sxs-lookup"><span data-stu-id="efe4d-122">The markup compiler also preprocesses any event attributes found in XAML where the build actions declare that the markup compiler is used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe4d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efe4d-123">See also</span></span>

- [<span data-ttu-id="efe4d-124">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="efe4d-124">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
