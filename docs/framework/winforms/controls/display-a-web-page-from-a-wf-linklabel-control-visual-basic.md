---
title: "如何：從 Windows Form LinkLabel 控制項顯示 Web 網頁 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LinkLabel1_LinkClicked"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "範例 [Windows Form], LinkLabel 控制項"
  - "連結, 從表單到 Web 網頁"
  - "LinkLabel 控制項 [Windows Form], 範例"
  - "Web 網頁, 顯示"
  - "Windows Form, 連結至 Web 網頁"
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：從 Windows Form LinkLabel 控制項顯示 Web 網頁 (Visual Basic)
這個範例會在使用者按一下 Windows Form <xref:System.Windows.Forms.LinkLabel> 控制項時，於預設瀏覽器中顯示網頁。  
  
## 範例  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 `Form1` 的 Windows Form。  
  
-   名為 `LinkLabel1` 的 <xref:System.Windows.Forms.LinkLabel> 控制項。  
  
-   作用中網際網路連接。  
  
## .NET Framework 安全性  
 呼叫 <xref:System.Diagnostics.Process.Start%2A> 方法時需要完全信任。  如需詳細資訊，請參閱 <xref:System.Security.SecurityException>。  
  
## 請參閱  
 <xref:System.Windows.Forms.LinkLabel>   
 [LinkLabel 控制項](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)