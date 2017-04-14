---
title: "如何：停用索引標籤頁 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "索引標籤頁, 在表單中隱藏"
  - "TabControl 控制項 [Windows Form], 停用頁面"
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：停用索引標籤頁
在某些狀況下，您會想要限制對 Windows Form 應用程式中可用資料的存取。  這種情況的例子之一，是當您將資料顯示在索引標籤控制項的索引標籤頁中時；管理員會擁有索引標籤頁上的資訊，而您會希望限制這些資訊，以防訪客或低階使用者存取。  
  
### 若要以程式設計的方式停用索引標籤頁  
  
1.  撰寫程式碼處理索引標籤控制項的 <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> 事件。  這就是當使用者切換索引標籤間時所引發的事件。  
  
2.  檢查認證。  在允許使用者檢視索引標籤前，根據提供的資訊，您可能要檢查使用者用以登入的使用者名稱或其他形式的認證。  
  
3.  如果使用者具有適當的認證，則會顯示使用者所按的索引標籤。  如果使用者沒有適當的認證，則會顯示訊息方塊或其他使用者介面，表示使用者沒有存取權限，並返回最初的索引標籤。  
  
    > [!NOTE]
    >  在實際執行應用程式中實作這個功能時，您可以在表單的 <xref:System.Windows.Forms.Form.Load> 事件期間執行認證檢查。  如此可讓您在顯示任何使用者介面時隱藏索引標籤，對於程式設計而言是更為徹底的方法。  以下使用的方法論 \(在 <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> 事件期間檢查認證並停用索引標籤\) 是做為說明之用。  
  
4.  如果您有兩個以上的索引標籤頁，也可以顯示有別於原始頁的索引標籤頁。  
  
     在以下的範例中，<xref:System.Windows.Forms.CheckBox> 控制項是用以替代檢查認證，因為存取索引標籤的準則會依應用程式而有所不同。  當 <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> 事件引發時，如果認證檢查為 true \(即選取了核取方塊\)，而選取的索引標籤為 `TabPage2` \(在此範例中為具有機密資訊的索引標籤\)，則會顯示 `TabPage2`。  否則，會對使用者顯示 `TabPage3` 和訊息方塊，表示他們沒有適當的存取權限。  以下程式碼假設含 <xref:System.Windows.Forms.CheckBox> 控制項 \(`CredentialCheck`\) 的表單，以及含有三個索引標籤頁的 <xref:System.Windows.Forms.TabControl> 控制項。  
  
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
  
     \(Visual C\#、Visual C\+\+\) 在表單的建構函式中加入下列程式碼，將事件處理常式加以註冊。  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## 請參閱  
 [TabControl 控制項概觀](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [如何：將控制項加入至索引標籤頁](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [如何：使用 Windows Form TabControl 加入和移除索引標籤](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)   
 [如何：變更 Windows Form TabControl 的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)