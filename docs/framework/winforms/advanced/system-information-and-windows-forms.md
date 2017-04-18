---
title: "系統資訊和 Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "網域名稱, 擷取"
  - "系統資訊 [Windows Form]"
  - "SystemInformation 類別 [Windows Form]"
  - "使用者名稱, 擷取"
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 系統資訊和 Windows Form
有時候，您可能必須收集目前執行應用程式之電腦的相關資訊，以便決定程式碼。  例如，您可能有一項只在連接到特定網路網域時才適用的函式；如果是這種情況，您就需要一套方法來判斷網域並在網域不存在時停用函式。  
  
 Windows Form 應用程式可以使用 <xref:System.Windows.Forms.SystemInformation> 類別在執行階段判斷電腦的一些事項。  下列範例示範使用 <xref:System.Windows.Forms.SystemInformation> 類別來擷取 <xref:System.Windows.Forms.SystemInformation.UserName%2A> 和 <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>：  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to " _  
+ Domain)  
```  
  
 <xref:System.Windows.Forms.SystemInformation> 類別的所有成員都是唯讀的；您無法修改使用者的設定。  此類別有超過 100 個成員，會傳回從電腦連接的監視器數目 \(<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>\) 到 Windows 檔案總管中的圖示間距 \(<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> 和 <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>\) 等各項資訊。  
  
 <xref:System.Windows.Forms.SystemInformation> 類別中某些較有用的成員包括 <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>、<xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>、<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> 和 <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>。  
  
## 請參閱  
 <xref:System.Windows.Forms.SystemInformation>   
 [Windows Form 中的電源管理](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)