---
title: "COM 包裝函式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM 可呼叫包裝函式"
  - "COM Interop, COM 包裝函式"
  - "COM 包裝函式"
  - "COM, 包裝函式"
  - "與 Unmanaged 程式碼的互通, COM 包裝函式"
  - "包裝函式類別"
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# COM 包裝函式
COM 在下列幾個重要的方面有別於 .NET Framework 物件模型：  
  
-   COM 物件的用戶端必須管理這些物件的存留期 \(Lifetime\)；Common Language Runtime 則會管理在它環境下之物件的存留期。  
  
-   COM 物件的用戶端會藉由要求提供某項服務的介面並且取回介面指標，來判斷這項服務是否可以使用。  .NET 物件的用戶端可以使用反映 \(Reflection\) 來取得物件功能的描述。  
  
-   .NET 物件是位於由 .NET Framework 執行環境所管理的記憶體中。  基於效能的理由，這個執行環境可以在記憶體中四處移動物件，並且更新它所移動之物件的所有參考。  一旦取得某一物件的指標之後，Unmanaged 用戶端必須依賴這個物件保持在同一位置。  這些用戶端沒有能夠處理位置不固定之物件的機制。  
  
 為了克服這些差異，執行階段提供了一些包裝函式類別，可以讓 Managed 和 Unmanaged 用戶端兩者都認為它們是在各自的環境中呼叫物件。  每當 Managed 用戶端呼叫 COM 物件上的方法時，執行階段就會建立[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md) \(RCW\)。  這些 RCW 會抽走 Managed 和 Unmanaged 參考機制之間的差異 \(以及一些其他的東西\)。  執行階段也會建立 [COM 可呼叫包裝函式](../../../docs/framework/interop/com-callable-wrapper.md) \(CCW\) 來反轉處理序，讓 COM 用戶端能夠不著痕跡地呼叫 .NET 物件上的方法。  如下圖所示，呼叫程式碼的觀點將決定執行階段會建立哪一種包裝函式類別。  
  
 ![COM 包裝函式概觀](../../../docs/framework/interop/media/bidirectional.gif "bidirectional")  
COM 包裝函式概觀  
  
 在大部分情況下，由 Runtime 產生的標準 RCW 或 CCW，對於在 COM 和 .NET Framework 之間的跨界限呼叫，都能提供適切的封送處理。  使用自訂屬性 \(Attribute\)，您可以選擇性地調整執行階段表示 Managed 和 Unmanaged 程式碼的方式。  
  
## 請參閱  
 [Advanced COM Interoperability](http://msdn.microsoft.com/zh-tw/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md)   
 [COM 可呼叫包裝函式](../../../docs/framework/interop/com-callable-wrapper.md)   
 [Customizing Standard Wrappers](http://msdn.microsoft.com/zh-tw/c40d089b-6a3c-41b5-a20d-d760c215e49d)   
 [How to: Customize Runtime Callable Wrappers](http://msdn.microsoft.com/zh-tw/4a4bb3da-4d60-4517-99f2-78d46a681732)