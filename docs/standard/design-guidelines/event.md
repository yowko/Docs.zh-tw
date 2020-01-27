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
ms.openlocfilehash: b44ee5933f8629b4dddbf3be1b79b2e77b0254f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741683"
---
# <a name="event-design"></a>事件設計
事件是最常使用的回呼形式（可讓架構呼叫使用者程式碼的結構）。 其他回呼機制包含取得委派、虛擬成員和以介面為基礎之外掛程式的成員。來自可用性研究的資料表示大部分的開發人員都使用事件，而不是使用其他回呼機制. 事件與 Visual Studio 和多種語言完美整合。

 請務必注意，有兩個事件群組：在系統狀態變更之前引發的事件（稱為前置事件），以及狀態變更後引發的事件，稱為「後置事件」。 預先事件的範例會 `Form.Closing`，在表單關閉之前引發。 Post 事件的範例會 `Form.Closed`，這會在表單關閉後引發。

 ✔️確實會針對事件使用「引發」一詞，而非「引發」或「觸發程式」。

 ✔️確實使用 <xref:System.EventHandler%601?displayProperty=nameWithType>，而不是手動建立新的委派，以作為事件處理常式使用。

 ✔️考慮使用 <xref:System.EventArgs> 的子類別做為事件引數，除非您絕對確定事件永遠不需要將任何資料傳送至事件處理方法，在此情況下，您可以直接使用 `EventArgs` 類型。

 如果您使用 `EventArgs` 直接寄送 API，您永遠都無法在不中斷相容性的情況下，新增任何要攜帶事件的資料。 如果您使用子類別，即使一開始完全空白，您也可以在需要時將屬性新增至子類別。

 ✔️確實使用受保護的虛擬方法來引發每個事件。 這只適用于未密封類別上的非靜態事件，而不適用於結構、密封類別或靜態事件。

 方法的目的是要提供方法，讓衍生類別使用覆寫來處理事件。 覆寫是更有彈性、更快速且更自然的方式來處理衍生類別中的基類事件。 依照慣例，方法名稱的開頭應該是 "On"，後面接著事件的名稱。

 衍生的類別可以選擇不要在其覆寫中呼叫方法的基底實作為。 請不要在基類所需的方法中包含任何處理，就可以正確地運作。

 ✔️請對引發事件的受保護方法執行一個參數。

 參數應該命名為 `e`，且應輸入為事件引數類別。

 當引發非靜態事件時，❌ 不要傳遞 null 做為寄件者。

 ✔️在引發靜態事件時，傳遞 null 做為寄件者。

 當引發事件時，❌ 不會傳遞 null 做為事件資料參數。

 如果您不想要將任何資料傳遞至事件處理方法，則應該傳遞 `EventArgs.Empty`。 開發人員預期此參數不是 null。

 ✔️考慮引發終端使用者可以取消的事件。 這只適用于前置事件。

 使用 <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> 或其子類別做為事件引數，以允許終端使用者取消事件。

### <a name="custom-event-handler-design"></a>自訂事件處理常式設計
 在某些情況下，`EventHandler<T>` 無法使用，例如，當架構需要使用舊版 CLR 時，這不支援泛型。 在這種情況下，您可能需要設計和開發自訂事件處理常式委派。

 ✔️針對事件處理常式使用 void 的傳回類型。

 事件處理常式可以叫用多個事件處理方法，可能會在多個物件上叫用。 如果允許事件處理方法傳回值，每個事件調用都會有多個傳回值。

 ✔️確實使用 `object` 做為事件處理常式第一個參數的型別，並將它呼叫 `sender`。

 ✔️確實使用 <xref:System.EventArgs?displayProperty=nameWithType> 或其子類別做為事件處理常式第二個參數的型別，並將它呼叫 `e`。

 ❌ 在事件處理常式上不能有兩個以上的參數。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
