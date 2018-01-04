---
title: "逐步解說：對表單提供標準功能表項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f1b976a0b5e0962cae155f380b17737077c5353
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>逐步解說：對表單提供標準功能表項目
您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。  
  
 本逐步解說示範如何使用<xref:System.Windows.Forms.MenuStrip>控制項來建立標準功能表。 當使用者選取功能表項目，也會回應表單。 在本逐步解說說明下列工作：  
  
-   建立 Windows Form 專案。  
  
-   建立標準功能表。  
  
-   建立<xref:System.Windows.Forms.StatusStrip>控制項。  
  
-   處理功能表項目選取項目。  
  
 當您完成時，您必須具有標準功能表會顯示功能表項目中的選取項目表單<xref:System.Windows.Forms.StatusStrip>控制項。  
  
 若要為單一列出本主題中複製的程式碼，請參閱[How to： 提供標準功能表項目表單](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   若要能夠建立和執行 Windows Form 應用程式專案的電腦上有足夠的權限所在[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]安裝。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  建立 Windows 應用程式專案，稱為**StandardMenuForm**。  
  
     如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  在 Windows Form 設計工具中，選取的表單。  
  
## <a name="creating-a-standard-menu"></a>建立標準功能表  
 Windows Form 設計工具可以自動填入<xref:System.Windows.Forms.MenuStrip>具有標準功能表項目控制項。  
  
#### <a name="to-create-a-standard-menu"></a>建立標準功能表  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至表單。  
  
2.  按一下<xref:System.Windows.Forms.MenuStrip>控制項的智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 並選取**插入標準項目**。  
  
     <xref:System.Windows.Forms.MenuStrip>標準功能表項目填入控制項。  
  
3.  按一下**檔案**功能表項目即可查看其預設功能表項目和對應的圖示。  
  
## <a name="creating-a-statusstrip-control"></a>建立 StatusStrip 控制項  
 使用<xref:System.Windows.Forms.StatusStrip>控制項來顯示 Windows Form 應用程式的狀態。 在目前的範例中，使用者所選取的功能表項目都會顯示在<xref:System.Windows.Forms.StatusStrip>控制項。  
  
#### <a name="to-create-a-statusstrip-control"></a>若要建立 StatusStrip 控制項  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.StatusStrip>控制項拖曳至表單。  
  
     <xref:System.Windows.Forms.StatusStrip>控制項自動停駐於表單的下方。  
  
2.  按一下<xref:System.Windows.Forms.StatusStrip>控制項的下拉式按鈕，然後選取**statuslabel 設**新增<xref:System.Windows.Forms.ToolStripStatusLabel>控制權傳輸至<xref:System.Windows.Forms.StatusStrip>控制項。  
  
## <a name="handling-item-selection"></a>處理的項目選取  
 處理<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件回應使用者選取功能表項目時。  
  
#### <a name="to-handle-item-selection"></a>若要處理的項目選取  
  
1.  按一下**檔案**功能表項目，您在 「 建立標準功能表區段。  
  
2.  在**屬性**視窗中，按一下 **事件**。  
  
3.  按兩下<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件。  
  
     Windows Form 設計工具產生的事件處理常式<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>事件。  
  
4.  此事件處理常式中插入下列程式碼。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  插入`UpdateStatus`至表單的公用程式方法定義。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a>檢查點  
  
#### <a name="to-test-your-form"></a>若要測試您的表單  
  
1.  按 F5 編譯和執行您的表單。  
  
2.  按一下**檔案**開啟功能表的功能表項目。  
  
3.  在**檔案**功能表上，按一下其中一個項目，即可選取它。  
  
     <xref:System.Windows.Forms.StatusStrip>控制項會顯示選取的項目。  
  
## <a name="next-steps"></a>後續步驟  
 在本逐步解說中，您已建立具有標準功能表的表單。 您可以使用<xref:System.Windows.Forms.ToolStrip>系列用於許多其他用途的控制項：  
  
-   建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。 如需詳細資訊，請參閱[ContextMenu 元件概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。  
  
-   建立多個文件介面 (MDI) 表單上具有停駐<xref:System.Windows.Forms.ToolStrip>控制項。 如需詳細資訊，請參閱[逐步解說： 使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。  
  
-   提供您<xref:System.Windows.Forms.ToolStrip>控制項專業外觀。 如需詳細資訊，請參閱[How to： 設定應用程式的 ToolStrip 產生器](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [MenuStrip 控制項](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
