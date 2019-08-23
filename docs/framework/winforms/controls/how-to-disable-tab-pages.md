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
# <a name="how-to-disable-tab-pages"></a>HOW TO：停用索引標籤頁
在某些情況下, 您會想要限制存取 Windows Forms 應用程式中可用的資料。 其中一個範例可能是當您將資料顯示在索引標籤控制項的索引標籤頁面中時:系統管理員可以在您想要限制來賓或較低層級使用者的索引標籤頁面上, 擁有資訊。  
  
### <a name="to-disable-tab-pages-programmatically"></a>以程式設計方式停用索引標籤頁  
  
1. 撰寫程式碼來處理索引標籤控制項<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>的事件。 這是使用者從一個索引標籤切換到下一個索引標籤時所引發的事件。  
  
2. 檢查認證。 視呈現的資訊而定, 您可能會想要檢查使用者已登入的使用者名稱或其他形式的認證, 再允許使用者查看索引標籤。  
  
3. 如果使用者具有適當的認證, 請顯示已按下的索引標籤。 如果使用者沒有適當的認證, 則會顯示訊息方塊或其他使用者介面, 指出他們沒有存取權, 並返回 [初始] 索引標籤。  
  
    > [!NOTE]
    > 當您在生產應用程式中執行這項功能時, 您可以在表單的<xref:System.Windows.Forms.Form.Load>事件期間執行此認證檢查。 這可讓您在顯示任何使用者介面之前隱藏索引標籤, 這是更清楚的程式設計方法。 下面所使用的方法 (在<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件期間檢查認證和停用索引標籤) 是供說明之用。  
  
4. (選擇性) 如果您有兩個以上的索引標籤頁, 會顯示不同于原始的索引標籤頁。  
  
     在下列範例中, <xref:System.Windows.Forms.CheckBox>會使用控制項代替檢查認證, 因為存取索引標籤的準則會因應用程式而異。 當事件引發時, 如果認證檢查為 true (也就是已核取核取方塊), 而選取的索引標籤`TabPage2`是 (具有機密資訊的索引標籤, 在`TabPage2`此範例中為), 則會顯示。 <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> `TabPage3`否則會顯示, 並向使用者顯示訊息方塊, 指出他們沒有適當的存取權限。 下列程式碼假設具有<xref:System.Windows.Forms.CheckBox>控制項 (`CredentialCheck`) 的表單, 以及<xref:System.Windows.Forms.TabControl>具有三個索引標籤頁的控制項。  
  
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
  
     (視覺C#效果, C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。  
  
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
- [如何：將控制項加入至索引標籤頁](how-to-add-a-control-to-a-tab-page.md)
- [如何：使用 Windows Forms TabControl 新增和移除索引標籤](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [如何：變更 Windows Forms TabControl 的外觀](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
