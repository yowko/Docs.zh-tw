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
ms.openlocfilehash: bf45d6fb3fb161ca5171e94b9ab7af1e0e6f0c3d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786933"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>如何：列舉列印佇列的子集
管理印表機的全公司組的資訊技術 (IT) 專業人員所面臨的常見情況是產生一份具有特定特性的印表機。 此功能會由<xref:System.Printing.PrintServer.GetPrintQueues%2A>方法<xref:System.Printing.PrintServer>物件和<xref:System.Printing.EnumeratedPrintQueueTypes>列舉型別。  
  
## <a name="example"></a>範例  
 在下列範例程式碼一開始會建立指定我們想要列出之列印佇列的特性的旗標的陣列。 在此範例中，我們正在尋找的列印伺服器上本機安裝和共用的列印佇列。 <xref:System.Printing.EnumeratedPrintQueueTypes>列舉提供許多其他的可能性。  
  
 程式碼接著會建立<xref:System.Printing.LocalPrintServer>物件的類別衍生自<xref:System.Printing.PrintServer>。 本機列印伺服器是應用程式執行所在的電腦。  
  
 最後一個重要步驟是將傳遞的陣列<xref:System.Printing.PrintServer.GetPrintQueues%2A>方法。  
  
 最後，結果會呈現給使用者。  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 您可以擴充此範例由`foreach`透過每個列印佇列的步驟執行進一步的迴圈檢測。 比方說，您無法篩選出由迴圈呼叫不支援雙面列印的印表機每個列印佇列<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>方法，測試傳回的值是否存在的雙面列印。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)
