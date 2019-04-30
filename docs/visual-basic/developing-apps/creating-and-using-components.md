---
title: 在 Visual Basic 中建立和使用元件
ms.date: 07/20/2015
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
ms.openlocfilehash: ca336e2ffa3831167088d92bfca017ce2226d8a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014319"
---
# <a name="creating-and-using-components-in-visual-basic"></a>在 Visual Basic 中建立和使用元件
「元件」是實作 <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> 介面的類別，或直接或間接衍生自可實作 <xref:System.ComponentModel.IComponent> 類別的類別。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 元件是能重複使用的物件，可以與其他物件互動，並且提供對於外部資源的控制與設計階段支援。  
  
 元件的一項重要功能是可以進行設計，這表示類別如果是元件，則可用於 Visual Studio 整合式開發環境。 元件可以新增至工具箱、拖曳並放至表單上，以及在設計介面上操作。 請注意，元件的基底設計階段支援已內建至 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]，元件開發人員不需要執行任何額外的工作，即可利用基底設計階段功能。  
  
 「控制項」類似於元件，都是可以設計的。 不過，控制項提供使用者介面，而元件則不提供。 控制項必須衍生自基底控制項類別其中之一︰<xref:System.Windows.Forms.Control> 或 <xref:System.Web.UI.Control>。  
  
## <a name="when-to-create-a-component"></a>建立元件的時機  
 如果您的類別將用在設計介面 (例如 Windows Forms 或 Web Forms 設計工具)，但沒有使用者介面，則它應該是元件，並且實作 <xref:System.ComponentModel.IComponent>，或衍生自直接或間接實作 <xref:System.ComponentModel.IComponent> 的類別。  
  
 <xref:System.ComponentModel.Component> 和 <xref:System.ComponentModel.MarshalByValueComponent> 類別是 <xref:System.ComponentModel.IComponent> 介面的基底實作。 這些類別的主要差異在於 <xref:System.ComponentModel.Component> 類別是以傳址方式封送處理，而 <xref:System.ComponentModel.IComponent> 是以傳值方式封送處理。 下列清單為實作者提供廣泛的指導方針。  
  
- 如果您的元件需要以傳址方式封送處理，則衍生自 <xref:System.ComponentModel.Component>。  
  
- 如果您的元件需要以傳值方式封送處理，則衍生自 <xref:System.ComponentModel.MarshalByValueComponent>。  
  
- 如果您的元件因為單一繼承而不能衍生自其中一個基底實作，請實作 <xref:System.ComponentModel.IComponent>。  
  
## <a name="component-classes"></a>元件類別  
 <xref:System.ComponentModel> 命名空間提供類別，用來實作元件和控制項的執行階段和設計階段行為。 此命名空間包含基底類別和介面，以便實作屬性和類型轉換器、繫結至資料來源，以及授權元件。  
  
 核心元件類別包括︰  
  
- <xref:System.ComponentModel.Component>. <xref:System.ComponentModel.IComponent> 介面的基底實作。 這個類別可在應用程式之間共用物件。  
  
- <xref:System.ComponentModel.MarshalByValueComponent>. <xref:System.ComponentModel.IComponent> 介面的基底實作。  
  
- <xref:System.ComponentModel.Container>. <xref:System.ComponentModel.IContainer> 介面的基底實作。 這個類別會封裝零個或更多元件。  
  
 用於元件授權的部分類別包括︰  
  
- <xref:System.ComponentModel.License>. 所有授權的抽象基底類別。 授權是授與給元件的特定執行個體。  
  
- <xref:System.ComponentModel.LicenseManager>. 提供屬性和方法以新增授權至元件，以及管理 <xref:System.ComponentModel.LicenseProvider>。  
  
- <xref:System.ComponentModel.LicenseProvider>. 實作授權提供者的抽象基底類別。  
  
- <xref:System.ComponentModel.LicenseProviderAttribute>. 指定要與類別一起使用的 <xref:System.ComponentModel.LicenseProvider> 類別。  
  
 常用於描述和保存元件的類別。  
  
- <xref:System.ComponentModel.TypeDescriptor>. 提供元件特性的相關資訊，例如其屬性 (attribute)、屬性 (property) 與事件。  
  
- <xref:System.ComponentModel.EventDescriptor>. 提供事件的相關資訊。  
  
- <xref:System.ComponentModel.PropertyDescriptor>. 提供屬性的相關資訊。  
  
## <a name="related-sections"></a>相關章節  
 [針對控制項和元件撰寫進行疑難排解](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 說明如何修正常見問題。  
  
## <a name="see-also"></a>另請參閱

- [如何：在 Windows Forms 中存取設計階段支援](../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
