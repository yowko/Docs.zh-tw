---
title: 如何：停用索引標籤頁
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 9074aedb81a485267dc4faff92e0fe8d0d3b467f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182165"
---
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="91a02-102">如何：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="91a02-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="91a02-103">在某些情況下，您需要限制對 Windows 表單應用程式中可用的資料的訪問。</span><span class="sxs-lookup"><span data-stu-id="91a02-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="91a02-104">其中一個示例可能是，當您在索引標籤控制項的選項卡頁中顯示資料時;例如，在索引標籤控制項的選項卡頁中顯示資料時，可能會顯示此情況。管理員可以在選項卡頁上包含您希望從來賓或較低級別使用者限制的資訊。</span><span class="sxs-lookup"><span data-stu-id="91a02-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="91a02-105">以程式設計方式禁用選項卡頁</span><span class="sxs-lookup"><span data-stu-id="91a02-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="91a02-106">編寫代碼來處理索引標籤控制項的事件<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>。</span><span class="sxs-lookup"><span data-stu-id="91a02-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="91a02-107">這是當使用者從一個選項卡切換到下一個選項卡時引發的事件。</span><span class="sxs-lookup"><span data-stu-id="91a02-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="91a02-108">檢查憑據。</span><span class="sxs-lookup"><span data-stu-id="91a02-108">Check credentials.</span></span> <span data-ttu-id="91a02-109">根據提供的資訊，您可能需要在允許使用者查看選項卡之前檢查使用者已登錄的使用者名或其他形式的憑據。</span><span class="sxs-lookup"><span data-stu-id="91a02-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="91a02-110">如果使用者具有適當的憑據，請顯示按一下的選項卡。</span><span class="sxs-lookup"><span data-stu-id="91a02-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="91a02-111">如果使用者沒有適當的憑據，則顯示訊息方塊或其他一些使用者介面，指示他們沒有存取權限，然後返回到初始選項卡。</span><span class="sxs-lookup"><span data-stu-id="91a02-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="91a02-112">在生產應用程式中實現此功能時，可以在表單<xref:System.Windows.Forms.Form.Load>的事件期間執行此憑據檢查。</span><span class="sxs-lookup"><span data-stu-id="91a02-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="91a02-113">這將允許您在顯示任何使用者介面之前隱藏選項卡，這是一種更簡潔的程式設計方法。</span><span class="sxs-lookup"><span data-stu-id="91a02-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="91a02-114">下面使用的方法（在<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>活動期間檢查憑據並禁用選項卡）用於說明目的。</span><span class="sxs-lookup"><span data-stu-id="91a02-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="91a02-115">或者，如果您有兩個以上的選項卡頁，則顯示與原始頁面不同的選項卡頁。</span><span class="sxs-lookup"><span data-stu-id="91a02-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="91a02-116">在下面的示例中，使用<xref:System.Windows.Forms.CheckBox>控制項來代替檢查憑據，因為訪問選項卡的條件因應用程式而異。</span><span class="sxs-lookup"><span data-stu-id="91a02-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="91a02-117">引發<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件時，如果憑據檢查為 true（即選中核取方塊），並且所選選項卡為`TabPage2`（在此示例中顯示帶有機密資訊的選項卡），則`TabPage2`顯示。</span><span class="sxs-lookup"><span data-stu-id="91a02-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="91a02-118">否則，`TabPage3`將顯示訊息方塊，並顯示一個訊息方塊，指示使用者沒有適當的存取權限。</span><span class="sxs-lookup"><span data-stu-id="91a02-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="91a02-119">下面的代碼假定一個包含控制項<xref:System.Windows.Forms.CheckBox>（`CredentialCheck`） 的<xref:System.Windows.Forms.TabControl>表單和具有三個選項卡頁的控制項。</span><span class="sxs-lookup"><span data-stu-id="91a02-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     <span data-ttu-id="91a02-120">（視覺 C#，視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="91a02-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="91a02-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91a02-121">See also</span></span>

- [<span data-ttu-id="91a02-122">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="91a02-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="91a02-123">如何：將控制項加入至索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="91a02-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="91a02-124">操作說明：使用 Windows Forms TabControl 加入和移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="91a02-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="91a02-125">如何：變更 Windows Form TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="91a02-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
