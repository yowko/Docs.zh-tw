---
title: "逐步解說：將 ElementHost 控制項複製並貼至另外的 Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 579bce312296d9799f9f7c739f740e2c9111ccff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a>逐步解說：將 ElementHost 控制項複製並貼至另外的 Windows Form
本逐步解說示範如何將 Windows Presentation Foundation (WPF) 控制項從一個 Windows Form 複製到另一個 Windows Form。  
  
 在這個逐步解說中，您將執行下列工作：  
  
-   建立專案。  
  
-   複製 WPF 控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立 Windows Form 專案。  
  
> [!NOTE]
>  裝載 WPF 內容時，只支援 C# 和 Visual Basic 專案。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
-   建立新的 Windows Forms 應用程式專案在 Visual Basic 或 Visual C# 中名為`CopyElementHost`。  
  
## <a name="copying-a-wpf-control"></a>複製 WPF 控制項  
 將 WPF 控制項加入專案之後，您可以將其複製到專案中的其他表單。  
  
#### <a name="to-copy-a-wpf-control"></a>複製 WPF 控制項  
  
1.  將新的 WPF <xref:System.Windows.Controls.UserControl> 專案加入方案。 使用控制項類型的預設名稱 `UserControl1.xaml`。 如需詳細資訊，請參閱[逐步解說： 建立的新 WPF 內容在設計階段的 Windows Form 上](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。  
  
2.  建置專案。  
  
3.  在 Windows Form 設計工具中開啟 `Form1`。  
  
4.  從**工具箱**，拖曳的執行個體`UserControl1`拖曳至表單。  
  
     `UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  
  
5.  在選取 `elementHost1` 時，按 CTRL+C 將其複製到剪貼簿。  
  
6.  將新的 Windows Form 加入專案。 使用表單類型的預設名稱 `Form2`。  
  
7.  當 `Form2` 在 Windows Form 設計工具中開啟時，按 CTRL+V 將 `elementHost1` 的複本貼到表單上。  
  
     由於複製的控制項是 `Form2` 類別的私用欄位，因此該控制項的名稱也是 `elementHost1`。 這樣並不會與 `Form1` 類別中的 `elementHost1` 產生名稱衝突。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [使用 WPF 控制項](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [WPF 設計工具](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
