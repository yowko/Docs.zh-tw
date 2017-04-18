---
title: "控制項和元件撰寫疑難排解 | Microsoft Docs"
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
  - "元件 [Windows Form], 疑難排解"
  - "控制項 [Windows Form], 疑難排解"
  - "元件疑難排解"
  - "控制項疑難排解"
  - "Windows Form 控制項, 偵錯"
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 控制項和元件撰寫疑難排解
這個主題列出以下在開發元件和控制項時常發生的問題。  如需詳細資訊，請參閱[使用元件進行程式設計](../Topic/Programming%20with%20Components.md)。  
  
-   無法將控制項加入至工具箱  
  
-   無法偵錯 Windows Form 使用者控制項或元件  
  
-   在繼承控制項或元件中引發兩次事件  
  
-   設計階段錯誤：「無法建立元件 '*Component Name*'。」  
  
-   STAThreadAttribute  
  
-   元件圖示沒有顯示在工具箱中  
  
## 無法將控制項加入至工具箱  
 如果您希望將在其他專案或協力廠商控制項中建立的自訂控制項加入至 \[**工具箱**\]，就必須手動處理。  如果目前的專案包含了控制項或元件，就應該會自動顯示在 \[**工具箱**\] 中。  如需詳細資訊，請參閱[逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。  
  
#### 若要將控制項加入至工具箱  
  
1.  以滑鼠右鍵按一下 \[**工具箱**\]，然後從捷徑功能表中選取 \[**選擇項目**\]。  
  
2.  在 \[**選擇工具箱項目**\] 對話方塊中加入該元件：  
  
    -   如果您希望加入 .NET Framework 元件或控制項，請按一下 \[**.NET Framework 元件**\] 索引標籤。  
  
         \-或\-  
  
    -   如果您希望加入 COM 元件或 ActiveX 控制項，請按一下 \[**COM 元件**\] 索引標籤。  
  
3.  如果您的控制項列在對話方塊中，請確定它已選取，然後按一下 \[**確定**\]。  
  
     控制項已加入至 \[**工具箱**\]。  
  
4.  如果您的控制項未列在對話方塊中，請執行下列作業：  
  
    1.  按一下 \[**瀏覽**\] 按鈕。  
  
    2.  瀏覽至包含控制項的 .dll 檔案的資料夾。  
  
    3.  選取 .dll 檔案，然後按一下 \[**開啟**\]。  
  
         您的控制項就會出現在對話方塊中。  
  
    4.  請確認已選取控制項，然後按一下 \[**確定**\]。  
  
         您的控制項已加入至 \[**工具箱**\]。  
  
## 無法偵錯 Windows Form 使用者控制項或元件  
 如果您的控制項是衍生自 <xref:System.Windows.Forms.UserControl> 類別，就可以使用測試容器偵錯控制項的執行階段行為。  如需詳細資訊，請參閱 [如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
 其他自訂控制項和元件並非獨立專案。  他們必須由例如像 Windows Form 專案的應用程式所裝載。  若要偵錯控制項或元件，必須將它加入至 Windows Form 專案中。  
  
#### 若要偵錯控制項或元件  
  
1.  從 \[**建置**\] 功能表按一下 \[**建置方案**\] 以建置您的方案。  
  
2.  從 \[**檔案**\] 功能表選擇 \[**加入**\]，然後選擇 \[**新增專案**\]，將測試專案加入至應用程式。  
  
3.  在 \[**加入新的專案**\] 對話方塊中，選擇專案類型的 \[**Windows 應用程式**\]。  
  
4.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下新專案的 \[**參考**\] 節點。  在捷徑功能表上按一下 \[**加入參考**\]，將參考加入至包含控制項或元件的專案。  
  
5.  在測試專案中建立控制項或元件的執行個體。  如果元件就在 \[**工具箱**\] 中，您可以將它拖曳至設計工具介面，或如下列範例所示，以程式設計方式建立執行個體：  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     現在您可以照常偵錯控制項或元件。  
  
 如需偵錯的詳細資訊，請參閱[Visual Studio 偵錯](../Topic/Debugging%20in%20Visual%20Studio.md)和[逐步解說：在設計階段偵錯自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)。  
  
## 在繼承控制項或元件中引發兩次事件  
 這可能是因為重複的 `Handles` 子句所造成的。  如需詳細資訊，請參閱[Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)。  
  
## 設計階段錯誤：「無法建立元件 'Component Name'。」  
 您的元件或控制項必須提供沒有參數的預設建構函式。  當設計環境建立元件或控制項的執行個體時，並不會嘗試提供任何參數給使用參數的建構函式多載。  
  
## STAThreadAttribute  
 <xref:System.STAThreadAttribute> 會通知 Common Language Runtime \(CLR\) 有關 Windows Form 使用單一執行緒 Apartment 模型的消息。  如果沒有套用這個屬性至 Windows Form 應用程式的 `Main` 方法，您可能會發現未知的行為。  例如，對於類似 <xref:System.Windows.Forms.ListView> 的控制項，可能不會出現背景影像。  某些控制項也可能需要這個屬性，以修正 AutoComplete 和拖放行為。  
  
## 元件圖示沒有顯示在工具箱中  
 使用 <xref:System.Drawing.ToolboxBitmapAttribute> 將圖示與您的自訂元件建立關聯時，\[工具箱\] 中沒有出現用來自動產生元件的點陣圖。  若要看到點陣圖，請使用 \[**選擇工具箱項目**\] 對話方塊重新載入該控制項。  如需詳細資訊，請參閱 [如何：為控制項提供工具箱點陣圖](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)。  
  
## 請參閱  
 [在設計階段開發 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)   
 [如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)   
 [逐步解說：在設計階段偵錯自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)   
 [元件撰寫](../Topic/Component%20Authoring.md)   
 [Troubleshooting Design\-Time Development](../Topic/Troubleshooting%20Design-Time%20Development.md)   
 [使用元件進行程式設計](../Topic/Programming%20with%20Components.md)