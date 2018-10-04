---
title: Windows Form 控制項中的屬性
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 37db3f16a17acc7f3a6e594bd284ba368801e70a
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48262887"
---
# <a name="properties-in-windows-forms-controls"></a>Windows Form 控制項中的屬性
將 Windows Forms 控制項繼承許多屬性，形成基底類別<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。 這包括屬性，例如<xref:System.Windows.Forms.Control.Font%2A>， <xref:System.Windows.Forms.Control.ForeColor%2A>， <xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.Bounds%2A>， <xref:System.Windows.Forms.Control.ClientRectangle%2A>， <xref:System.Windows.Forms.Control.DisplayRectangle%2A>， <xref:System.Windows.Forms.Control.Enabled%2A>， <xref:System.Windows.Forms.Control.Focused%2A>， <xref:System.Windows.Forms.Control.Height%2A>， <xref:System.Windows.Forms.Control.Width%2A>， <xref:System.Windows.Forms.Control.Visible%2A>， <xref:System.Windows.Forms.Control.AutoSize%2A>，和許多其他因素。 如需繼承屬性的詳細資訊，請參閱<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。  
  
 您可以在控制項中覆寫繼承的屬性，以及定義新的屬性。  
  
## <a name="in-this-section"></a>本節內容  
 [定義屬性](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 示範如何實作自訂控制項或元件的屬性，並且示範如何將屬性整合至設計環境。  
  
 [使用 ShouldSerialize 和 Reset 方法定義預設值](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 示範如何定義自訂控制項或元件的預設屬性值。  
  
 [屬性變更事件](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 描述如何在屬性值變更時，啟用屬性變更通知。  
  
 [如何：公開組成控制項的屬性](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 示範如何在自訂複合控制項中公開組成控制項的屬性。  
  
 [自訂控制項中的方法實作](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 描述如何在自訂控制項和元件中實作方法。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.UserControl>  
 記錄基底類別以實作複合控制項。  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 記錄屬性，指定<xref:System.ComponentModel.TypeConverter>来用於自訂的屬性類型。  
  
 <xref:System.ComponentModel.EditorAttribute>  
 記錄屬性，指定<xref:System.Drawing.Design.UITypeEditor>来用於自訂的屬性。  
  
## <a name="related-sections"></a>相關章節  
 [Windows Forms 控制項中的屬性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 描述可以套用至屬性 (Property) 或您的自訂控制項和元件之其他成員的屬性 (Attribute)。  
  
 [元件的設計階段屬性](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 列出要套用至元件和控制項的中繼資料屬性，以便在設計階段於視覺設計工具中正確顯示這些屬性。  
  
 [擴充設計階段支援](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 描述如何實作類別，例如提供設計階段支援的編輯器和設計工具。
