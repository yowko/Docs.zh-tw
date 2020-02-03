---
title: 系統資訊
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
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="8d8b6-102">系統資訊和 Windows Form</span><span class="sxs-lookup"><span data-stu-id="8d8b6-102">System Information and Windows Forms</span></span>
<span data-ttu-id="8d8b6-103">有時候，必須收集您的應用程式執行所在電腦的相關資訊，才能在您的程式碼中做出決策。</span><span class="sxs-lookup"><span data-stu-id="8d8b6-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="8d8b6-104">例如，您可能有一個僅適用于連線到特定網路網域的函數;在此情況下，您需要一種方法來判斷網域，並在網域不存在時停用函式。</span><span class="sxs-lookup"><span data-stu-id="8d8b6-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="8d8b6-105">Windows Forms 的應用程式可以使用 <xref:System.Windows.Forms.SystemInformation> 類別，在執行時間判斷電腦的一些相關事項。</span><span class="sxs-lookup"><span data-stu-id="8d8b6-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="8d8b6-106">下列範例示範如何使用 <xref:System.Windows.Forms.SystemInformation> 類別來取出 <xref:System.Windows.Forms.SystemInformation.UserName%2A> 和 <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>：</span><span class="sxs-lookup"><span data-stu-id="8d8b6-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
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
  
 <span data-ttu-id="8d8b6-107"><xref:System.Windows.Forms.SystemInformation> 類別的所有成員都是唯讀的;您無法修改使用者的設定。</span><span class="sxs-lookup"><span data-stu-id="8d8b6-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="8d8b6-108">類別的成員超過100，從連接到電腦的監視器數目（<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>），將所有專案的相關資訊傳回 Windows Explorer 中的圖示間距（<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> 和 <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>）。</span><span class="sxs-lookup"><span data-stu-id="8d8b6-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="8d8b6-109"><xref:System.Windows.Forms.SystemInformation> 類別的一些更有用的成員包括 <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>、<xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>、<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>和 <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>。</span><span class="sxs-lookup"><span data-stu-id="8d8b6-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8b6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d8b6-110">See also</span></span>

- <xref:System.Windows.Forms.SystemInformation>
- [<span data-ttu-id="8d8b6-111">Windows Forms 中的電源管理</span><span class="sxs-lookup"><span data-stu-id="8d8b6-111">Power Management in Windows Forms</span></span>](power-management-in-windows-forms.md)
