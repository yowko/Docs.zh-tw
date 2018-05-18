---
title: 前景和背景執行緒
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 476dc75a569224db405eb7498ecb35eb6bda24d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="foreground-and-background-threads"></a>前景和背景執行緒
受控執行緒可以是背景執行緒或前景執行緒。 背景執行緒與前景執行緒完全相同，但有一個例外：背景執行緒不會讓受控的執行環境保持執行狀態。 一旦受控處理序 (其中的 .exe 檔案為受控組件) 的所有前景執行緒都已停止之後，系統就會停止所有背景執行緒並關閉。  
  
> [!NOTE]
>  當執行階段因為處理序正在關閉而停止背景執行緒時，執行緒中不會擲回任何例外狀況。 不過，當執行緒因為 <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> 方法卸載應用程式定義域而停止時，前景和背景執行緒中都會擲回 <xref:System.Threading.ThreadAbortException>。  
  
 使用 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> 屬性，來判斷執行緒是否為背景或前景執行緒，或變更其狀態。 您隨時都能藉由將執行緒的 <xref:System.Threading.Thread.IsBackground%2A> 屬性設為 `true`，來將其變更為背景執行緒。  
  
> [!IMPORTANT]
>  執行緒的前景或背景狀態不會影響執行緒中未處理的例外狀況結果。 在 .NET Framework 2.0 版中，前景或背景執行緒中未處理的例外狀況會導致應用程式終止。 請參閱[受控執行緒中的例外狀況](../../../docs/standard/threading/exceptions-in-managed-threads.md)。  
  
 屬於受控執行緒集區的執行緒 (也就是其 <xref:System.Threading.Thread.IsThreadPoolThread%2A> 屬性為 `true` 的執行緒) 是背景執行緒。 從非受控碼進入受控執行環境的所有執行緒都會標示為背景執行緒。 藉由建立並啟動新 <xref:System.Threading.Thread> 物件而產生的所有執行緒預設均為前景執行緒。  
  
 如果您使用執行緒來監視活動 (例如通訊端連線)，請將它的 <xref:System.Threading.Thread.IsBackground%2A> 屬性設為 `true`，讓執行緒不會阻止您的處理序終止。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
