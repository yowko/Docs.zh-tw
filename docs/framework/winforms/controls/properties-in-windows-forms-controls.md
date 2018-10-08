---
title: Windows Form 控制項中的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 37db3f16a17acc7f3a6e594bd284ba368801e70a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850162"
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="264f1-102">Windows Form 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="264f1-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="264f1-103">將 Windows Forms 控制項繼承許多屬性，形成基底類別<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="264f1-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="264f1-104">這包括屬性，例如<xref:System.Windows.Forms.Control.Font%2A>， <xref:System.Windows.Forms.Control.ForeColor%2A>， <xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.Bounds%2A>， <xref:System.Windows.Forms.Control.ClientRectangle%2A>， <xref:System.Windows.Forms.Control.DisplayRectangle%2A>， <xref:System.Windows.Forms.Control.Enabled%2A>， <xref:System.Windows.Forms.Control.Focused%2A>， <xref:System.Windows.Forms.Control.Height%2A>， <xref:System.Windows.Forms.Control.Width%2A>， <xref:System.Windows.Forms.Control.Visible%2A>， <xref:System.Windows.Forms.Control.AutoSize%2A>，和許多其他因素。</span><span class="sxs-lookup"><span data-stu-id="264f1-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="264f1-105">如需繼承屬性的詳細資訊，請參閱<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="264f1-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="264f1-106">您可以在控制項中覆寫繼承的屬性，以及定義新的屬性。</span><span class="sxs-lookup"><span data-stu-id="264f1-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="264f1-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="264f1-107">In This Section</span></span>  
 [<span data-ttu-id="264f1-108">定義屬性</span><span class="sxs-lookup"><span data-stu-id="264f1-108">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="264f1-109">示範如何實作自訂控制項或元件的屬性，並且示範如何將屬性整合至設計環境。</span><span class="sxs-lookup"><span data-stu-id="264f1-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="264f1-110">使用 ShouldSerialize 和 Reset 方法定義預設值</span><span class="sxs-lookup"><span data-stu-id="264f1-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="264f1-111">示範如何定義自訂控制項或元件的預設屬性值。</span><span class="sxs-lookup"><span data-stu-id="264f1-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="264f1-112">屬性變更事件</span><span class="sxs-lookup"><span data-stu-id="264f1-112">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 <span data-ttu-id="264f1-113">描述如何在屬性值變更時，啟用屬性變更通知。</span><span class="sxs-lookup"><span data-stu-id="264f1-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="264f1-114">如何：公開組成控制項的屬性</span><span class="sxs-lookup"><span data-stu-id="264f1-114">How to: Expose Properties of Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="264f1-115">示範如何在自訂複合控制項中公開組成控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="264f1-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="264f1-116">自訂控制項中的方法實作</span><span class="sxs-lookup"><span data-stu-id="264f1-116">Method Implementation in Custom Controls</span></span>](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 <span data-ttu-id="264f1-117">描述如何在自訂控制項和元件中實作方法。</span><span class="sxs-lookup"><span data-stu-id="264f1-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="264f1-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="264f1-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="264f1-119">記錄基底類別以實作複合控制項。</span><span class="sxs-lookup"><span data-stu-id="264f1-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="264f1-120">記錄屬性，指定<xref:System.ComponentModel.TypeConverter>来用於自訂的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="264f1-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="264f1-121">記錄屬性，指定<xref:System.Drawing.Design.UITypeEditor>来用於自訂的屬性。</span><span class="sxs-lookup"><span data-stu-id="264f1-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="264f1-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="264f1-122">Related Sections</span></span>  
 [<span data-ttu-id="264f1-123">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="264f1-123">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="264f1-124">描述可以套用至屬性 (Property) 或您的自訂控制項和元件之其他成員的屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="264f1-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="264f1-125">元件的設計階段屬性</span><span class="sxs-lookup"><span data-stu-id="264f1-125">Design-Time Attributes for Components</span></span>](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="264f1-126">列出要套用至元件和控制項的中繼資料屬性，以便在設計階段於視覺設計工具中正確顯示這些屬性。</span><span class="sxs-lookup"><span data-stu-id="264f1-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="264f1-127">擴充設計階段支援</span><span class="sxs-lookup"><span data-stu-id="264f1-127">Extending Design-Time Support</span></span>](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="264f1-128">描述如何實作類別，例如提供設計階段支援的編輯器和設計工具。</span><span class="sxs-lookup"><span data-stu-id="264f1-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>
