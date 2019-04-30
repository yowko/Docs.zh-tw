---
title: HOW TO：停用索引標籤頁
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 21592fdd74c43d40310e0fcbc96af6565a42e08b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013448"
---
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="58397-102">HOW TO：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="58397-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="58397-103">在某些情況下，您會想要限制存取可以在 Windows Forms 應用程式中使用的資料。</span><span class="sxs-lookup"><span data-stu-id="58397-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="58397-104">這其中一個範例可能是當您有索引標籤控制項之索引標籤頁面中顯示的資料系統管理員可能會有您想要限制從客體或較低層級的使用者 索引標籤頁面上的資訊。</span><span class="sxs-lookup"><span data-stu-id="58397-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="58397-105">若要以程式設計方式停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="58397-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="58397-106">撰寫程式碼來處理索引標籤控制項的<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="58397-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="58397-107">這是當使用者從某個索引標籤切換至下一個引發的事件。</span><span class="sxs-lookup"><span data-stu-id="58397-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="58397-108">請檢查認證。</span><span class="sxs-lookup"><span data-stu-id="58397-108">Check credentials.</span></span> <span data-ttu-id="58397-109">視所呈現的資訊，您可能想要檢查在使用者登入的使用者名稱或其他形式的認證，再允許使用者檢視 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="58397-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="58397-110">如果使用者有適當的認證，顯示已按下 [] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="58397-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="58397-111">如果使用者沒有適當的認證，顯示訊息方塊，或一些其他使用者介面，表示他們沒有存取權，並返回初始 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="58397-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="58397-112">當您在生產環境應用程式中實作這項功能時，您可以在表單的期間來執行這項認證檢查<xref:System.Windows.Forms.Form.Load>事件。</span><span class="sxs-lookup"><span data-stu-id="58397-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="58397-113">這可讓您隱藏 索引標籤上，才會顯示任何使用者介面，這是程式設計更簡便的方法。</span><span class="sxs-lookup"><span data-stu-id="58397-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="58397-114">下面所使用的方法 (檢查認證，並停用 [期間] 索引標籤<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件) 為說明之用。</span><span class="sxs-lookup"><span data-stu-id="58397-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="58397-115">（選擇性） 如果您有兩個以上的索引標籤頁，顯示與原始版本不同的索引標籤頁。</span><span class="sxs-lookup"><span data-stu-id="58397-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="58397-116">在下列範例中，<xref:System.Windows.Forms.CheckBox>控制項使用存取 索引標籤會因應用程式檢查認證，做為準則。</span><span class="sxs-lookup"><span data-stu-id="58397-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="58397-117">時<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>引發事件時，如果認證核取為 true （也就是都會選取此核取方塊） 選取的索引標籤，而且`TabPage2`（索引標籤上的機密資訊，在此範例中），然後`TabPage2`隨即出現。</span><span class="sxs-lookup"><span data-stu-id="58397-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="58397-118">否則，`TabPage3`隨即出現，而且訊息方塊會顯示給使用者，指出他們沒有適當存取權限。</span><span class="sxs-lookup"><span data-stu-id="58397-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="58397-119">下列程式碼假設使用的表單<xref:System.Windows.Forms.CheckBox>控制項 (`CredentialCheck`) 和<xref:System.Windows.Forms.TabControl>與三個索引標籤頁的控制項。</span><span class="sxs-lookup"><span data-stu-id="58397-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="58397-120">(Visual C#、 Visual C++)下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="58397-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="58397-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58397-121">See also</span></span>

- [<span data-ttu-id="58397-122">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="58397-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="58397-123">如何：將控制項加入索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="58397-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="58397-124">如何：新增和移除使用 Windows Form TabControl 的索引標籤</span><span class="sxs-lookup"><span data-stu-id="58397-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="58397-125">如何：變更 Windows Form TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="58397-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
