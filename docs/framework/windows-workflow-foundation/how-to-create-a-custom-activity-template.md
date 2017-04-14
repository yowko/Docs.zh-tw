---
title: "HOW TO：建立自訂活動範本 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# HOW TO：建立自訂活動範本
自訂活動範本是用來自訂活動的組態，包括自訂複合活動，因此使用者不需要個別建立每個活動以及手動設定其所有屬性和其他設定。這些自訂範本會出現在 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 的 \[**工具箱**\] 中，也可以透過重新裝載的設計工具使用，使用者可以在設計工具中將範本拖曳到預先設定的設計介面上。[!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 隨附此類範本的範例：[SendAndReceiveReply 樣本設計工具](../Topic/SendAndReceiveReply%20Template%20Designer.md)和 [ReceiveAndSendReply 樣板設計工具](../Topic/ReceiveAndSendReply%20Template%20Designer.md) \(在 [傳訊活動設計工具](../Topic/Messaging%20Activity%20Designers.md) 分類中\)。  
  
 本主題的第一個程序描述如何建立 **Delay** 活動的自訂活動範本，第二個程序簡短描述如何在 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 中提供此範本，以驗證自訂範例是否正常執行。  
  
 自訂活動範本必須實作 <xref:System.Activities.Presentation.IActivityTemplateFactory>。此介面有單一 <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> 方法，您可以用它來建立及設定範本中所用的活動執行個體。  
  
### 若要建立 Delay 活動範本  
  
1.  啟動 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。  
  
2.  在 \[**檔案**\] 功能表中，指向 \[**新增**\]，再選取 \[**專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即開啟。  
  
3.  在 \[**專案類型**\] 窗格中，選取 \[**Visual C\#**\] 專案或 \[**Visual Basic**\] 群組中的 \[**工作流程**\]，視您的語言偏好而定。  
  
4.  選取 \[**範本**\] 窗格中的 \[**活動程式庫**\]。  
  
5.  在 \[**名稱**\] 方塊中輸入 `DelayActivityTemplate`。  
  
6.  接受 \[**位置**\] 和 \[**方案名稱**\] 文字方塊中的預設值，然後按一下 \[**確定**\]。  
  
7.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 DelayActivityTemplate 專案的 \[參考\] 目錄，然後選擇 \[**加入參考**\] 開啟 \[**加入參考**\] 對話方塊。  
  
8.  移至 \[**.NET**\] 索引標籤，選取左側 \[**元件名稱**\] 欄中的 \[**PresentationFramework**\]，然後按一下 \[**確定**\] 加入 PresentationFramework.dll 檔案的參考。  
  
9. 重複此程序，加入 System.Activities.Presentation.dll 和 WindowsBase.dll 檔案的參考。  
  
10. 在 \[**方案總管**\] 中，以滑鼠右鍵按一下 DelayActivityTemplate 專案，然後依序選擇 \[**加入**\] 和 \[**新增項目**\]，開啟 \[**加入新項目**\] 對話方塊。  
  
11. 選取 \[**類別**\] 範本，將它命名為 MyDelayTemplate，然後按一下 \[**確定**\]。  
  
12. 開啟 MyDelayTemplate.cs 檔案，然後加入下列陳述式。  
  
    ```  
  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
  
    ```  
  
13. 使用具有下列程式碼的 `MyDelayActivity` 類別來實作 <xref:System.Activities.Presentation.IActivityTemplateFactory>。這會將延遲設定擁有 10 秒持續時間。  
  
    ```  
  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
  
    ```  
  
14. 選取 \[**建置**\] 功能表中的 \[**建置方案**\]，以產生 DelayActivityTemplate.dll 檔案。  
  
### 若要在工作流程設計工具中提供範本  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 DelayActivityTemplate 方案，然後依序選擇 \[**加入**\] 和 \[**新增專案**\]，開啟 \[**加入新專案**\] 對話方塊。  
  
2.  選取 \[**工作流程主控台應用程式**\] 範本，將它命名為 `CustomActivityTemplateApp`，然後按一下 \[**確定**\]。  
  
3.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 CustomActivityTemplateApp 專案的 \[參考\] 目錄，然後選擇 \[**加入參考**\] 開啟 \[**加入參考**\] 對話方塊。  
  
4.  移至 \[**專案**\] 索引標籤，選取左側 \[**專案名稱**\] 欄中的 \[**DelayActivityTemplate**\]，然後按一下 \[**確定**\]，加入第一個程序中所建立之 DelayActivityTemplate.dll 檔案的參考。  
  
5.  在 \[**方案總管**\] 中以滑鼠右鍵按一下 CustomActivityTemplateApp 專案，然後選擇 \[**建置**\] 以編譯應用程式。  
  
6.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 CustomActivityTemplateApp 專案，然後選擇 \[**設定為啟始專案**\]。  
  
7.  選取 \[**偵錯**\] 功能表中的 \[**啟動但不偵錯**\]，並在 cmd.exe 視窗中出現提示時按任何鍵。  
  
8.  開啟 Workflow1.xaml 檔案，然後開啟 \[**工具箱**\]。  
  
9. 在 **DelayActivityTemplate** 類別目錄中尋找 **MyDelayActivity** 範本。將它拖曳至設計介面。在 \[**屬性**\] 視窗中確認 `Duration` 屬性已設為 10 秒。  
  
## 範例  
 MyDelayActivity.cs 檔案應該會包含下列程式碼。  
  
```  
  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
//Namespaces added  
using System.Activities;  
using System.Activities.Statements;  
using System.Activities.Presentation;  
using System.Windows;  
  
namespace DelayActivityTemplate  
{  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
}  
  
```  
  
## 請參閱  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>   
 [自訂工作流程設計經驗](../../../docs/framework/windows-workflow-foundation//customizing-the-workflow-design-experience.md)