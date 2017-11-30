---
title: "在 Visual Basic 中建立和使用元件"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 453d341961207dd851136aa47a52759b0841424d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="creating-and-using-components-in-visual-basic"></a><span data-ttu-id="ab053-102">在 Visual Basic 中建立和使用元件</span><span class="sxs-lookup"><span data-stu-id="ab053-102">Creating and Using Components in Visual Basic</span></span>
<span data-ttu-id="ab053-103">「元件」是實作 <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> 介面的類別，或直接或間接衍生自可實作 <xref:System.ComponentModel.IComponent> 類別的類別。</span><span class="sxs-lookup"><span data-stu-id="ab053-103">A *component* is a class that implements the <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> interface or that derives directly or indirectly from a class that implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="ab053-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 元件是能重複使用的物件，可以與其他物件互動，並且提供對於外部資源的控制與設計階段支援。</span><span class="sxs-lookup"><span data-stu-id="ab053-104">A [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] component is an object that is reusable, can interact with other objects, and provides control over external resources and design-time support.</span></span>  
  
 <span data-ttu-id="ab053-105">元件的一項重要特色是它們可以設計，這表示類別如果是元件，則可用於 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 整合式開發環境。</span><span class="sxs-lookup"><span data-stu-id="ab053-105">An important feature of components is that they are designable, which means that a class that is a component can be used in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Integrated Development Environment.</span></span> <span data-ttu-id="ab053-106">元件可以新增至工具箱、拖曳並放至表單上，以及在設計介面上操作。</span><span class="sxs-lookup"><span data-stu-id="ab053-106">A component can be added to the Toolbox, dragged and dropped onto a form, and manipulated on a design surface.</span></span> <span data-ttu-id="ab053-107">請注意，元件的基底設計階段支援已內建至 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]，元件開發人員不需要執行任何額外的工作，即可利用基底設計階段功能。</span><span class="sxs-lookup"><span data-stu-id="ab053-107">Notice that base design-time support for components is built into the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]; a component developer does not have to do any additional work to take advantage of the base design-time functionality.</span></span>  
  
 <span data-ttu-id="ab053-108">「控制項」類似於元件，都是可以設計的。</span><span class="sxs-lookup"><span data-stu-id="ab053-108">A *control* is similar to a component, as both are designable.</span></span> <span data-ttu-id="ab053-109">不過，控制項提供使用者介面，而元件則不提供。</span><span class="sxs-lookup"><span data-stu-id="ab053-109">However, a control provides a user interface, while a component does not.</span></span> <span data-ttu-id="ab053-110">控制項必須衍生自基底控制項類別其中之一︰<xref:System.Windows.Forms.Control> 或 <xref:System.Web.UI.Control>。</span><span class="sxs-lookup"><span data-stu-id="ab053-110">A control must derive from one of the base control classes: <xref:System.Windows.Forms.Control> or <xref:System.Web.UI.Control>.</span></span>  
  
## <a name="when-to-create-a-component"></a><span data-ttu-id="ab053-111">建立元件的時機</span><span class="sxs-lookup"><span data-stu-id="ab053-111">When to Create a Component</span></span>  
 <span data-ttu-id="ab053-112">如果您的類別將用在設計介面 (例如 Windows Forms 或 Web Forms 設計工具)，但沒有使用者介面，則它應該是元件，並且實作 <xref:System.ComponentModel.IComponent>，或衍生自直接或間接實作 <xref:System.ComponentModel.IComponent> 的類別。</span><span class="sxs-lookup"><span data-stu-id="ab053-112">If your class will be used on a design surface (such as the Windows Forms or Web Forms Designer) but has no user interface, it should be a component and implement <xref:System.ComponentModel.IComponent>, or derive from a class that directly or indirectly implements <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="ab053-113"><xref:System.ComponentModel.Component> 和 <xref:System.ComponentModel.MarshalByValueComponent> 類別是 <xref:System.ComponentModel.IComponent> 介面的基底實作。</span><span class="sxs-lookup"><span data-stu-id="ab053-113">The <xref:System.ComponentModel.Component> and <xref:System.ComponentModel.MarshalByValueComponent> classes are base implementations of the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="ab053-114">這些類別的主要差異在於 <xref:System.ComponentModel.Component> 類別是以傳址方式封送處理，而 <xref:System.ComponentModel.IComponent> 是以傳值方式封送處理。</span><span class="sxs-lookup"><span data-stu-id="ab053-114">The main difference between these classes is that the <xref:System.ComponentModel.Component> class is marshaled by reference, while <xref:System.ComponentModel.IComponent> is marshaled by value.</span></span> <span data-ttu-id="ab053-115">下列清單為實作者提供廣泛的指導方針。</span><span class="sxs-lookup"><span data-stu-id="ab053-115">The following list provides broad guidelines for implementers.</span></span>  
  
-   <span data-ttu-id="ab053-116">如果您的元件需要以傳址方式封送處理，則衍生自 <xref:System.ComponentModel.Component>。</span><span class="sxs-lookup"><span data-stu-id="ab053-116">If your component needs to be marshaled by reference, derive from <xref:System.ComponentModel.Component>.</span></span>  
  
