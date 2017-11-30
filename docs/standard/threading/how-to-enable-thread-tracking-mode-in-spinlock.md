---
title: "如何：啟用 SpinLock 中的執行緒追蹤模式"
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
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>如何：啟用 SpinLock 中的執行緒追蹤模式
<xref:System.Threading.SpinLock?displayProperty=nameWithType>是具有非常短的等候時間的情況下，您可以使用低層級的互斥鎖定。 <xref:System.Threading.SpinLock>不重複執行。 在執行緒進入鎖定之後，它必須結束鎖定正確後，才可以一次進入。 一般而言，重新進入鎖定狀態的任何嘗試會導致死結，死結 （deadlock） 可以是很難偵錯。 協助程式開發，<xref:System.Threading.SpinLock?displayProperty=nameWithType>支援一個執行緒追蹤模式，造成執行緒嘗試重新輸入已經保留的鎖定時擲回例外狀況。 這可讓您更輕鬆地找出的鎖定不結束正常的點。 您可以藉由開啟執行緒追蹤模式<xref:System.Threading.SpinLock>建構函式會採用布林值的輸入參數，並傳入的引數`true`。 開發和測試階段完成之後，關閉執行緒追蹤模式，以提升效能。  
  
## <a name="example"></a>範例  
 下列範例會示範執行緒追蹤模式。 正確地結束鎖定行標記為註解來模擬發生編碼錯誤，導致其中一個下列結果：  
  
-   如果擲回例外狀況<xref:System.Threading.SpinLock>使用的引數建立`true`(`True`在 Visual Basic 中)。  
  
-   如果發生死結<xref:System.Threading.SpinLock>使用的引數建立`false`(`False`在 Visual Basic 中)。  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>另請參閱  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
