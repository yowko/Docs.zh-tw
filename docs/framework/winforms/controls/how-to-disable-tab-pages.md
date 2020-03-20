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
# <a name="how-to-disable-tab-pages"></a>如何：停用索引標籤頁
在某些情況下，您需要限制對 Windows 表單應用程式中可用的資料的訪問。 其中一個示例可能是，當您在索引標籤控制項的選項卡頁中顯示資料時;例如，在索引標籤控制項的選項卡頁中顯示資料時，可能會顯示此情況。管理員可以在選項卡頁上包含您希望從來賓或較低級別使用者限制的資訊。  
  
### <a name="to-disable-tab-pages-programmatically"></a>以程式設計方式禁用選項卡頁  
  
1. 編寫代碼來處理索引標籤控制項的事件<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>。 這是當使用者從一個選項卡切換到下一個選項卡時引發的事件。  
  
2. 檢查憑據。 根據提供的資訊，您可能需要在允許使用者查看選項卡之前檢查使用者已登錄的使用者名或其他形式的憑據。  
  
3. 如果使用者具有適當的憑據，請顯示按一下的選項卡。 如果使用者沒有適當的憑據，則顯示訊息方塊或其他一些使用者介面，指示他們沒有存取權限，然後返回到初始選項卡。  
  
    > [!NOTE]
    > 在生產應用程式中實現此功能時，可以在表單<xref:System.Windows.Forms.Form.Load>的事件期間執行此憑據檢查。 這將允許您在顯示任何使用者介面之前隱藏選項卡，這是一種更簡潔的程式設計方法。 下面使用的方法（在<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>活動期間檢查憑據並禁用選項卡）用於說明目的。  
  
4. 或者，如果您有兩個以上的選項卡頁，則顯示與原始頁面不同的選項卡頁。  
  
     在下面的示例中，使用<xref:System.Windows.Forms.CheckBox>控制項來代替檢查憑據，因為訪問選項卡的條件因應用程式而異。 引發<xref:System.Windows.Forms.TabControl.SelectedIndexChanged>事件時，如果憑據檢查為 true（即選中核取方塊），並且所選選項卡為`TabPage2`（在此示例中顯示帶有機密資訊的選項卡），則`TabPage2`顯示。 否則，`TabPage3`將顯示訊息方塊，並顯示一個訊息方塊，指示使用者沒有適當的存取權限。 下面的代碼假定一個包含控制項<xref:System.Windows.Forms.CheckBox>（`CredentialCheck`） 的<xref:System.Windows.Forms.TabControl>表單和具有三個選項卡頁的控制項。  
  
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
  
     （視覺 C#，視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。  
  
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
- [操作說明：使用 Windows Forms TabControl 加入和移除索引標籤](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [如何：變更 Windows Form TabControl 的外觀](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
