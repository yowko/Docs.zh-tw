---
title: "如何：將面板加入至 StatusBar 控制項"
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
- cpp
helpviewer_keywords:
- panels [Windows Forms], status bars
- status bars [Windows Forms], adding panels
- StatusBar control [Windows Forms], adding panels
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96fbfc86183afef047d210fbc13a0944f2b209b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a><span data-ttu-id="7c9ce-102">如何：將面板加入至 StatusBar 控制項</span><span class="sxs-lookup"><span data-stu-id="7c9ce-102">How to: Add Panels to a StatusBar Control</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="7c9ce-103"><xref:System.Windows.Forms.StatusStrip>和<xref:System.Windows.Forms.ToolStripStatusLabel>控制項取代，並將功能加入至<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項是被保留為回溯相容性及未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="7c9ce-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="7c9ce-104">可程式化的區域內[StatusBar 控制項](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md)控制項所組成的執行個體<xref:System.Windows.Forms.StatusBarPanel>類別。</span><span class="sxs-lookup"><span data-stu-id="7c9ce-104">The programmable area within a [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) control consists of instances of the <xref:System.Windows.Forms.StatusBarPanel> class.</span></span> <span data-ttu-id="7c9ce-105">新增這些新增項目透過<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="7c9ce-105">These are added through additions to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> class.</span></span>  
  
### <a name="to-add-panels-to-a-status-bar"></a><span data-ttu-id="7c9ce-106">若要將面板加入狀態列</span><span class="sxs-lookup"><span data-stu-id="7c9ce-106">To add panels to a status bar</span></span>  
  
1.  <span data-ttu-id="7c9ce-107">在程序，建立狀態列面板藉由加入<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>。</span><span class="sxs-lookup"><span data-stu-id="7c9ce-107">In a procedure, create status-bar panels by adding them to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span> <span data-ttu-id="7c9ce-108">指定屬性設定為個別的面板，您可以使用其索引通過<xref:System.Windows.Forms.StatusBar.Panels%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="7c9ce-108">Specify property settings for individual panels by using its index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property.</span></span>  
  
     <span data-ttu-id="7c9ce-109">在下列程式碼範例中，將路徑設定圖示的位置是**我的文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="7c9ce-109">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="7c9ce-110">使用這個位置是因為您可以假設執行 Windows 作業系統的大部分電腦都會包含此資料夾。</span><span class="sxs-lookup"><span data-stu-id="7c9ce-110">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="7c9ce-111">選擇此位置也可讓使用者以最少的系統存取層級可安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c9ce-111">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="7c9ce-112">下列範例要求的表單具有<xref:System.Windows.Forms.StatusBar>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="7c9ce-112">The following example requires a form with a <xref:System.Windows.Forms.StatusBar> control already added.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7c9ce-113"><xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>是以零為起始的集合，因此應視情況繼續執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c9ce-113">The <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> is a zero-based collection, so code should proceed accordingly.</span></span>  
  
    ```vb  
    Public Sub CreateStatusBarPanels()  
    ' Create panels and set text property.  
       StatusBar1.Panels.Add("One")  
       StatusBar1.Panels.Add("Two")  
       StatusBar1.Panels.Add("Three")  
    ' Set properties of StatusBar panels.  
    ' Set AutoSize property of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(1).AutoSize = StatusBarPanelAutoSize.Contents  
       StatusBar1.Panels(2).AutoSize = StatusBarPanelAutoSize.Contents  
    ' Set BorderStyle property of panels.  
       StatusBar1.Panels(0).BorderStyle = StatusBarPanelBorderStyle.Raised  
       StatusBar1.Panels(1).BorderStyle = StatusBarPanelBorderStyle.Sunken  
       StatusBar1.Panels(2).BorderStyle = StatusBarPanelBorderStyle.Raised  
    ' Set Icon property of third panel. You should replace the bolded  
    ' icon in the sample below with an icon of your own choosing.  
       StatusBar1.Panels(2).Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
       StatusBar1.ShowPanels = True  
    End Sub  
    ```  
  
    ```csharp  
    public void CreateStatusBarPanels()  
    {  
       // Create panels and set text property.  
       statusBar1.Panels.Add("One");  
       statusBar1.Panels.Add("Two");  
       statusBar1.Panels.Add("Three");  
       // Set properties of StatusBar panels.  
       // Set AutoSize property of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[1].AutoSize = StatusBarPanelAutoSize.Contents;  
       statusBar1.Panels[2].AutoSize = StatusBarPanelAutoSize.Contents;  
       // Set BorderStyle property of panels.  
       statusBar1.Panels[0].BorderStyle =  
          StatusBarPanelBorderStyle.Raised;  
       statusBar1.Panels[1].BorderStyle = StatusBarPanelBorderStyle.Sunken;  
       statusBar1.Panels[2].BorderStyle = StatusBarPanelBorderStyle.Raised;  
       // Set Icon property of third panel. You should replace the bolded  
       // icon in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       statusBar1.Panels[2].Icon =   
          new System.Drawing.Icon (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Icon.ico");  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void CreateStatusBarPanels()  
       {  
          // Create panels and set text property.  
          statusBar1->Panels->Add("One");  
          statusBar1->Panels->Add("Two");  
          statusBar1->Panels->Add("Three");  
          // Set properties of StatusBar panels.  
          // Set AutoSize property of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[1]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          statusBar1->Panels[2]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          // Set BorderStyle property of panels.  
          statusBar1->Panels[0]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          statusBar1->Panels[1]->BorderStyle =  
             StatusBarPanelBorderStyle::Sunken;  
          statusBar1->Panels[2]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          // Set Icon property of third panel.  
          // You should replace the bolded image   
          // in the sample below with an icon of your own choosing.  
          statusBar1->Panels[2]->Icon =  
             gcnew System::Drawing::Icon(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Icon.ico"));  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7c9ce-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="7c9ce-114">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="7c9ce-115">集合編輯器對話方塊</span><span class="sxs-lookup"><span data-stu-id="7c9ce-115">Collection Editor Dialog Box</span></span>](http://msdn.microsoft.com/en-us/53fb3aad-bffa-4da5-ac89-8438e6fc803c)  
 [<span data-ttu-id="7c9ce-116">操作說明：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="7c9ce-116">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [<span data-ttu-id="7c9ce-117">逐步解說：在執行階段更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="7c9ce-117">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [<span data-ttu-id="7c9ce-118">操作說明：判斷在 Windows Forms StatusBar 控制項中按下的面板</span><span class="sxs-lookup"><span data-stu-id="7c9ce-118">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [<span data-ttu-id="7c9ce-119">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="7c9ce-119">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
