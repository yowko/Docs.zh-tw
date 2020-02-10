---
title: 如何：列舉列印佇列的子集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: aae41931f012f6d34fc057fdd6ee9fc9baab6e7b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094536"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a><span data-ttu-id="ee22f-102">如何：列舉列印佇列的子集</span><span class="sxs-lookup"><span data-stu-id="ee22f-102">How to: Enumerate a Subset of Print Queues</span></span>
<span data-ttu-id="ee22f-103">由資訊技術（IT）專業人員負責管理一組全公司印表機的常見情況，就是產生具有特定特性的印表機清單。</span><span class="sxs-lookup"><span data-stu-id="ee22f-103">A common situation faced by information technology (IT) professionals managing a company-wide set of printers is to generate a list of printers having certain characteristics.</span></span> <span data-ttu-id="ee22f-104">這項功能是由 <xref:System.Printing.PrintServer> 物件的 <xref:System.Printing.PrintServer.GetPrintQueues%2A> 方法和 <xref:System.Printing.EnumeratedPrintQueueTypes> 列舉所提供。</span><span class="sxs-lookup"><span data-stu-id="ee22f-104">This functionality is provided by the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method of a <xref:System.Printing.PrintServer> object and the <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee22f-105">範例</span><span class="sxs-lookup"><span data-stu-id="ee22f-105">Example</span></span>  
 <span data-ttu-id="ee22f-106">在下列範例中，程式碼一開始會建立一組旗標，以指定要列出的列印佇列特性。</span><span class="sxs-lookup"><span data-stu-id="ee22f-106">In the example below, the code begins by creating an array of flags that specify the characteristics of the print queues we want to list.</span></span> <span data-ttu-id="ee22f-107">在此範例中，我們要尋找在列印伺服器本機上安裝並共用的列印佇列。</span><span class="sxs-lookup"><span data-stu-id="ee22f-107">In this example, we are looking for print queues that are installed locally on the print server and are shared.</span></span> <span data-ttu-id="ee22f-108"><xref:System.Printing.EnumeratedPrintQueueTypes> 列舉可提供許多其他的可能性。</span><span class="sxs-lookup"><span data-stu-id="ee22f-108">The <xref:System.Printing.EnumeratedPrintQueueTypes> enumeration provides many other possibilities.</span></span>  
  
 <span data-ttu-id="ee22f-109">然後，程式碼會建立一個 <xref:System.Printing.LocalPrintServer> 物件，這是一個衍生自 <xref:System.Printing.PrintServer>的類別。</span><span class="sxs-lookup"><span data-stu-id="ee22f-109">The code then creates a <xref:System.Printing.LocalPrintServer> object, a class derived from <xref:System.Printing.PrintServer>.</span></span> <span data-ttu-id="ee22f-110">本機列印伺服器是正在執行應用程式的電腦。</span><span class="sxs-lookup"><span data-stu-id="ee22f-110">The local print server is the computer on which the application is running.</span></span>  
  
 <span data-ttu-id="ee22f-111">最後一個重要步驟是將陣列傳遞給 <xref:System.Printing.PrintServer.GetPrintQueues%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ee22f-111">The last significant step is to pass the array to the <xref:System.Printing.PrintServer.GetPrintQueues%2A> method.</span></span>  
  
 <span data-ttu-id="ee22f-112">最後，結果會呈現給使用者。</span><span class="sxs-lookup"><span data-stu-id="ee22f-112">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 <span data-ttu-id="ee22f-113">您可以藉由讓 `foreach` 迴圈逐步執行每個列印佇列進行進一步的篩選，來擴充此範例。</span><span class="sxs-lookup"><span data-stu-id="ee22f-113">You could extend this example by having the `foreach` loop that steps through each print queue do further screening.</span></span> <span data-ttu-id="ee22f-114">例如，您可以讓迴圈呼叫每個列印佇列的 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> 方法，並測試傳回的值是否存在雙工，以將不支援雙面列印的印表機螢幕出。</span><span class="sxs-lookup"><span data-stu-id="ee22f-114">For example, you could screen out printers that do not support two-sided printing by having the loop call each print queue's <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method and test the returned value for the presence of duplexing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee22f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee22f-115">See also</span></span>

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="ee22f-116">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="ee22f-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="ee22f-117">列印概觀</span><span class="sxs-lookup"><span data-stu-id="ee22f-117">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="ee22f-118">Microsoft XPS 檔寫入器</span><span class="sxs-lookup"><span data-stu-id="ee22f-118">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)
