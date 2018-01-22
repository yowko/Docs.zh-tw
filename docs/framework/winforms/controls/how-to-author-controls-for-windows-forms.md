---
title: "如何：撰寫 Windows Forms 的控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 125e3f1c32c5186cce0b28aa3f8d1eff1ef95a09
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-author-controls-for-windows-forms"></a>如何：撰寫 Windows Forms 的控制項
控制項所代表使用者與程式之間的圖形化連結。 控制項可以提供或處理資料、接受使用者輸入、回應事件，或執行任意數目的其他功能來連接使用者與應用程式。 因為控制項本質上是具有圖形化介面的元件，所以可以提供元件所執行的任何功能，以及提供使用者互動。 建立控制項以提供特定用途，而編寫控制項只是另一個程式設計工作。 記住這點，下列步驟代表控制項撰寫處理序的概觀。 連結可提供各個步驟的其他資訊。  
  
> [!NOTE]
>  如果您想要撰寫自訂控制項以在 Web Forms 上使用，請參閱[開發自訂 ASP.NET 伺服器控制項](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-author-a-control"></a>撰寫控制項  
  
1.  決定您希望控制項完成的事項，或在您的應用程式中扮演的角色。 應考量的因素包括：  
  
    -   您需要何種圖形化介面？  
  
    -   此控制項將處理哪些特定的使用者互動？  
  
    -   您需要的功能是由任何現有控制項提供嗎？  
  
    -   您可以藉由結合數個 Windows Forms 控制項來取得您需要的功能嗎？  
  
2.  如果您需要控制項的物件模型，請決定如何將功能散發於整個物件模型，以及在控制項與任何子物件之間分配功能。 如果您要規劃複雜的控制項，或想要併入多個功能，物件模型可能很有用。  
  
3.  決定您需要的控制項類型 (例如，使用者控制項、自訂控制項、繼承的 Windows Forms 控制項)。 如需詳細資訊，請參閱[控制項類型建議](../../../../docs/framework/winforms/controls/control-type-recommendations.md)和[各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)。  
  
4.  將功能表示為控制項的屬性、方法和事件及其子物件或附屬結構，並指派適當的存取層級 (例如，公用、受保護等等)。  
  
5.  如果您需要自訂控制項的繪製，請為它新增程式碼。 如需詳細資訊，請參閱[自訂控制項繪製和轉譯](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)。  
  
6.  如果您的控制項是繼承自<xref:System.Windows.Forms.UserControl>，您可以藉由建置控制項專案中執行測試其執行階段行為**UserControl 測試容器**。 如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
7.  您也可以建立新專案 (例如 Windows 應用程式) 並將它放入容器中，來測試您的控制項並進行偵錯。 此處理序的示範在[逐步解說：使用 Visual Basic 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)中。  
  
8.  當您新增每項功能時，將功能新增至測試專案，以執行新功能。  
  
9. 重複執行，並調整設計。  
  
10. 封裝並部署您的控制項。 如需詳細資訊，請參閱[部署應用程式、服務和元件](https://msdn.microsoft.com/library/wtzawcsz)。  
  
## <a name="see-also"></a>請參閱  
 [逐步解說：使用 Visual Basic 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [逐步解說：使用 Visual Basic 繼承自 Windows Forms 控制項](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [操作說明：繼承自 UserControl 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [操作說明：繼承自 Control 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [操作說明：繼承自現有的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [操作說明：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
