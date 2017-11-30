---
title: "如何：列舉列印佇列的子集"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 393d1692526551b1eb9aa16f48d3c78c3cd6692f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="0d816-102">如何：列舉列印佇列的子集</span><span class="sxs-lookup"><span data-stu-id="0d816-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="0d816-103">管理印表機的全公司的設定資訊技術 (IT) 專業人員所面臨的常見情況是產生一份具有特定特性的印表機。</span><span class="sxs-lookup"><span data-stu-id="0d816-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="0d816-104">這項功能由<xref:System.Printing.PrintServer.GetPrintQueues%2A>方法<xref:System.Printing.PrintServer>物件和<xref:System.Printing.EnumeratedPrintQueueTypes>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="0d816-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d816-105">範例</span><span class="sxs-lookup"><span data-stu-id="0d816-105">Example</span></span>  
 <span data-ttu-id="0d816-106">在下列範例程式碼一開始會建立指定的特性，我們要列出的列印佇列的旗標的陣列。</span><span class="sxs-lookup"><span data-stu-id="0d816-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="0d816-107">在此範例中，我們正在為列印伺服器上本機安裝，並共用的列印佇列。</span><span class="sxs-lookup"><span data-stu-id="0d816-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="0d816-108"><xref:System.Printing.EnumeratedPrintQueueTypes>列舉型別提供許多其他的可能性。</span><span class="sxs-lookup"><span data-stu-id="0d816-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="0d816-109">程式碼接著會建立<xref:System.Printing.LocalPrintServer>物件的類別衍生自<xref:System.Printing.PrintServer>。</span><span class="sxs-lookup"><span data-stu-id="0d816-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="0d816-110">本機列印伺服器是應用程式執行所在的電腦。</span><span class="sxs-lookup"><span data-stu-id="0d816-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="0d816-111">最後一個的重要步驟是將陣列傳遞給<xref:System.Printing.PrintServer.GetPrintQueues%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="0d816-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="0d816-112">最後，結果會呈現給使用者。</span><span class="sxs-lookup"><span data-stu-id="0d816-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="0d816-113">您可以擴充這個範例有`foreach`迴圈每個列印佇列會逐步執行進一步的檢測。</span><span class="sxs-lookup"><span data-stu-id="0d816-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="0d816-114">比方說，您無法篩選出印表機，讓迴圈呼叫不支援雙面列印每個列印佇列<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>方法，並測試傳回值出現的雙工。</span><span class="sxs-lookup"><span data-stu-id="0d816-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d816-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d816-115">See Also</span></span>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="0d816-116">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="0d816-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="0d816-117">列印概觀</span><span class="sxs-lookup"><span data-stu-id="0d816-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="0d816-118">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="0d816-118">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)
