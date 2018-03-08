---
title: "計時器"
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
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 80b4cee03e934d3aec98ca323aac43f934c56455
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="timers"></a>計時器
計時器是輕量型物件，可讓您指定要在指定時間呼叫的委派。 執行緒集區中的執行緒會執行等候作業。  
  
 使用 <xref:System.Threading.Timer?displayProperty=nameWithType> 類別的方式相當直接明瞭。 您建立**計時器**，將 <xref:System.Threading.TimerCallback> 委派傳遞至回呼方法、代表將傳遞至回呼之狀態的物件、最初引發時間，以及代表介於回呼引動過程間之期間的時間。 若要取消擱置中的計時器，請呼叫 **Timer.Dispose** 函式。  
  
> [!NOTE]
>  另外還有兩個計時器類別。 <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> 類別是搭配視覺化設計工具運作且要用於使用者介面內容的控制項；它會在使用者介面執行緒上引發事件。 <xref:System.Timers.Timer?displayProperty=nameWithType> 類別衍生自<xref:System.ComponentModel.Component>，因此可將它與視覺化設計工具搭配使用；它也會引發事件，但會在 <xref:System.Threading.ThreadPool> 執行緒上引發它們。 <xref:System.Threading.Timer?displayProperty=nameWithType> 類別會在 <xref:System.Threading.ThreadPool> 執行緒上進行回呼，完全不會使用事件模型。 它也會將狀態物件提供給回呼方法，其他計時器則不會。 它極為精簡。  
  
 下列程式碼範例會在一秒 (1000 毫秒) 後啟動計時器且每秒都有滴答聲，直到您按下 **Enter** 鍵為止。 包含計時器參考的變數是類別層級的欄位，確保計時器仍在執行時不會受到記憶體回收限制。 如需積極型記憶體回收的詳細資訊，請參閱 <xref:System.GC.KeepAlive%2A>。  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.Timer>  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
