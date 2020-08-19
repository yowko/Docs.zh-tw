---
title: 註冊取消要求的回呼
ms.date: 08/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: faa8dada5779f6eaee7a60e6210ec604f5fb4680
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608452"
---
# <a name="register-callbacks-for-cancellation-requests"></a>註冊取消要求的回呼

瞭解如何註冊將在屬性變成 true 時叫用的委派 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 。 當對建立 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 權杖的物件進行呼叫時，此值會從 false 變更為 true。 使用這項技術來取消非原生支援整合取消架構的非同步作業，以及解除封鎖可能等候非同步作業完成的方法。

> [!NOTE]
> 啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。 這個錯誤是良性的。 您可以按 <kbd>F5</kbd> 繼續執行，並查看下列範例中示範的例外狀況處理行為。 若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消核取 [工具]、[選項]、[偵錯]、[一般]**** 下的 [Just My Code] 核取方塊即可。

## <a name="example"></a>範例

在下列範例中，<xref:System.Net.WebClient.CancelAsync%2A> 方法註冊為透過取消語彙基元要求取消時，所要叫用的方法。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

如果註冊回呼時，已經要求過取消，仍然保證會呼叫回呼。 在這個特殊案例中，如果沒有任何非同步作業正在進行中，<xref:System.Net.WebClient.CancelAsync%2A> 方法就不會做任何事，所以呼叫方法一定是安全的。

## <a name="see-also"></a>另請參閱

- [受控執行緒中的取消作業](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
