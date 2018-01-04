---
title: "系統資訊和 Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 685a62b885469a9cac8884cc045b67bac02bea80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="system-information-and-windows-forms"></a>系統資訊和 Windows Form
有時則需要收集您的應用程式執行才能做出的決策，在程式碼中的電腦的相關資訊。 例如，您可能只是適用於連線到特定的網路網域; 函式在此情況下，您必須能夠判斷的網域，並停用此函式，如果網域不存在。  
  
 Windows Form 應用程式可以使用<xref:System.Windows.Forms.SystemInformation>類別以決定在執行階段電腦相關的事項數目。 下列範例示範如何使用<xref:System.Windows.Forms.SystemInformation>類別來擷取<xref:System.Windows.Forms.SystemInformation.UserName%2A>和<xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
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
  
 所有成員<xref:System.Windows.Forms.SystemInformation>類別是唯讀，則您無法修改使用者的設定。 有超過 100 個類別的成員，傳回資訊的所有連接到電腦的監視器數目 (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) 為 Windows 檔案總管 中的圖示間距 (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A>和<xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>)。  
  
 一些更實用的成員<xref:System.Windows.Forms.SystemInformation>類別包含<xref:System.Windows.Forms.SystemInformation.ComputerName%2A>， <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>， <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>，和<xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.SystemInformation>  
 [Windows Forms 中的電源管理](../../../../docs/framework/winforms/advanced/power-management-in-windows-forms.md)
