---
title: "事件設計 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "前事件"
  - "事件 [.NET Framework] 設計指導方針"
  - "成員設計方針的事件"
  - "事件處理常式 [.NET Framework] 事件設計方針"
  - "後續的事件"
  - "簽章，事件處理"
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 事件設計
事件是最常用的回呼 （允許呼叫使用者程式碼架構的建構） 形式。 其他回呼機制包括委派、 虛擬成員，而且介面架構外掛程式的成員。 資料可用性研究指出大多數開發人員可以更輕鬆地使用事件，比使用其他的回呼機制。 事件會妥善整合於 Visual Studio 和許多語言。  
  
 請務必請注意，有兩個群組的事件︰ 之前的狀態系統變更，名為預期的事件和事件引發之後的狀態變更時，所引發的事件呼叫後的事件。 前事件的範例是 `Form.Closing`, ，這在關閉表單之前引發。 過去事件的範例會 `Form.Closed`, ，表單關閉之後，這會引發。  
  
 **✓ 執行** 使用詞彙 「 引發 」 事件，而非 「 引發 」 或 「 觸發 」。  
  
 **✓ 執行** 使用 <xref:System.EventHandler%601?displayProperty=fullName> 而不是以手動方式建立新的委派，要做為事件處理常式。  
  
 **✓ 考慮** 使用的子類別 <xref:System.EventArgs> 當做事件引數，除非您真的確定事件永遠不需要執行任何資料的事件處理方法，在這種情況下您可以使用 `EventArgs` 直接輸入。  
  
 如果您在出貨 API 使用 `EventArgs` 直接，您絕對不會再新增要與事件保持相容性的情況下執行的任何資料。 如果您使用子類別，甚至是如果一開始會完全空白的您會將屬性加入時所需的子類別。  
  
 **✓ 執行** 使用受保護的虛擬方法來引發每一個事件。 這只適用於非密封類別，不適用於結構、 密封的類別或靜態事件上的非靜態事件。  
  
 方法的目的是要提供一個方式來處理事件使用覆寫衍生類別。 覆寫是更有彈性、 快速且更自然的方式來處理在衍生類別中的基底類別事件。 依照慣例，方法的名稱必須以 「 On 」 開頭，並運用事件的名稱。  
  
 在衍生的類別不可以選擇在其覆寫中呼叫方法的基底實作。 準備此方法所需的正確運作的基底類別中不能包含任何處理。  
  
 **✓ 執行** 採用一個參數的受保護的方法引發事件。  
  
 參數名稱應該是 `e` 和輸入應該為事件引數類別。  
  
 **X 不** 時引發的非靜態事件傳遞 null 做為寄件者。  
  
 **✓ 執行** 時引發靜態事件傳遞 null 做為寄件者。  
  
 **X 不** 時引發事件會傳遞 null 做為事件資料參數。  
  
 您應該傳遞 `EventArgs.Empty` 如果您不想將任何資料傳遞至事件處理方法。 開發人員預期這個參數不可以是 null。  
  
 **✓ 考慮** 引發事件，使用者可以取消。 這只適用於預期事件。  
  
 使用 <xref:System.ComponentModel.CancelEventArgs?displayProperty=fullName> 或其為允許使用者取消事件的事件引數的子類別。  
  
### 自訂事件處理常式設計  
 某些情況下，在其中 `EventHandler<T>` 無法使用，例如架構需要使用較早版本的 CLR 並不支援泛型。 在這種情況下，您可能需要設計和開發自訂事件處理常式委派。  
  
 **✓ 執行** 使用 void 傳回類型的事件處理常式。  
  
 事件處理常式可以叫用多個事件處理常式方法，可能位於多個物件。 允許事件處理方法的傳回值，如果有多個傳回的值，每個事件引動過程。  
  
 **✓ 執行** 使用 `object` 做為事件處理常式的第一個參數的類型，並稱之為 `sender`。  
  
 **✓ 執行** 使用 <xref:System.EventArgs?displayProperty=fullName> 或做為事件處理常式中，第二個參數的型別及其子類別，並稱之為 `e`。  
  
 **X 不** 之事件處理常式有兩個以上的參數。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)