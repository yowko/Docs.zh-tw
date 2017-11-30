---
title: "如何：接聽多個取消要求"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36cf338a15ad3f7d234f902c50a2dbb1b2e95847
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>如何：接聽多個取消要求
這個範例示範如何取消語彙基元兩個同時接聽，讓您可以取消作業，如果 token，或是要求它。  
  
> [!NOTE]
>  啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。 這個錯誤是良性的。 您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。 若要防止 Visual Studio 的第一個錯誤的中斷，只要取消核取下的 [Just My Code] 核取方塊**工具、 選項、 偵錯、 一般**。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A>方法用來將兩個權杖聯結到一個權杖。 這可讓要傳遞給這些方法會採用一個取消語彙基元當做引數的語彙基元。 此範例示範常見的案例中的方法必須觀察這兩個語彙基元從傳入外部類別，而產生的類別內的語彙基元。  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 連結的語彙基元會擲回<xref:System.OperationCanceledException>，傳遞的例外狀況的語彙基元是連結的語彙基元，不是其中一個前置項語彙基元。 若要判斷哪一個語彙基元已取消，直接簽前置 token 的狀態。  
  
 在此範例中，<xref:System.AggregateException>應該永遠不會擲回，但是它會攔截到這裡因為真實世界案例中以外的任何其他例外狀況<xref:System.OperationCanceledException>擲回的工作委派會包裝在<xref:System.OperationCanceledException>。  
  
## <a name="see-also"></a>另請參閱  
 [Managed 執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)
