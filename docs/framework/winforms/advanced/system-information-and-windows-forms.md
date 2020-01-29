---
title: '[系統資訊]'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: a91e2fd8db0ef338ce30f89f11869f1b6698af3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732586"
---
# <a name="system-information-and-windows-forms"></a>系統資訊和 Windows Form
有時候，必須收集您的應用程式執行所在電腦的相關資訊，才能在您的程式碼中做出決策。 例如，您可能有一個僅適用于連線到特定網路網域的函數;在此情況下，您需要一種方法來判斷網域，並在網域不存在時停用函式。  
  
 Windows Forms 的應用程式可以使用 <xref:System.Windows.Forms.SystemInformation> 類別，在執行時間判斷電腦的一些相關事項。 下列範例示範如何使用 <xref:System.Windows.Forms.SystemInformation> 類別來取出 <xref:System.Windows.Forms.SystemInformation.UserName%2A> 和 <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>：  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to "
+ Domain);
```  
  
 <xref:System.Windows.Forms.SystemInformation> 類別的所有成員都是唯讀的;您無法修改使用者的設定。 類別的成員超過100，從連接到電腦的監視器數目（<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>），將所有專案的相關資訊傳回 Windows Explorer 中的圖示間距（<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> 和 <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>）。  
  
 <xref:System.Windows.Forms.SystemInformation> 類別的一些更有用的成員包括 <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>、<xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>、<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>和 <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.SystemInformation>
- [Windows Forms 中的電源管理](power-management-in-windows-forms.md)
