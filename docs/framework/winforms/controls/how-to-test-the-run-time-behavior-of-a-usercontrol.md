---
title: "如何：測試 UserControl 的執行階段行為"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ccf386acd50338f1743bbf8f6be38b3267a7103
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>如何：測試 UserControl 的執行階段行為
當您開發<xref:System.Windows.Forms.UserControl>，您要測試其執行階段行為。 您可以建立個別的 Windows 架構應用程式專案，並將您的控制項上測試表單，但此程序，是很方便。 更快且更容易的方式是使用**UserControl Test Container** Visual Studio 所提供。 這個測試容器啟動直接從您的 Windows 控制項程式庫專案。  
  
> [!IMPORTANT]
>  載入測試容器您<xref:System.Windows.Forms.UserControl>，控制項必須有至少一個公用建構函式。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
> [!NOTE]
>  Visual c + + 控制項無法使用測試**UserControl Test Container**。  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a>若要測試 UserControl 的執行階段行為  
  
1.  建立 Windows 控制項程式庫專案，稱為**TestContainerExample**。 如需詳細資訊，請參閱[Windows 控制項程式庫範本](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4)。  
  
2.  在**Windows Form 設計工具**，拖曳<xref:System.Windows.Forms.Label>控制項從**工具箱**拖曳至控制項的設計介面。  
  
3.  按 F5 以建置專案並執行**UserControl Test Container**。 測試容器會顯示您<xref:System.Windows.Forms.UserControl>中**預覽**窗格。  
  
4.  選取<xref:System.Windows.Forms.Control.BackColor%2A>屬性顯示在<xref:System.Windows.Forms.PropertyGrid>右邊的控制項**預覽**窗格。 變更其值以`ControlDark`。 請注意，控制項就會變更為較深的色彩。 請嘗試更換其他屬性值，然後觀察您的控制項上的效果。  
  
5.  按一下**停駐填滿使用者控制項**下方的核取方塊**預覽**窗格。 觀察控制項會調整大小以填滿窗格。 調整測試容器的大小，並觀察，調整控制項大小的窗格。  
  
6.  關閉測試容器。  
  
7.  將另一個使用者控制項加入**TestContainerExample**專案。 如需詳細資訊，請參閱[NIB： 如何： 加入現有項目加入至專案](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)。  
  
8.  在**Windows Form 設計工具**，拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至控制項的設計介面。  
  
9. 按 F5 以建置專案並執行測試容器。  
  
10. 按一下**選取的使用者控制項**<xref:System.Windows.Forms.ComboBox>兩個使用者控制項之間切換。  
  
## <a name="testing-user-controls-from-another-project"></a>從另一個專案的測試使用者控制項  
 您可以在目前專案的測試容器測試與其他專案的使用者控制項。  
  
#### <a name="to-test-user-controls-from-another-project"></a>若要測試使用者控制項，從另一個專案  
  
1.  建立 Windows 控制項程式庫專案，稱為**TestContainerExample2**。 如需詳細資訊，請參閱[Windows 控制項程式庫範本](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4)。  
  
2.  在**Windows Form 設計工具**，拖曳<xref:System.Windows.Forms.RadioButton>控制項從**工具箱**拖曳至控制項的設計介面。  
  
3.  按 F5 以建置專案並執行測試容器。 測試容器會顯示您<xref:System.Windows.Forms.UserControl>中**預覽**窗格。  
  
4.  按一下**負載** 按鈕。  
  
5.  在**開啟**對話方塊方塊中，瀏覽至**TestContainerExample**.dll，建置於中先前的程序。 選取**TestContainerExample**.dll 和按一下**開啟**按鈕以載入使用者控制項  
  
6.  使用**選取的使用者控制項**<xref:System.Windows.Forms.ComboBox>切換兩個使用者控制項，從**TestContainerExample**專案。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.UserControl>  
 [操作說明：撰寫複合控制項](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [逐步解說：使用 Visual Basic 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [逐步解說：使用 Visual C# 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [使用者控制項設計工具](http://msdn.microsoft.com/en-us/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)
