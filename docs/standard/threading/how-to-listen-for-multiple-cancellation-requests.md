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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 397de114a3d8c3cbcfbc8ab55e4dbaf45ca9b652
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>如何：接聽多個取消要求
此範例顯示如何同時接聽兩個取消權杖，讓您可以在其中一個權杖要求作業時將作業取消。  
  
> [!NOTE]
>  啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。 這個錯誤是良性的。 您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。 若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消核取 [工具]、[選項]、[偵錯]、[一般] 下的 [Just My Code] 核取方塊即可。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> 方法是用來將兩個權杖聯結為一個權杖。 這可將權杖傳遞給僅採取一個取消權杖作為引數的方法。 此範例示範一個常見的案例，其中方法必須同時觀察從類別外部傳入的權杖，以及類別內部產生的權杖。  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 當連結的權杖擲回 <xref:System.OperationCanceledException> 時，傳遞給例外狀況的權杖是連結的權杖，而非其中一個前置項權杖。 若要判斷哪一個權杖已取消，請直接檢查前置項權杖的狀態。  
  
 在此範例中，應該永遠不會擲回 <xref:System.AggregateException>，但是卻在這裡攔截到它，是因為在真實案例中，<xref:System.OperationCanceledException> 以外從工作委派擲回的任何其他例外狀況，都會包裝在 <xref:System.OperationCanceledException> 中。  
  
## <a name="see-also"></a>請參閱  
 [Managed 執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)
