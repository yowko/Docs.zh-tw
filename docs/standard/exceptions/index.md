---
title: 在 .NET 中處理和擲回例外狀況
ms.date: 06/19/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET], exceptions
- exceptions [.NET], throwing
- exceptions [.NET]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 648a4d9e2f9be2cd8a5912ebfe272331a70ee76e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707878"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>在 .NET 中處理和擲回例外狀況

應用程式必須能以一致的方式處理執行期間發生的錯誤。 .NET 提供模型，可以統一的方式通知應用程式的錯誤：.NET 作業會藉由擲回例外狀況指出失敗。

## <a name="exceptions"></a>例外狀況

例外狀況是執行程式所遇到的錯誤狀況或未預期的行為。 在發生程式碼或您呼叫的程式碼 (例如共用程式庫) 中有錯誤、無法使用作業系統資源、執行階段遇到非預期的狀況 (例如無法驗證的程式碼) 等情況時，就可能會擲回例外狀況。 您的應用程式可從一些狀況中復原，但有些狀況就無法復原。 雖然您可以從大部分的應用程式例外狀況中復原，但是無法從大部分的執行階段例外狀況中復原。

在 .NET 中，例外狀況是繼承自 <xref:System.Exception?displayProperty=nameWithType> 類別的物件。 從發生問題的程式碼區域擲回例外狀況。 例外狀況會向上傳遞堆疊，直到應用程式處理或程式終止它。

## <a name="exceptions-vs-traditional-error-handling-methods"></a>例外狀況與傳統錯誤處理方法的比較

傳統上，一種語言的錯誤處理模型不是依賴語言唯一偵測錯誤的方式與尋找處理常式，就是依賴作業系統所提供的錯誤處理機制。 .NET 實作例外狀況處理的方式具有下列優點：

- .NET 程式語言擲回和處理例外狀況的方式都相同。

- 不需要任何特定語言語法以處理例外狀況，但可讓每一種語言定義屬於自己的語法。

- 例外狀況可跨處理序，甚至是跨電腦界限擲回。

- 可將例外狀況處理程式碼加入應用程式，以增加程式可靠性。

例外狀況優於其他錯誤通知方法，例如傳回碼。 不會發生未注意到失敗的情況，因為如果系統擲出例外狀況且您未加以處理，執行階段就會終止您的應用程式。 無效值不會因為程式碼無法檢查失敗傳回碼，而持續在系統中散佈。

## <a name="common-exceptions"></a>常見的例外狀況

下表列出一些常見的例外狀況，並提供可能造成這些例外狀況的原因範例。

| 例外狀況類型 | 說明 | 範例 |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | 適用於所有例外狀況的基底類別。 | 無 (使用這個例外狀況的衍生類別)。 |
| <xref:System.IndexOutOfRangeException> | 只有當陣列索引不正確時，才由執行階段擲回。 | 在陣列有效範圍之外對它進行索引： <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | 只有當參考 Null 物件時，才由執行階段擲回。 | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | 當處於無效狀態時，由方法擲回。 | 在從基礎集合將項目移除之後，呼叫 `Enumerator.MoveNext()`。 |
| <xref:System.ArgumentException> | 適用於所有引數例外狀況的基底類別。 | 無 (使用這個例外狀況的衍生類別)。 |
| <xref:System.ArgumentNullException> | 由不允許引數為 Null 的方法擲回。 | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | 由驗證引數是在指定範圍內的方法擲回。 | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>另請參閱

- [例外狀況類別和屬性](exception-class-and-properties.md)
- [如何：使用 Try/Catch 區塊攔截例外狀況](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [如何：使用 Catch 區塊中的特定例外狀況](how-to-use-specific-exceptions-in-a-catch-block.md)
- [如何：明確擲回例外狀況](how-to-explicitly-throw-exceptions.md)
- [如何：建立使用者定義的例外狀況](how-to-create-user-defined-exceptions.md)
- [使用使用者篩選的例外狀況處理常式](using-user-filtered-exception-handlers.md)
- [如何：使用 Finally 區塊](how-to-use-finally-blocks.md)
- [處理 COM Interop 例外狀況](handling-com-interop-exceptions.md)
- [例外狀況的最佳做法](best-practices-for-exceptions.md)
- [每個開發人員針對執行階段中例外狀況所需知道的概念](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md) \(英文\)。
