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
ms.openlocfilehash: 94d8522a71fcd565ae8f994d73ffe4c46fcf7ce3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-tab-pages"></a>如何：停用索引標籤頁
在某些情況下，您會想要限制存取您的 Windows Form 應用程式中使用的資料。 當您需要的索引標籤控制項; 索引標籤頁面中顯示的資料，可能是一個範例是系統管理員可能會有您想要限制 guest 帳戶或較低層級的使用者 索引標籤頁面上的資訊。  
  
### <a name="to-disable-tab-pages-programmatically"></a>若要以程式設計的方式停用索引標籤頁  
  
1.  撰寫程式碼來處理索引標籤控制項的<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件。 這是當使用者從某個索引標籤切換至下一個引發的事件。  
  
2.  請檢查認證。 視所呈現之資訊，您可以檢查使用者登入的使用者名稱或其他形式的認證，再允許使用者檢視 索引標籤。  
  
3.  如果使用者有適當的認證，顯示已按下 [] 索引標籤。 如果使用者沒有適當的認證，會顯示訊息方塊中，或指出此問題的一些其他使用者介面他們沒有存取權，並返回 [初始] 索引標籤。  
  
    > [!NOTE]
    >  當您在實際執行應用程式中實作這項功能時，您就可以在表單的期間執行這項認證檢查<xref:System.Windows.Forms.Form.Load>事件。 這可讓您顯示任何使用者介面，這是清理方式進行程式設計前隱藏 索引標籤。 使用以下方法 (檢查認證並停用 [期間] 索引標籤<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件) 為說明之用。  
  
4.  （選擇性） 如果您有兩個以上的索引標籤頁，顯示與原始版本不同的索引標籤頁。  
  
     在下列範例中，<xref:System.Windows.Forms.CheckBox>控制項的用途就不需檢查認證，做為準則存取 索引標籤會根據應用程式而有所不同。 當<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>引發事件時，如果為 true 的認證核取 （也就是核取方塊） 選取的索引標籤，且`TabPage2`（索引標籤上的機密資訊，在此範例中），然後`TabPage2`會顯示。 否則，`TabPage3`會顯示訊息方塊會顯示給使用者，指出他們沒有適當存取權限。 下列程式碼會假設的表單具有<xref:System.Windows.Forms.CheckBox>控制項 (`CredentialCheck`) 和<xref:System.Windows.Forms.TabControl>具有三個索引標籤頁控制項。  
  
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
  
     （visual C#、 Visual c + +）下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [TabControl 控制項概觀](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [操作說明：將控制項加入至索引標籤頁](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [操作說明：使用 Windows Forms TabControl 加入和移除索引標籤](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 [操作說明：變更 Windows Forms TabControl 的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
