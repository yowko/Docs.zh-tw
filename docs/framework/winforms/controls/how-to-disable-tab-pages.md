---
title: "如何：停用索引標籤頁"
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
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20674a93459f42a793ddf5f7ee5dffb1fa122d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="032da-102">如何：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="032da-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="032da-103">在某些情況下，您會想要限制存取您的 Windows Form 應用程式中使用的資料。</span><span class="sxs-lookup"><span data-stu-id="032da-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="032da-104">當您需要的索引標籤控制項; 索引標籤頁面中顯示的資料，可能是一個範例是系統管理員可能會有您想要限制 guest 帳戶或較低層級的使用者 索引標籤頁面上的資訊。</span><span class="sxs-lookup"><span data-stu-id="032da-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="032da-105">若要以程式設計的方式停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="032da-105">To disable tab pages programmatically</span></span>  
  
1.  <span data-ttu-id="032da-106">撰寫程式碼來處理索引標籤控制項的<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="032da-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="032da-107">這是當使用者從某個索引標籤切換至下一個引發的事件。</span><span class="sxs-lookup"><span data-stu-id="032da-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2.  <span data-ttu-id="032da-108">請檢查認證。</span><span class="sxs-lookup"><span data-stu-id="032da-108">Check credentials.</span></span> <span data-ttu-id="032da-109">視所呈現之資訊，您可以檢查使用者登入的使用者名稱或其他形式的認證，再允許使用者檢視 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="032da-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3.  <span data-ttu-id="032da-110">如果使用者有適當的認證，顯示已按下 [] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="032da-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="032da-111">如果使用者沒有適當的認證，會顯示訊息方塊中，或指出此問題的一些其他使用者介面他們沒有存取權，並返回 [初始] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="032da-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="032da-112">當您在實際執行應用程式中實作這項功能時，您就可以在表單的期間執行這項認證檢查<xref:System.Windows.Forms.Form.Load>事件。</span><span class="sxs-lookup"><span data-stu-id="032da-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="032da-113">這可讓您顯示任何使用者介面，這是清理方式進行程式設計前隱藏 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="032da-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="032da-114">使用以下方法 (檢查認證並停用 [期間] 索引標籤<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件) 為說明之用。</span><span class="sxs-lookup"><span data-stu-id="032da-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4.  <span data-ttu-id="032da-115">（選擇性） 如果您有兩個以上的索引標籤頁，顯示與原始版本不同的索引標籤頁。</span><span class="sxs-lookup"><span data-stu-id="032da-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="032da-116">在下列範例中，<xref:System.Windows.Forms.CheckBox>控制項的用途就不需檢查認證，做為準則存取 索引標籤會根據應用程式而有所不同。</span><span class="sxs-lookup"><span data-stu-id="032da-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="032da-117">當<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>引發事件時，如果為 true 的認證核取 （也就是核取方塊） 選取的索引標籤，且`TabPage2`（索引標籤上的機密資訊，在此範例中），然後`TabPage2`會顯示。</span><span class="sxs-lookup"><span data-stu-id="032da-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="032da-118">否則，`TabPage3`會顯示訊息方塊會顯示給使用者，指出他們沒有適當存取權限。</span><span class="sxs-lookup"><span data-stu-id="032da-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="032da-119">下列程式碼會假設的表單具有<xref:System.Windows.Forms.CheckBox>控制項 (`CredentialCheck`) 和<xref:System.Windows.Forms.TabControl>具有三個索引標籤頁控制項。</span><span class="sxs-lookup"><span data-stu-id="032da-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="032da-120">（visual C#、 Visual c + +）下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="032da-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="032da-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="032da-121">See Also</span></span>  
 [<span data-ttu-id="032da-122">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="032da-122">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="032da-123">操作說明：將控制項加入至索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="032da-123">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="032da-124">操作說明：使用 Windows Forms TabControl 加入和移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="032da-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="032da-125">操作說明：變更 Windows Forms TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="032da-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
