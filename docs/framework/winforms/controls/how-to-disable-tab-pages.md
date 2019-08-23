---
title: 作法：停用索引標籤頁
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 888228c28dce591b237be16b6a321afee0105208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967142"
---
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="57774-102">HOW TO：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="57774-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="57774-103">在某些情況下, 您會想要限制存取 Windows Forms 應用程式中可用的資料。</span><span class="sxs-lookup"><span data-stu-id="57774-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="57774-104">其中一個範例可能是當您將資料顯示在索引標籤控制項的索引標籤頁面中時:系統管理員可以在您想要限制來賓或較低層級使用者的索引標籤頁面上, 擁有資訊。</span><span class="sxs-lookup"><span data-stu-id="57774-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="57774-105">以程式設計方式停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="57774-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="57774-106">撰寫程式碼來處理索引標籤控制項<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>的事件。</span><span class="sxs-lookup"><span data-stu-id="57774-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="57774-107">這是使用者從一個索引標籤切換到下一個索引標籤時所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="57774-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="57774-108">檢查認證。</span><span class="sxs-lookup"><span data-stu-id="57774-108">Check credentials.</span></span> <span data-ttu-id="57774-109">視呈現的資訊而定, 您可能會想要檢查使用者已登入的使用者名稱或其他形式的認證, 再允許使用者查看索引標籤。</span><span class="sxs-lookup"><span data-stu-id="57774-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="57774-110">如果使用者具有適當的認證, 請顯示已按下的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="57774-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="57774-111">如果使用者沒有適當的認證, 則會顯示訊息方塊或其他使用者介面, 指出他們沒有存取權, 並返回 [初始] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="57774-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="57774-112">當您在生產應用程式中執行這項功能時, 您可以在表單的<xref:System.Windows.Forms.Form.Load>事件期間執行此認證檢查。</span><span class="sxs-lookup"><span data-stu-id="57774-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="57774-113">這可讓您在顯示任何使用者介面之前隱藏索引標籤, 這是更清楚的程式設計方法。</span><span class="sxs-lookup"><span data-stu-id="57774-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="57774-114">下面所使用的方法 (在<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件期間檢查認證和停用索引標籤) 是供說明之用。</span><span class="sxs-lookup"><span data-stu-id="57774-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="57774-115">(選擇性) 如果您有兩個以上的索引標籤頁, 會顯示不同于原始的索引標籤頁。</span><span class="sxs-lookup"><span data-stu-id="57774-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="57774-116">在下列範例中, <xref:System.Windows.Forms.CheckBox>會使用控制項代替檢查認證, 因為存取索引標籤的準則會因應用程式而異。</span><span class="sxs-lookup"><span data-stu-id="57774-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="57774-117">當事件引發時, 如果認證檢查為 true (也就是已核取核取方塊), 而選取的索引標籤`TabPage2`是 (具有機密資訊的索引標籤, 在`TabPage2`此範例中為), 則會顯示。 <xref:System.Windows.Forms.TabControl.SelectedIndexChanged></span><span class="sxs-lookup"><span data-stu-id="57774-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="57774-118">`TabPage3`否則會顯示, 並向使用者顯示訊息方塊, 指出他們沒有適當的存取權限。</span><span class="sxs-lookup"><span data-stu-id="57774-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="57774-119">下列程式碼假設具有<xref:System.Windows.Forms.CheckBox>控制項 (`CredentialCheck`) 的表單, 以及<xref:System.Windows.Forms.TabControl>具有三個索引標籤頁的控制項。</span><span class="sxs-lookup"><span data-stu-id="57774-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="57774-120">(視覺C#效果, C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="57774-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="57774-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57774-121">See also</span></span>

- [<span data-ttu-id="57774-122">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="57774-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="57774-123">如何：將控制項加入至索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="57774-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="57774-124">如何：使用 Windows Forms TabControl 新增和移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="57774-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="57774-125">如何：變更 Windows Forms TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="57774-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
