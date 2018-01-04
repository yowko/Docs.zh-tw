---
title: "使用 .NET Framework 開發自訂的 Windows Form 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2f15dc4bb3bd4a6d1163823509f0f2c2bf2c11a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a>使用 .NET Framework 開發自訂的 Windows Form 控制項
Windows Form 控制項是可重複使用的元件，這些控制項可封裝使用者介面功能，並可用於用戶端 Windows 應用程式。 Windows Form 不僅提供許多立即可用的控制項，也提供用以開發您自己的控制項的基礎結構。 您可以結合現有的控制項、擴充現有的控制項，或撰寫您自己的自訂控制項。 本節提供背景資訊和範例，以協助您開發 Windows Form 控制項。  
  
## <a name="in-this-section"></a>本節內容  
 [在 Windows Forms 中使用控制項的概觀](../../../../docs/framework/winforms/controls/overview-of-using-controls-in-windows-forms.md)  
 重點說明在 Windows Forms 應用程式中使用控制項的基本項目。  
  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 描述可以使用 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間撰寫之各種不同的自訂控制項。  
  
 [Windows Forms 控制項開發的基本概念](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)  
 討論開發 Windows Form 控制項的第一個步驟。  
  
 [Windows Forms 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 示範如何將屬性加入 Windows Form 控制項。  
  
 [Windows Forms 控制項中的事件](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 示範如何在 Windows Form 控制項中處理及定義事件。  
  
 [Windows Forms 控制項中的屬性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 描述可以套用至屬性 (Property) 或您的自訂控制項和元件之其他成員的屬性 (Attribute)。  
  
 [自訂控制項繪製和轉譯](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 示範如何自訂控制項的外觀。  
  
 [Windows Forms 控制項中的配置](../../../../docs/framework/winforms/controls/layout-in-windows-forms-controls.md)  
 示範如何為控制項和表單建立複雜的配置。  
  
 [Windows Forms 控制項中的多執行緒](../../../../docs/framework/winforms/controls/multithreading-in-windows-forms-controls.md)  
 示範如何實作多執行緒的控制項。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 描述這個類別，並且提供其所有成員的連結。  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 描述這個類別，並且提供其所有成員的連結。  
  
## <a name="related-sections"></a>相關章節  
 [元件的設計階段屬性](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 列出要套用至元件和控制項的中繼資料屬性，以便在設計階段於視覺設計工具中正確顯示這些屬性。  
  
 [擴充設計階段支援](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 描述如何實作類別，例如提供設計階段支援的編輯器和設計工具。  
  
 [如何：授權元件和控制項](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)  
 描述如何在您的控制項或元件中實作授權。  
  
 另請參閱[在設計階段開發 Windows Forms 控制項](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\))。
