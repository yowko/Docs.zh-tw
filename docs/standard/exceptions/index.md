---
title: "處理和擲回例外狀況 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET Framework], exceptions
- exceptions [.NET Framework], throwing
- exceptions [.NET Framework]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
caps.latest.revision: 16
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c8c5962db342dba6ff22c409d145af5e628eed3d
ms.contentlocale: zh-tw
ms.lasthandoff: 06/08/2017

---
# <a name="handling-and-throwing-exceptions-in-net"></a>在 .NET 中處理和擲回例外狀況

應用程式必須能以一致的方式處理執行期間發生的錯誤。 .NET 提供模型，可以統一的方式通知應用程式的錯誤：.NET 作業會藉由擲回例外狀況指出失敗。

## <a name="exceptions"></a>例外狀況

例外狀況是執行程式所遇到的錯誤狀況或未預期的行為。 若是程式碼或您呼叫的程式碼 (例如共用程式庫) 中有錯誤、無法使用作業系統資源、執行階段遇到非預期的狀況 (例如無法驗證的程式碼) 等等，就可能擲回例外狀況。 您的應用程式可從一些狀況中復原，但有些狀況就無法復原。 雖然您可以從應用程式的大部分例外狀況中復原，但卻無法從執行階段的大部分例外狀況中復原。

在 .NET 中，例外狀況是從 [System.Exception](xref:System.Exception) 類別繼承的物件。 從發生問題的程式碼區域擲回例外狀況。 例外狀況會向上傳遞堆疊，直到應用程式處理或程式終止它。

## <a name="exceptions-vs-traditional-error-handling-methods"></a>例外狀況與傳統錯誤處理方法的比較

傳統上，一種語言的錯誤處理模型不是依賴語言唯一偵測錯誤的方式與尋找處理常式，就是依賴作業系統所提供的錯誤處理機制。 .NET 實作例外狀況處理的方式具有下列優點：

- .NET 程式語言擲回和處理例外狀況的方式都相同。

- 要處理例外狀況不需要任何特定語言的語法，但可讓每一種語言定義自己的語法。

- 例外狀況可跨處理序，甚至是跨電腦界限擲回。

- 可將例外狀況處理程式碼加入應用程式，以增加程式可靠性。

例外狀況優於其他錯誤通知方法，例如傳回碼。 不會發生未通知失敗的情況，因為如果擲回例外狀況而您未加以處理，執行階段就會終止您的應用程式。 也不會因為程式碼無法檢查失敗傳回碼，就繼續在整個系統散佈無效的值。 

## <a name="common-exceptions"></a>常見的例外狀況

下表列出一些常見的例外狀況，並提供可能造成這些例外狀況的原因範例。

| 例外狀況類型 | 基底類型 | 描述 | 範例 |
| -------------- | --------- | ----------- | ------- |
| @System.Exception | @System.Object | 適用於所有例外狀況的基底類別。 | 無 (使用這個例外狀況的衍生類別)。 |
| @System.IndexOutOfRangeException | @System.Exception | 只有當陣列索引不正確時，才由執行階段擲回。 | 在有效的陣列範圍之外編製陣列索引：`arr[arr.Length+1]` |
| @System.NullReferenceException | @System.Exception | 只有當參考 Null 物件時，才由執行階段擲回。 | `object o = null; o.ToString();` |
| @System.InvalidOperationException | @System.Exception | 當處於無效狀態時，由方法擲回。 | 在從基礎集合將 Item 移除之後，呼叫 `Enumerator.GetNext()`。 |
| @System.ArgumentException | @System.Exception | 適用於所有引數例外狀況的基底類別。 | 無 (使用這個例外狀況的衍生類別)。 |
| @System.ArgumentNullException | @System.Exception | 由不允許引數為 Null 的方法擲回。 | `String s = null; "Calculate".IndexOf (s);` |
| @System.ArgumentOutOfRangeException | @System.Exception | 由驗證引數是在指定範圍內的方法擲回。 | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="see-also"></a>另請參閱

* [例外狀況類別和屬性](exception-class-and-properties.md)
* [操作說明：使用 Try/Catch 區塊攔截例外狀況](how-to-use-the-try-catch-block-to-catch-exceptions.md)
* [操作說明：使用 Catch 區塊中的特定例外狀況](how-to-use-specific-exceptions-in-a-catch-block.md)
* [操作說明：明確擲回例外狀況](how-to-explicitly-throw-exceptions.md)
* [操作說明：建立使用者定義的例外狀況](how-to-create-user-defined-exceptions.md)
* [使用使用者篩選的例外狀況處理常式](using-user-filtered-exception-handlers.md)
* [操作說明：使用 Finally 區塊](how-to-use-finally-blocks.md)
* [處理 COM Interop 例外狀況](handling-com-interop-exceptions.md)
* [例外狀況的最佳做法](best-practices-for-exceptions.md)

若要深入了解 .NET 中例外狀況的運作方式，請參閱 [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md)。

