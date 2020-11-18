---
title: 事件設計
ms.date: 10/22/2008
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: eee4b1a9e72c167b9b1e48a73dbb3f0528744bdc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821329"
---
# <a name="event-design"></a>事件設計
事件是最常用的回呼形式 (結構，可讓架構呼叫使用者程式碼) 。 其他回呼機制包括取得委派、虛擬成員和以介面為基礎之外掛程式的成員。可用性研究中的資料表示大部分的開發人員使用事件比使用其他回呼機制更熟悉。 事件與 Visual Studio 和許多語言緊密整合。

 請務必注意，有兩個事件群組：在系統狀態變更之前引發的事件（稱為「前置事件」）和狀態變更之後引發的事件（稱為「後續事件」）。 在 `Form.Closing` 關閉表單之前，會引發預先事件的範例。 後續事件的範例是 `Form.Closed` ，在關閉表單之後引發。

 ✔️請針對事件使用「引發」一詞，而不是「引發」或「觸發程式」。

 ✔️請使用 <xref:System.EventHandler%601?displayProperty=nameWithType> 而非手動建立新的委派，以作為事件處理常式使用。

 ✔️考慮使用的子類別 <xref:System.EventArgs> 做為事件引數，除非您絕對確定事件永遠不需要將任何資料傳送至事件處理方法，在此情況下，您可以直接使用 `EventArgs` 類型。

 如果您直接使用來傳送 API `EventArgs` ，您將無法在不中斷相容性的情況下，新增任何要與事件一起傳送的資料。 如果您使用子類別，即使一開始完全是空的，您也可以視需要將屬性加入子類別。

 ✔️使用受保護的虛擬方法來引發每個事件。 這僅適用于未密封類別上的非靜態事件，而不適用於結構、密封類別或靜態事件。

 方法的目的是要提供方法讓衍生類別使用覆寫來處理事件。 覆寫是在衍生類別中處理基類事件的更具彈性、更快速且更自然的方式。 依照慣例，方法名稱的開頭應該是 "On"，後面接著事件的名稱。

 衍生的類別可以選擇不在其覆寫中呼叫方法的基底實作為。 為此做好準備，方法是不要在基類所需的方法中包含任何處理程式，才能正確運作。

 ✔️會對引發事件的受保護方法採取一個參數。

 參數應該命名為 `e` ，而且應輸入為事件引數類別。

 ❌ 引發非靜態事件時，請勿傳遞 null 做為傳送者。

 當引發靜態事件時，✔️ DO 傳遞 null 做為傳送者。

 ❌ 引發事件時，請勿將 null 傳遞為事件資料參數。

 `EventArgs.Empty`如果您不想要將任何資料傳遞至事件處理方法，則應傳遞。 開發人員預期此參數不是 null。

 ✔️考慮引發終端使用者可以取消的事件。 這僅適用于預先事件。

 使用 <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> 或其子類別做為事件引數，以允許終端使用者取消事件。

### <a name="custom-event-handler-design"></a>自訂事件處理常式設計
 有些情況下 `EventHandler<T>` 無法使用，例如，當架構需要使用舊版 CLR 時，不支援泛型。 在這種情況下，您可能需要設計及開發自訂事件處理常式委派。

 ✔️針對事件處理常式使用 void 的傳回型別。

 事件處理常式可以叫用多個事件處理方法，可能會在多個物件上叫用。 如果允許事件處理方法傳回值，則每個事件調用都會有多個傳回值。

 ✔️請使用做 `object` 為事件處理常式第一個參數的型別，並加以呼叫 `sender` 。

 ✔️請使用 <xref:System.EventArgs?displayProperty=nameWithType> 或其子類別做為事件處理常式之第二個參數的類型，並加以呼叫 `e` 。

 ❌ 在事件處理常式上，不能有兩個以上的參數。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [成員設計方針](member.md)
- [架構設計指導方針](index.md)
