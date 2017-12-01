---
title: "Interlocked 作業"
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
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 122058b7e826e27fe6c60c5b07610f7c63e64f78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="interlocked-operations"></a>Interlocked 作業
<xref:System.Threading.Interlocked>類別提供方法，以同步存取由多個執行緒共用的變數。 如果變數位於共用的記憶體中，則不同處理序的執行緒可以使用這個機制。 Interlocked 作業不可部分完成，亦即，整個作業是一個單位，同一個變數上的另一個 Interlocked 作業不可將此 Interlocked 作業中斷。 在使用先佔式多執行緒的作業系統中，這一點很重要，因為執行緒可在從記憶體位址載入值後便加以暫停，而不致於有機會受到修改並儲存。  
  
 <xref:System.Threading.Interlocked>類別會提供下列作業：  
  
-   在.NET Framework 2.0 版中，<xref:System.Threading.Interlocked.Add%2A>方法將變數加入整數值，並傳回新變數的值。  
  
-   在.NET Framework 2.0 版中，<xref:System.Threading.Interlocked.Read%2A>方法讀取的 64 位元整數值，成為不可部分完成的作業。 這在 32 位元作業系統上很實用，因為讀取 64 位元的整數通常不是不可部分完成的作業。  
  
-   <xref:System.Threading.Interlocked.Increment%2A>和<xref:System.Threading.Interlocked.Decrement%2A>方法遞增或遞減的變數，並傳回產生的值。  
  
-   <xref:System.Threading.Interlocked.Exchange%2A>方法會執行不可部分完成的值交換中指定的變數，將該值傳回並以新值取代。 在 .NET Framework 2.0 版中，這個方法的泛型多載可用來對任何參考型別的變數執行這項交換。 請參閱 <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>。  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A>方法也交換兩個值，但視比較的結果。 在 .NET Framework 2.0 版中，這個方法的泛型多載可用來對任何參考型別的變數執行這項交換。 請參閱 <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>。  
  
 現代處理器的方法上<xref:System.Threading.Interlocked>通常可由單一指令實作類別。 因此，這些方法能提供極高效能的同步處理作業，並可用來建置更高層級的同步處理機制，例如微調鎖定。  
  
 如需範例，會使用<xref:System.Threading.Monitor>和<xref:System.Threading.Interlocked>類別的組合，請參閱[監視器](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)。  
  
## <a name="compareexchange-example"></a>CompareExchange 範例  
 <xref:System.Threading.Interlocked.CompareExchange%2A>方法可以用來保護比簡單的遞增和遞減更複雜的計算。 下列範例示範安全執行緒方法，此方法可新增到儲存為浮點數的計算加總  (如整數、<xref:System.Threading.Interlocked.Add%2A>方法是比較簡單的解決方案。)如需完整的程式碼範例，請參閱的多載<xref:System.Threading.Interlocked.CompareExchange%2A>可接受單精確度和雙精度浮點引數 (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29>和<xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>)。  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Exchange 和 CompareExchange 的不具型別多載  
 <xref:System.Threading.Interlocked.Exchange%2A>和<xref:System.Threading.Interlocked.CompareExchange%2A>方法具有接受型別引數的多載<xref:System.Object>。 每個這些多載的第一個引數是`ref Object`(`ByRef … As Object`在 Visual Basic 中)，且型別安全需要變數傳遞給這個引數的類型可以是絕對<xref:System.Object>; 您只是無法轉換輸入的第一個引數<xref:System.Object>呼叫這些方法時。  
  
> [!NOTE]
>  在.NET Framework 2.0 版中，使用的泛型多載<xref:System.Threading.Interlocked.Exchange%2A>和<xref:System.Threading.Interlocked.CompareExchange%2A>方法，以交換強型別變數。  
  
 下列程式碼範例會示範 `ClassA` 型別的屬性，這種屬性只能設定一次，因為它可能會在 .NET Framework 1.0 或 1.1 版中實作。  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
