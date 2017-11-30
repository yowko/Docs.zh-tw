---
title: "前景和背景執行緒"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ad427fc2c1175c0d9b333aa418aea039f11a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="foreground-and-background-threads"></a>前景和背景執行緒
Managed 的執行緒是背景執行緒或前景執行緒。 背景執行緒會與相同前景執行緒有一個例外狀況： 背景執行緒不會保存執行的 managed 的執行環境。 一旦所有的前景執行緒都已停止 （.exe 檔案是 managed 組件） 的受管理處理序中，系統就會停止所有的背景執行緒，並關閉。  
  
> [!NOTE]
>  當執行階段停止背景執行緒，因為處理序正在關閉時，執行緒擲不回任何例外狀況。 不過，當執行緒已停止，因為<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>方法卸載應用程式定義域，<xref:System.Threading.ThreadAbortException>前景和背景執行緒中擲回。  
  
 使用<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>屬性來判斷執行緒是背景或前景執行緒，或變更其狀態。 執行緒可以變更為背景執行緒上隨時藉由設定其<xref:System.Threading.Thread.IsBackground%2A>屬性`true`。  
  
> [!IMPORTANT]
>  前景或背景執行緒的狀態不會影響結果的執行緒中處理的例外狀況。 在.NET Framework 2.0 版中，在前景或背景執行緒中處理的例外狀況會導致應用程式終止。 請參閱[Managed 執行緒中的例外狀況](../../../docs/standard/threading/exceptions-in-managed-threads.md)。  
  
 執行緒屬於 managed 的執行緒集區 (也就是執行緒的<xref:System.Threading.Thread.IsThreadPoolThread%2A>屬性是`true`) 為背景執行緒。 從 unmanaged 程式碼進入 managed 的執行環境的所有執行緒都會都標示為背景執行緒。 建立並啟動新產生的所有執行緒<xref:System.Threading.Thread>物件會由預設前景執行緒。  
  
 如果您使用的執行緒來監視活動，例如通訊端連線中，設定其<xref:System.Threading.Thread.IsBackground%2A>屬性`true`，讓執行緒不會阻止您的處理序終止。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
