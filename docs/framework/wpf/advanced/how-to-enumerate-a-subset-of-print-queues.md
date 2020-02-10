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
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>如何：列舉列印佇列的子集
由資訊技術（IT）專業人員負責管理一組全公司印表機的常見情況，就是產生具有特定特性的印表機清單。 這項功能是由 <xref:System.Printing.PrintServer> 物件的 <xref:System.Printing.PrintServer.GetPrintQueues%2A> 方法和 <xref:System.Printing.EnumeratedPrintQueueTypes> 列舉所提供。  
  
## <a name="example"></a>範例  
 在下列範例中，程式碼一開始會建立一組旗標，以指定要列出的列印佇列特性。 在此範例中，我們要尋找在列印伺服器本機上安裝並共用的列印佇列。 <xref:System.Printing.EnumeratedPrintQueueTypes> 列舉可提供許多其他的可能性。  
  
 然後，程式碼會建立一個 <xref:System.Printing.LocalPrintServer> 物件，這是一個衍生自 <xref:System.Printing.PrintServer>的類別。 本機列印伺服器是正在執行應用程式的電腦。  
  
 最後一個重要步驟是將陣列傳遞給 <xref:System.Printing.PrintServer.GetPrintQueues%2A> 方法。  
  
 最後，結果會呈現給使用者。  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 您可以藉由讓 `foreach` 迴圈逐步執行每個列印佇列進行進一步的篩選，來擴充此範例。 例如，您可以讓迴圈呼叫每個列印佇列的 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> 方法，並測試傳回的值是否存在雙工，以將不支援雙面列印的印表機螢幕出。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [WPF 中的文件](documents-in-wpf.md)
- [列印概觀](printing-overview.md)
- [Microsoft XPS 檔寫入器](/windows/win32/printdocs/microsoft-xps-document-writer)
