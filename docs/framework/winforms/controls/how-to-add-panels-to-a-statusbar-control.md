---
title: 如何：將面板加入至 StatusBar 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- panels [Windows Forms], status bars
- status bars [Windows Forms], adding panels
- StatusBar control [Windows Forms], adding panels
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
ms.openlocfilehash: 386c8cae425c458ddf4c446a454ae4213761e651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142195"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a><span data-ttu-id="dbefd-102">如何：將面板加入至 StatusBar 控制項</span><span class="sxs-lookup"><span data-stu-id="dbefd-102">How to: Add Panels to a StatusBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="dbefd-103"><xref:System.Windows.Forms.StatusStrip>和<xref:System.Windows.Forms.ToolStripStatusLabel>控制項將 功能替換並添加到<xref:System.Windows.Forms.StatusBar><xref:System.Windows.Forms.StatusBarPanel>和 控制項;但是，如果<xref:System.Windows.Forms.StatusBar>願意<xref:System.Windows.Forms.StatusBarPanel>，將保留 和 控制項以進行向後相容性和未來使用。</span><span class="sxs-lookup"><span data-stu-id="dbefd-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="dbefd-104">[StatusBar 控制項](statusbar-control-windows-forms.md)中的可程式設計區域由<xref:System.Windows.Forms.StatusBarPanel>類的實例組成。</span><span class="sxs-lookup"><span data-stu-id="dbefd-104">The programmable area within a [StatusBar Control](statusbar-control-windows-forms.md) control consists of instances of the <xref:System.Windows.Forms.StatusBarPanel> class.</span></span> <span data-ttu-id="dbefd-105">這些通過添加到類添加<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>。</span><span class="sxs-lookup"><span data-stu-id="dbefd-105">These are added through additions to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> class.</span></span>  
  
### <a name="to-add-panels-to-a-status-bar"></a><span data-ttu-id="dbefd-106">將面板添加到狀態列</span><span class="sxs-lookup"><span data-stu-id="dbefd-106">To add panels to a status bar</span></span>  
  
1. <span data-ttu-id="dbefd-107">在此過程中，通過將狀態列面板添加到 中<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>，創建狀態列面板。</span><span class="sxs-lookup"><span data-stu-id="dbefd-107">In a procedure, create status-bar panels by adding them to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span> <span data-ttu-id="dbefd-108">使用通過<xref:System.Windows.Forms.StatusBar.Panels%2A>屬性傳遞的索引為各個面板指定屬性設置。</span><span class="sxs-lookup"><span data-stu-id="dbefd-108">Specify property settings for individual panels by using its index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property.</span></span>  
  
     <span data-ttu-id="dbefd-109">在下面的代碼示例中，為圖示的位置設置的路徑是 **"我的文件"** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="dbefd-109">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="dbefd-110">使用此位置是因為您可以假定運行 Windows 作業系統的大多數電腦都將包含此資料夾。</span><span class="sxs-lookup"><span data-stu-id="dbefd-110">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="dbefd-111">選擇此位置還允許系統存取層級最低的使用者安全地運行應用程式。</span><span class="sxs-lookup"><span data-stu-id="dbefd-111">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="dbefd-112">下面的示例需要已添加控制項的<xref:System.Windows.Forms.StatusBar>表單。</span><span class="sxs-lookup"><span data-stu-id="dbefd-112">The following example requires a form with a <xref:System.Windows.Forms.StatusBar> control already added.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="dbefd-113"><xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>是一個基於零的集合，因此代碼應相應地繼續。</span><span class="sxs-lookup"><span data-stu-id="dbefd-113">The <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> is a zero-based collection, so code should proceed accordingly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dbefd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbefd-114">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <span data-ttu-id="dbefd-115">[集合編輯器對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dbefd-115">[Collection Editor Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))</span></span>
- [<span data-ttu-id="dbefd-116">如何：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="dbefd-116">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="dbefd-117">逐步解說：在執行階段更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="dbefd-117">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="dbefd-118">如何：判斷在 Windows Forms StatusBar 控制項中按下的面板</span><span class="sxs-lookup"><span data-stu-id="dbefd-118">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="dbefd-119">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="dbefd-119">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
