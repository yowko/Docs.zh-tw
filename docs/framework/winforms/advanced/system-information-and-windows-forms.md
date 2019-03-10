---
title: 系統資訊和 Windows Form
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
ms.openlocfilehash: d8efb783fcb5bcbe9c4ee99bc784e27a1aebb0cf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707660"
---
# <a name="system-information-and-windows-forms"></a>系統資訊和 Windows Form
有時候就必須蒐集電腦上執行您的應用程式以在您的程式碼中進行決策的相關資訊。 例如，您可能只是適用於連線到特定的網路網域; 函式在此情況下，您必須判斷網域和停用此函式，如果網域不存在的方法。  
  
 Windows Forms 應用程式可以使用<xref:System.Windows.Forms.SystemInformation>類別，以判斷在執行階段的電腦相關的項目數目。 下列範例示範如何使用<xref:System.Windows.Forms.SystemInformation>類別來擷取<xref:System.Windows.Forms.SystemInformation.UserName%2A>和<xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
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
  
 所有成員<xref:System.Windows.Forms.SystemInformation>類別是唯讀; 您無法修改使用者的設定。 有超過 100 個類別的成員，傳回所有項目上的資訊，從連接到電腦的監視器數目 (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) 為 Windows 檔案總管中的圖示間距 (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A>和<xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>)。  
  
 某些更有用的成員<xref:System.Windows.Forms.SystemInformation>類別包含<xref:System.Windows.Forms.SystemInformation.ComputerName%2A>， <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>， <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>，和<xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.SystemInformation>
- [Windows Forms 中的電源管理](power-management-in-windows-forms.md)
