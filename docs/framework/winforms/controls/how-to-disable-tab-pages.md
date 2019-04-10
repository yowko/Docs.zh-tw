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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336066"
---
# <a name="how-to-disable-tab-pages"></a>HOW TO：停用索引標籤頁
在某些情況下，您會想要限制存取可以在 Windows Forms 應用程式中使用的資料。 這其中一個範例可能是當您有索引標籤控制項之索引標籤頁面中顯示的資料系統管理員可能會有您想要限制從客體或較低層級的使用者 索引標籤頁面上的資訊。  
  
### <a name="to-disable-tab-pages-programmatically"></a>若要以程式設計方式停用索引標籤頁  
  
1. 撰寫程式碼來處理索引標籤控制項的<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件。 這是當使用者從某個索引標籤切換至下一個引發的事件。  
  
2. 請檢查認證。 視所呈現的資訊，您可能想要檢查在使用者登入的使用者名稱或其他形式的認證，再允許使用者檢視 索引標籤。  
  
3. 如果使用者有適當的認證，顯示已按下 [] 索引標籤。 如果使用者沒有適當的認證，顯示訊息方塊，或一些其他使用者介面，表示他們沒有存取權，並返回初始 索引標籤。  
  
    > [!NOTE]
    >  當您在生產環境應用程式中實作這項功能時，您可以在表單的期間來執行這項認證檢查<xref:System.Windows.Forms.Form.Load>事件。 這可讓您隱藏 索引標籤上，才會顯示任何使用者介面，這是程式設計更簡便的方法。 下面所使用的方法 (檢查認證，並停用 [期間] 索引標籤<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件) 為說明之用。  
  
4. （選擇性） 如果您有兩個以上的索引標籤頁，顯示與原始版本不同的索引標籤頁。  
  
     在下列範例中，<xref:System.Windows.Forms.CheckBox>控制項使用存取 索引標籤會因應用程式檢查認證，做為準則。 時<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>引發事件時，如果認證核取為 true （也就是都會選取此核取方塊） 選取的索引標籤，而且`TabPage2`（索引標籤上的機密資訊，在此範例中），然後`TabPage2`隨即出現。 否則，`TabPage3`隨即出現，而且訊息方塊會顯示給使用者，指出他們沒有適當存取權限。 下列程式碼假設使用的表單<xref:System.Windows.Forms.CheckBox>控制項 (`CredentialCheck`) 和<xref:System.Windows.Forms.TabControl>與三個索引標籤頁的控制項。  
  
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
  
     (Visual C#、 Visual C++)下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>另請參閱

- [TabControl 控制項概觀](tabcontrol-control-overview-windows-forms.md)
- [HOW TO：將控制項新增至索引標籤頁](how-to-add-a-control-to-a-tab-page.md)
- [HOW TO：使用 Windows Forms TabControl 新增和移除索引標籤](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [HOW TO：變更 Windows Forms TabControl 的外觀](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
