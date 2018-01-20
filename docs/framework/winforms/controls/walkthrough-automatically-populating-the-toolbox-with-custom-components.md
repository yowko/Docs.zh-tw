---
title: "逐步解說：自動將自訂元件填入工具箱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b60d4ee7908a5ed9dcb3393132ba7d0bd0a6cb5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>逐步解說：自動將自訂元件填入工具箱
如果您的元件會由目前開啟的方案中的專案，會自動將會出現在**工具箱**，而不需要您所需的動作。 您也可以手動填入**工具箱**與使用自訂元件[選擇工具箱項目 對話方塊 (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)，但**工具箱**考慮您的方案中的項目建置輸出具有所有下列特性：  
  
-   實作<xref:System.ComponentModel.IComponent>;  
  
-   沒有<xref:System.ComponentModel.ToolboxItemAttribute>設`false`;  
  
-   沒有<xref:System.ComponentModel.DesignTimeVisibleAttribute>設`false`。  
  
> [!NOTE]
>  **工具箱**未遵循參考鏈結，所以它不會顯示並不是您方案中的專案所建置的項目。  
  
 本逐步解說示範如何自訂元件會自動出現在**工具箱**建置元件之後。 這個逐步解說中所述的工作包括：  
  
-   建立 Windows Form 專案。  
  
-   建立自訂元件。  
  
-   建立自訂元件的執行個體。  
  
-   卸載並重新載入自訂元件。  
  
 當您完成時，您會看到**工具箱**會填入您所建立的元件。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  建立以 Windows 為基礎的應用程式專案，名為 `ToolboxExample`。  
  
     如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  將新元件加入至專案。 呼叫它`DemoComponent`。  
  
     如需詳細資訊，請參閱[NIB： 如何： 加入新的專案項目](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)。  
  
3.  建置專案。  
  
4.  從**工具**功能表上，按一下 **選項**項目。 按一下**一般**下**Windows Form 設計工具**項目，並確定**AutoToolboxPopulate**選項設定為**True**。  
  
## <a name="creating-an-instance-of-a-custom-component"></a>建立自訂元件的執行個體  
 下一個步驟是在表單上建立自訂元件的執行個體。 因為**工具箱**自動帳戶的新元件，這非常容易，只要建立元件或控制項。  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a>若要建立自訂元件的執行個體  
  
1.  開啟專案的表單中**Form 設計工具**。  
  
2.  在**工具箱**，按一下 新索引標籤呼叫**ToolboxExample 元件**。  
  
     一旦您按一下索引標籤，您會看到**DemoComponent**。  
  
    > [!NOTE]
    >  基於效能考量，自動填入內容區域中的元件**工具箱**不會顯示自訂點陣圖與<xref:System.Drawing.ToolboxBitmapAttribute>不支援。 若要顯示的圖示中的自訂元件**工具箱**，使用**選擇工具箱項目**載入您的元件 對話方塊。  
  
3.  您的元件拖曳至表單。  
  
     建立元件的執行個體並將其加入**元件匣**。  
  
## <a name="unloading-and-reloading-a-custom-component"></a>卸載並重新載入自訂元件  
 **工具箱**會考慮在每個元件的載入專案，並卸載專案之後，它會移除專案的元件的參考。  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a>若要試驗的卸載和重新載入元件工具箱上的效果  
  
1.  專案從方案中卸載。  
  
     如需 卸載專案的詳細資訊，請參閱[NIB： 如何： 卸載再重新載入專案](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b)。 如果提示您儲存時，請選擇**是**。  
  
2.  加入新**Windows 應用程式**專案加入方案。 開啟表單中的**設計師**。  
  
     **ToolboxExample 元件**從先前的專案 索引標籤現在會消失。  
  
3.  重新載入`ToolboxExample`專案。  
  
     **ToolboxExample 元件**索引標籤現在隨即再度出現。  
  
## <a name="next-steps"></a>後續步驟  
 本逐步解說會示範**工具箱**考慮專案的元件，但**工具箱**也是會考慮控制項。 實驗您自己的自訂控制項加入和移除控制項的專案，從您的方案。  
  
## <a name="see-also"></a>請參閱  
 [選項對話方塊、 Windows Form 設計工具，一般](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [如何：操作工具箱索引標籤](http://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [選擇工具箱項目對話方塊 (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [將控制項加入 Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)