-   <span data-ttu-id="ab053-117">如果您的元件需要以傳值方式封送處理，則衍生自 <xref:System.ComponentModel.MarshalByValueComponent>。</span><span class="sxs-lookup"><span data-stu-id="ab053-117">If your component needs to be marshaled by value, derive from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
-   <span data-ttu-id="ab053-118">如果您的元件因為單一繼承而不能衍生自其中一個基底實作，請實作 <xref:System.ComponentModel.IComponent>。</span><span class="sxs-lookup"><span data-stu-id="ab053-118">If your component cannot derive from one of the base implementations due to single inheritance, implement <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="ab053-119">如需設計階段支援的詳細資訊，請參閱[元件的設計階段屬性](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)和[擴充設計階段支援](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)。</span><span class="sxs-lookup"><span data-stu-id="ab053-119">For more information about design-time support, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3) and [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span></span>  
  
## <a name="component-classes"></a><span data-ttu-id="ab053-120">元件類別</span><span class="sxs-lookup"><span data-stu-id="ab053-120">Component Classes</span></span>  
 <span data-ttu-id="ab053-121"><xref:System.ComponentModel> 命名空間提供類別，用來實作元件和控制項的執行階段和設計階段行為。</span><span class="sxs-lookup"><span data-stu-id="ab053-121">The <xref:System.ComponentModel> namespace provides classes that are used to implement the run-time and design-time behavior of components and controls.</span></span> <span data-ttu-id="ab053-122">此命名空間包含基底類別和介面，以便實作屬性和類型轉換器、繫結至資料來源，以及授權元件。</span><span class="sxs-lookup"><span data-stu-id="ab053-122">This namespace includes the base classes and interfaces for implementing attributes and type converters, binding to data sources, and licensing components.</span></span>  
  
 <span data-ttu-id="ab053-123">核心元件類別包括︰</span><span class="sxs-lookup"><span data-stu-id="ab053-123">The core component classes are:</span></span>  
  
-   <span data-ttu-id="ab053-124"><xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="ab053-124"><xref:System.ComponentModel.Component>.</span></span> <span data-ttu-id="ab053-125"><xref:System.ComponentModel.IComponent> 介面的基底實作。</span><span class="sxs-lookup"><span data-stu-id="ab053-125">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="ab053-126">這個類別可在應用程式之間共用物件。</span><span class="sxs-lookup"><span data-stu-id="ab053-126">This class enables object sharing between applications.</span></span>  
  
-   <span data-ttu-id="ab053-127"><xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="ab053-127"><xref:System.ComponentModel.MarshalByValueComponent>.</span></span> <span data-ttu-id="ab053-128"><xref:System.ComponentModel.IComponent> 介面的基底實作。</span><span class="sxs-lookup"><span data-stu-id="ab053-128">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span>  
  
-   <span data-ttu-id="ab053-129"><xref:System.ComponentModel.Container>.</span><span class="sxs-lookup"><span data-stu-id="ab053-129"><xref:System.ComponentModel.Container>.</span></span> <span data-ttu-id="ab053-130"><xref:System.ComponentModel.IContainer> 介面的基底實作。</span><span class="sxs-lookup"><span data-stu-id="ab053-130">The base implementation for the <xref:System.ComponentModel.IContainer> interface.</span></span> <span data-ttu-id="ab053-131">這個類別會封裝零個或更多元件。</span><span class="sxs-lookup"><span data-stu-id="ab053-131">This class encapsulates zero or more components.</span></span>  
  
 <span data-ttu-id="ab053-132">用於元件授權的部分類別包括︰</span><span class="sxs-lookup"><span data-stu-id="ab053-132">Some of the classes used for component licensing are:</span></span>  
  
-   <span data-ttu-id="ab053-133"><xref:System.ComponentModel.License>.</span><span class="sxs-lookup"><span data-stu-id="ab053-133"><xref:System.ComponentModel.License>.</span></span> <span data-ttu-id="ab053-134">所有授權的抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="ab053-134">The abstract base class for all licenses.</span></span> <span data-ttu-id="ab053-135">授權是授與給元件的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab053-135">A license is granted to a specific instance of a component.</span></span>  
  
-   <span data-ttu-id="ab053-136"><xref:System.ComponentModel.LicenseManager>.</span><span class="sxs-lookup"><span data-stu-id="ab053-136"><xref:System.ComponentModel.LicenseManager>.</span></span> <span data-ttu-id="ab053-137">提供屬性和方法以新增授權至元件，以及管理 <xref:System.ComponentModel.LicenseProvider>。</span><span class="sxs-lookup"><span data-stu-id="ab053-137">Provides properties and methods to add a license to a component and to manage a <xref:System.ComponentModel.LicenseProvider>.</span></span>  
  
-   <span data-ttu-id="ab053-138"><xref:System.ComponentModel.LicenseProvider>.</span><span class="sxs-lookup"><span data-stu-id="ab053-138"><xref:System.ComponentModel.LicenseProvider>.</span></span> <span data-ttu-id="ab053-139">實作授權提供者的抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="ab053-139">The abstract base class for implementing a license provider.</span></span>  
  
-   <span data-ttu-id="ab053-140"><xref:System.ComponentModel.LicenseProviderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ab053-140"><xref:System.ComponentModel.LicenseProviderAttribute>.</span></span> <span data-ttu-id="ab053-141">指定要與類別一起使用的 <xref:System.ComponentModel.LicenseProvider> 類別。</span><span class="sxs-lookup"><span data-stu-id="ab053-141">Specifies the <xref:System.ComponentModel.LicenseProvider> class to use with a class.</span></span>  
  
 <span data-ttu-id="ab053-142">常用於描述和保存元件的類別。</span><span class="sxs-lookup"><span data-stu-id="ab053-142">Classes commonly used for describing and persisting components.</span></span>  
  
-   <span data-ttu-id="ab053-143"><xref:System.ComponentModel.TypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="ab053-143"><xref:System.ComponentModel.TypeDescriptor>.</span></span> <span data-ttu-id="ab053-144">提供元件特性的相關資訊，例如其屬性 (attribute)、屬性 (property) 與事件。</span><span class="sxs-lookup"><span data-stu-id="ab053-144">Provides information about the characteristics for a component, such as its attributes, properties, and events.</span></span>  
  
-   <span data-ttu-id="ab053-145"><xref:System.ComponentModel.EventDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="ab053-145"><xref:System.ComponentModel.EventDescriptor>.</span></span> <span data-ttu-id="ab053-146">提供事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ab053-146">Provides information about an event.</span></span>  
  
-   <span data-ttu-id="ab053-147"><xref:System.ComponentModel.PropertyDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="ab053-147"><xref:System.ComponentModel.PropertyDescriptor>.</span></span> <span data-ttu-id="ab053-148">提供屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ab053-148">Provides information about a property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ab053-149">相關章節</span><span class="sxs-lookup"><span data-stu-id="ab053-149">Related Sections</span></span>  
 [<span data-ttu-id="ab053-150">類別與元件與控制項</span><span class="sxs-lookup"><span data-stu-id="ab053-150">Class vs. Component vs. Control</span></span>](http://msdn.microsoft.com/library/db8b842e-44d9-40cc-a0f8-70fd189632c3)  
 <span data-ttu-id="ab053-151">定義「元件」和「控制項」，並討論它們和類別之間的差異。</span><span class="sxs-lookup"><span data-stu-id="ab053-151">Defines *component* and *control*, and discusses the differences between them and classes.</span></span>  
  
 [<span data-ttu-id="ab053-152">元件撰寫</span><span class="sxs-lookup"><span data-stu-id="ab053-152">Component Authoring</span></span>](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 <span data-ttu-id="ab053-153">開始使用元件的藍圖。</span><span class="sxs-lookup"><span data-stu-id="ab053-153">Roadmap for getting started with components.</span></span>  
  
 [<span data-ttu-id="ab053-154">元件撰寫逐步解說</span><span class="sxs-lookup"><span data-stu-id="ab053-154">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 <span data-ttu-id="ab053-155">提供元件程式設計逐步指示的主題連結。</span><span class="sxs-lookup"><span data-stu-id="ab053-155">Links to topics that provide step-by-step instruction for component programming.</span></span>  
  
 [<span data-ttu-id="ab053-156">元件類別</span><span class="sxs-lookup"><span data-stu-id="ab053-156">Component Classes</span></span>](http://msdn.microsoft.com/library/ce2e5647-e673-4c2b-8125-ffebbd9d71bc)  
 <span data-ttu-id="ab053-157">說明如何使類別成為元件、公開元件功能、控制元件存取權，以及控制如何建立元件執行個體。</span><span class="sxs-lookup"><span data-stu-id="ab053-157">Describes what makes a class a component, ways to expose component functionality, controlling access to components, and controlling how component instances are created.</span></span>  
  
 [<span data-ttu-id="ab053-158">針對控制項和元件撰寫進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="ab053-158">Troubleshooting Control and Component Authoring</span></span>](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="ab053-159">說明如何修正常見問題。</span><span class="sxs-lookup"><span data-stu-id="ab053-159">Explains how to fix common problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab053-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab053-160">See Also</span></span>  
 [<span data-ttu-id="ab053-161">如何： 存取 Windows Form 中的設計階段支援</span><span class="sxs-lookup"><span data-stu-id="ab053-161">How to: Access Design-Time Support in Windows Forms</span></span>](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)  
 [<span data-ttu-id="ab053-162">如何： 擴充的外觀和行為的設計模式中的控制項</span><span class="sxs-lookup"><span data-stu-id="ab053-162">How to: Extend the Appearance and Behavior of Controls in Design Mode</span></span>](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b)  
 [<span data-ttu-id="ab053-163">如何：在設計模式中執行控制項的自訂初始設定</span><span class="sxs-lookup"><span data-stu-id="ab053-163">How to: Perform Custom Initialization for Controls in Design Mode</span></span>](http://msdn.microsoft.com/library/914eaa03-092f-4556-9160-b8a2a40641d9)
