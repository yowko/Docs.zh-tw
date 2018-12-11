---
title: 事件設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
author: KrzysztofCwalina
ms.openlocfilehash: 54f98b3c685b77ecb9fe659522c599662aa8243c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129086"
---
# <a name="event-design"></a>事件設計
事件是最常使用的回呼 （允許呼叫使用者程式碼架構的建構）。 其他回呼機制包括做委派、 虛擬成員，以及以介面為基礎的隨插即用集的成員。資料可用性研究表示大部分的開發人員可以更輕鬆地使用事件，比使用其他回呼機制。 使用 Visual Studio 和許多語言妥善整合事件。  
  
 請務必請注意，有兩個群組的事件： 狀態系統的變更，呼叫前的事件，以及之後的狀態變更時，引發的事件之前引發的事件呼叫後的事件。 前的事件的範例是`Form.Closing`，這會引發一個表單關閉之前。 過去事件的範例是`Form.Closed`，表單關閉之後，這會引發。  
  
 **✓ DO** 使用詞彙 「 引發 」 事件，而非 「 引發 」 或 「 觸發程序。 」  
  
 **✓ DO** 使用 <xref:System.EventHandler%601?displayProperty=nameWithType>而不是以手動方式建立新的委派來做為事件處理常式。  
  
 **✓ CONSIDER** 使用的子類別 <xref:System.EventArgs> 當做事件引數，除非您完全確定事件則不需要執行任何資料的事件處理方法，在這種情況下您可以使用 `EventArgs` 直接輸入。  
  
 如果您在出貨 API 使用`EventArgs`直接，您將永遠無法新增任何要執行與事件，而不會中斷相容性的資料。 如果您使用子類別，甚至如果一開始完全空白的您將能夠加入子類別時所需的屬性。  
  
 **✓ DO** 用來引發的每個事件的受保護的虛擬方法。 這只適用於非密封類別，不適用於結構、 密封的類別或靜態事件上的非靜態事件。  
  
 方法的目的是提供方法讓衍生的類別處理使用覆寫的事件。 覆寫是更有彈性、 快速且更自然的方式來處理在衍生類別中的基底類別事件。 依照慣例，方法的名稱應以 「 On 」 開頭，且後面接著的事件名稱。  
  
 在衍生的類別不可以選擇在其覆寫中呼叫方法的基底實作。 做好這不是為了正常運作的基底類別方法中包含任何處理。  
  
 **✓ DO** 採用一個參數會引發事件的受保護方法。  
  
 參數應該命名為`e`和應該鍵入為事件引數類別。  
  
 **X DO NOT** 時引發的非靜態事件傳遞 null 做為傳送者。  
  
 **✓ DO** 時引發的靜態事件傳遞 null 做為傳送者。  
  
 **X DO NOT** 時引發事件會傳遞 null 做為事件資料參數。  
  
 您應傳入`EventArgs.Empty`如果您不想要傳遞至事件處理常式方法的任何資料。 開發人員預期此參數不可以是 null。  
  
 **✓ CONSIDER** 引發事件，使用者可以取消。 這只適用於前的事件。  
  
 使用<xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>或其為允許使用者取消事件的事件引數的子類別。  
  
### <a name="custom-event-handler-design"></a>自訂事件處理常式設計  
 某些情況下，在其中`EventHandler<T>`無法使用，例如當架構需要使用較早版本的 CLR，因為不支援泛型。 在這種情況下，您可能需要設計和開發自訂事件處理常式委派。  
  
 **✓ DO** 用於事件處理常式的傳回類型為 void。  
  
 事件處理常式可以叫用處理常式方法，可能是在多個物件上的多個事件。 如果允許事件處理方法的傳回值，會有多個傳回的值，每個事件引動過程。  
  
 **✓ DO** 使用 `object` 做為事件處理常式的第一個參數的類型，並為它 `sender`。  
  
 **✓ DO** 使用 <xref:System.EventArgs?displayProperty=nameWithType> 或做為事件處理常式中，第二個參數的類型及其子類別，並為它 `e`。  
  
 **X DO NOT** 上事件處理常式有兩個以上的參數。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
