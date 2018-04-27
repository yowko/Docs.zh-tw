---
title: 事件設計
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3d66d4e137c52310710f8b178167ceb3cca042c7
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="event-design"></a>事件設計
事件是最常使用的回呼 （允許呼叫使用者程式碼架構的建構） 形式。 其他的回撥機制包括委派、 虛擬成員和介面為基礎的外掛程式取得的成員。資料可用性研究表示大部分的開發人員可以更輕鬆地使用事件，比使用其他的回撥機制。 事件會正確地切割整合與 Visual Studio 和許多語言。  
  
 請務必請注意，有兩個群組的事件： 狀態系統的變更，呼叫前的事件，以及之後的狀態變更時，引發的事件之前引發的事件呼叫後的事件。 預先事件的一個範例是`Form.Closing`，在關閉表單之前引發的。 後續事件的一個範例是`Form.Closed`，表單關閉之後，這會引發。  
  
 **✓ 不要**使用詞彙 「 引發 」 事件，而非 「 引發 」 或 「 觸發程序。 」  
  
 **✓ 不要**使用<xref:System.EventHandler%601?displayProperty=nameWithType>而不是以手動方式建立新的委派來做為事件處理常式。  
  
 **✓ 考慮**使用的子類別<xref:System.EventArgs>當做事件引數，除非您完全確定事件則不需要執行任何資料的事件處理方法，在這種情況下您可以使用`EventArgs`直接輸入。  
  
 如果您在出貨 API 使用`EventArgs`直接管理，您絕對不會再加入要執行與事件，而不會中斷相容性的任何資料。 如果您使用子類別，即使如果一開始會完全空白的您將能夠將屬性加入至時所需的子類別。  
  
 **✓ 不要**用來引發的每個事件的受保護的虛擬方法。 這只適用於未密封的類別、 結構、 密封的類別，或靜態事件上的非靜態事件。  
  
 方法的目的是要提供一個方式來處理事件使用覆寫衍生類別。 覆寫是更有彈性、 更快更自然的方式，來處理基底類別衍生類別中的事件。 依照慣例，方法名稱應以 「 On 」 開頭，且後面的事件名稱。  
  
 在衍生的類別不可以選擇在其覆寫中呼叫方法的基底實作。 準備這個方法所需的正確運作的基底類別中不能包含任何處理。  
  
 **✓ 不要**採用一個參數會引發事件的受保護方法。  
  
 參數命名為`e`和輸入應該為事件引數類別。  
  
 **X 不**時引發的非靜態事件傳遞 null 做為傳送者。  
  
 **✓ 不要**時引發的靜態事件傳遞 null 做為傳送者。  
  
 **X 不**時引發事件會傳遞 null 做為事件資料參數。  
  
 您應該傳遞`EventArgs.Empty`若不想將任何資料傳遞至事件處理方法。 開發人員希望此參數不可以是 null。  
  
 **✓ 考慮**引發事件，使用者可以取消。 這只適用於預先事件。  
  
 使用<xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>或其為允許使用者在取消事件的事件引數的子類別。  
  
### <a name="custom-event-handler-design"></a>自訂事件處理常式設計  
 某些情況下，在其中`EventHandler<T>`無法使用，例如當架構需要使用較早版本的 CLR，因為不支援泛型。 在這種情況下，您可能需要設計和開發自訂的事件處理常式委派。  
  
 **✓ 不要**用於事件處理常式的傳回類型為 void。  
  
 事件處理常式可以叫用多個事件處理常式方法，可能位於多個物件。 允許事件處理方法會傳回值，如果有多個傳回值，每個事件的引動過程。  
  
 **✓ 不要**使用`object`做為事件處理常式的第一個參數的類型，並為它`sender`。  
  
 **✓ 不要**使用<xref:System.EventArgs?displayProperty=nameWithType>或做為事件處理常式中，第二個參數的類型及其子類別，並為它`e`。  
  
 **X 不**上事件處理常式有兩個以上的參數。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
