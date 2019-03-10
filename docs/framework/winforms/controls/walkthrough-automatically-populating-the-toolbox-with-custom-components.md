---
title: 逐步解說：自動填入 [工具箱] 中的以自訂元件
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 8ddb248d2e011714ddc7fb68474f0e92e9ad8b5e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723968"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>逐步解說：自動填入 [工具箱] 中的以自訂元件
如果您的元件會定義目前開啟的方案中的專案，它們會自動顯示，在**工具箱**，您需要採取任何動作。 您可以手動填入**工具箱**以使用您自訂元件[選擇工具箱項目對話方塊 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))，但**工具箱**考慮您的方案中的項目建置輸出具有所有下列特性：  
  
-   實作<xref:System.ComponentModel.IComponent>;  
  
-   沒有<xref:System.ComponentModel.ToolboxItemAttribute>設定為`false`;  
  
-   沒有<xref:System.ComponentModel.DesignTimeVisibleAttribute>設定為`false`。  
  
> [!NOTE]
>  **工具箱**並未遵循參考鏈結，所以它不會顯示由您方案中的專案未建置的項目。  
  
 本逐步解說示範如何自訂元件會自動出現在**工具箱**建立元件之後。 這個逐步解說中所述的工作包括：  
  
-   建立 Windows Forms 專案。  
  
-   建立自訂元件。  
  
-   建立自訂元件的執行個體。  
  
-   卸載並重新載入自訂元件。  
  
 當您完成時，您會看到**工具箱**會填入您所建立的元件。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  建立以 Windows 為基礎的應用程式專案，稱為`ToolboxExample`(**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。  
  
2.  將新元件加入至專案。 稱為 `DemoComponent`。  
  
     如需詳細資訊，請參閱[如何：加入新的專案項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))。  
  
3.  建置專案。  
  
4.  從**工具**功能表上，按一下**選項**項目。 按一下**一般**下方**Windows Form 設計工具**項目，並確定**AutoToolboxPopulate**選項設定為**True**。  
  
## <a name="creating-an-instance-of-a-custom-component"></a>建立自訂元件的執行個體  
 下一個步驟是在表單上建立自訂元件的執行個體。 因為**工具箱**自動帳戶的新元件，這非常簡單，只要建立其他元件或控制項。  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a>若要建立自訂元件的執行個體  
  
1.  開啟專案的表單**Form 設計工具**。  
  
2.  在 **工具箱**，按一下 新索引標籤上，並呼叫**ToolboxExample 元件**。  
  
     一旦您按一下  索引標籤，您會看到**DemoComponent**。  
  
    > [!NOTE]
    >  基於效能考量，自動填入的區域中的元件**工具箱**不會顯示自訂點陣圖，而<xref:System.Drawing.ToolboxBitmapAttribute>不支援。 若要顯示的圖示中的自訂元件**工具箱**，使用**選擇工具箱項目**載入您的元件 對話方塊。  
  
3.  將您的元件拖曳到表單。  
  
     建立並加入至元件的執行個體**元件匣**。  
  
## <a name="unloading-and-reloading-a-custom-component"></a>卸載並重新載入自訂元件  
 **工具箱**會考慮在每個元件的載入專案，並卸載專案時，它會移除專案的元件的參考。  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a>嘗試卸載及重新載入元件的 [工具箱] 上的效果  
  
1.  卸載方案中的專案。  
  
     如需 卸載專案的詳細資訊，請參閱[How to:卸載並重新載入專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100))。 如果提示您儲存時，請選擇**是**。  
  
2.  加入新**Windows 應用程式**專案加入方案。 開啟中的表單**設計工具**。  
  
     **ToolboxExample 元件**現已從先前的專案 索引標籤不見了。  
  
3.  重新載入`ToolboxExample`專案。  
  
     **ToolboxExample 元件**索引標籤現在隨即再度出現。  
  
## <a name="next-steps"></a>後續步驟  
 本逐步解說示範**工具箱**考慮專案的元件，但**工具箱**也是會考慮控制項。 若要試驗您自己的自訂控制項，可新增和移除您的方案中的控制項專案。  
  
## <a name="see-also"></a>另請參閱
- [選項對話方塊、 Windows Form 設計工具、 一般](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))
- [如何：操作工具箱索引標籤](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))
- [選擇工具箱項目對話方塊 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [將控制項加入 Windows Forms](putting-controls-on-windows-forms.md)
