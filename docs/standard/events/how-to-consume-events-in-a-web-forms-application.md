---
title: "如何：使用 Web Form 應用程式中的事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "事件 [.NET Framework]，Web Form"
  - "Web Form 控制項和事件"
  - "事件處理常式 [.NET Framework]，Web Form"
  - "事件 [.NET Framework]，使用"
  - "Web Form，事件處理"
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# 如何：使用 Web Form 應用程式中的事件
ASP.NET Web Form 應用程式中的常見使用情況是使用控制項填入網頁，然後根據使用者所按的控制項，執行特定動作。  例如，當使用者在網頁中按一下 <xref:System.Web.UI.WebControls.Button?displayProperty=fullName> 控制項，會引發事件。  藉由處理事件，應用程式能為按一下按鈕的動作執行適當的應用程式邏輯。  
  
### 若要處理網頁上按鈕的 Click 事件  
  
1.  建立具有其設定為下一個步驟中所定義的方法名稱的 `OnClick` 值的 <xref:System.Web.UI.WebControls.Button> 控制項的 ASP.NET Web Form 網頁 \(網頁\)。  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  定義一個符合 <xref:System.Web.UI.WebControls.Button.Click> 事件委派簽章，其名稱定義於 `OnClick` 值的事件處理常式。  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     <xref:System.Web.UI.WebControls.Button.Click> 事件會針對委派型別使用 <xref:System.EventHandler> 類別，並針對事件資料使用 <xref:System.EventArgs> 類別。  ASP.NET 網頁架構會自動產生程式碼，該程式碼會建立<xref:System.EventHandler> 執行個體，並將這個委派執行個體加入至 <xref:System.Web.UI.WebControls.Button> 介面的 <xref:System.Web.UI.WebControls.Button.Click> 事件。  
  
3.  在您於步驟 2 所定義的事件處理常式方法中，在事件發生時加入程式碼執行所需的任何動作。  
  
## 請參閱  
 [事件](../../../docs/standard/events/index.md)