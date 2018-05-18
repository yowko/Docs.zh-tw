---
title: 如何：啟用 SpinLock 中的執行緒追蹤模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93303ba84538a85350fd09b78f9963558668b91b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>如何：啟用 SpinLock 中的執行緒追蹤模式
<xref:System.Threading.SpinLock?displayProperty=nameWithType> 是低階的互斥鎖定，適用於等候時間非常短的案例。 <xref:System.Threading.SpinLock> 是不可重入的。 當執行緒進入鎖定之後，必須正確地結束鎖定之後，才可再次進入。 一般而言，重新進入鎖定的任何嘗試都會導致死結，而死結可能很難偵錯。 為了協助開發，<xref:System.Threading.SpinLock?displayProperty=nameWithType> 支援一個執行緒追蹤模式，此模式會導致在執行緒嘗試重新進入它已經保留的鎖定時擲回例外狀況。 這可讓您更容易找出未正確結束鎖定的點。 您可以使用採取布林值輸入參數的 <xref:System.Threading.SpinLock> 建構函式並傳入 `true` 的引數，來開啟執行緒追蹤模式。 當您完成開發和測試階段之後，關閉執行緒追蹤模式以提升效能。  
  
## <a name="example"></a>範例  
 下列範例示範執行緒追蹤模式。 正確結束鎖定的程式碼行會標記為註解，以模擬會導致其中一個下列結果的編碼錯誤：  
  
-   如果 <xref:System.Threading.SpinLock> 是使用 `true` (在 Visual Basic 中為 `True`) 的引數所建立，即會擲回例外狀況。  
  
-   如果 <xref:System.Threading.SpinLock> 是使用 `false` (在 Visual Basic 中為 `False`) 的引數所建立，即會鎖死。  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>請參閱  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
