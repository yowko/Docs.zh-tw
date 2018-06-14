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
ms.openlocfilehash: 3e616b3b61b4b1b561d5bdb7e51525f391901a22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543585"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>如何：列舉列印佇列的子集
管理印表機的全公司的設定資訊技術 (IT) 專業人員所面臨的常見情況是產生一份具有特定特性的印表機。 這項功能由<xref:System.Printing.PrintServer.GetPrintQueues%2A>方法<xref:System.Printing.PrintServer>物件和<xref:System.Printing.EnumeratedPrintQueueTypes>列舉型別。  
  
## <a name="example"></a>範例  
 在下列範例程式碼一開始會建立指定的特性，我們要列出的列印佇列的旗標的陣列。 在此範例中，我們正在為列印伺服器上本機安裝，並共用的列印佇列。 <xref:System.Printing.EnumeratedPrintQueueTypes>列舉型別提供許多其他的可能性。  
  
 程式碼接著會建立<xref:System.Printing.LocalPrintServer>物件的類別衍生自<xref:System.Printing.PrintServer>。 本機列印伺服器是應用程式執行所在的電腦。  
  
 最後一個的重要步驟是將陣列傳遞給<xref:System.Printing.PrintServer.GetPrintQueues%2A>方法。  
  
 最後，結果會呈現給使用者。  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 您可以擴充這個範例有`foreach`迴圈每個列印佇列會逐步執行進一步的檢測。 比方說，您無法篩選出印表機，讓迴圈呼叫不支援雙面列印每個列印佇列<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>方法，並測試傳回值出現的雙工。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)
