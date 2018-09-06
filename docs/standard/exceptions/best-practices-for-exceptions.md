---
title: 例外狀況的最佳作法
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee61d01acbf9c409eaedc04ff3e949908e1d595e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867851"
---
# <a name="best-practices-for-exceptions"></a>例外狀況的最佳做法

設計良好的應用程式可處理例外狀況和錯誤，防止應用程式損毀。 本節說明處理和建立例外狀況的最佳做法。

## <a name="use-trycatchfinally-blocks"></a>使用 try/catch/finally 區塊

使用 `try`/`catch`/`finally` 區塊括住程式碼可能會產生例外狀況。 

在 `catch` 區塊中，一律將例外狀況從最特殊的排列到最不特殊的。

不論您是否可以復原，使用 `finally` 區塊都可清除資源。

## <a name="handle-common-conditions-without-throwing-exceptions"></a>處理常見的狀況，而不擲回例外狀況

針對可能發生但可能會觸發例外狀況的狀況，請考慮以避免例外狀況的方式來處理這些狀況。 例如，如果您嘗試關閉已關閉的連線，您會得到 `InvalidOperationException`。 您可以在嘗試關閉之前，使用 `if` 陳述式來檢查連線狀態，以避免此例外狀況。

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

如果您沒有檢查連線狀態就關閉，您可能會攔截到 `InvalidOperationException` 例外狀況。

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

選擇的方法取決於您預期事件會發生的頻率。

- 如果事件不常發生，也就是說事件真的是例外並且表示錯誤 (例如未預期的檔案結尾)，則使用例外狀況處理。 當您使用例外狀況處理時，在正常情況下會執行較少的程式碼。

- 如果事件定期發生而且可視為正常執行的一部分，請檢查程式碼中是否有錯誤狀況。 當您檢查是否有常見的錯誤狀況時，因為避免例外狀況，所以會執行較少的程式碼。

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>設計類別以避免例外狀況

類別可提供方法或屬性，讓您避免進行會觸發例外狀況的呼叫。 例如，<xref:System.IO.FileStream> 類別會提供方法，協助判斷是否已經抵達檔案結尾。 這些方法或屬性可用來避免萬一您讀取超過檔案結尾時，所擲回的例外狀況。 下列範例示範如何讀取至檔案結尾，而不會觸發例外狀況。

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

另一個避免例外狀況的方法是針對很常見的錯誤案例傳回 null，而不擲回例外狀況。 相當普遍的錯誤案例可視為一般控制流程。 針對這些案例傳回 null，就能盡量降低對應用程式效能的影響。

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>擲回例外狀況來代替傳回錯誤碼

例外狀況可確保不會發生未通知失敗的情況，因為呼叫程式碼並不會檢查傳回碼。 

## <a name="use-the-predefined-net-exception-types"></a>使用預先定義的 .NET 例外狀況類型

只有在預先定義的類型不適用時，才引進新的例外狀況類別。 例如: 

- 如果屬性集或方法呼叫對於物件的目前狀態而言並不適當，就會擲回 <xref:System.InvalidOperationException> 例外狀況。

- 在傳遞的參數無效時擲回 <xref:System.ArgumentException> 例外狀況，或擲回預先定義之類別中，從 <xref:System.ArgumentException> 衍生而來的類別。

## <a name="end-exception-class-names-with-the-word-exception"></a>使用字組 `Exception` 作為例外狀況類別名稱的結尾

如需自訂例外狀況，請適當地加以命名，並從 <xref:System.Exception>加以衍生。 例如: 

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a>在自訂例外狀況類別中包含三個建構函式

當您建立自己的例外狀況類別時，請使用至少三個種常見的建構函式：預設建構函式、採用字串訊息的建構函式，以及採用字串訊息和內部例外狀況的建構函式。

* <xref:System.Exception.%23ctor>，會使用預設值。
  
* <xref:System.Exception.%23ctor%28System.String%29>，它會接受字串訊息。  
  
* <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>，它會接受字串訊息和內部例外狀況。  
  
如需範例，請參閱[如何：建立使用者定義的例外狀況](how-to-create-user-defined-exceptions.md)。

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>確保從遠端執行程式碼時可以使用例外狀況資料

當您建立使用者定義的例外狀況時，請確保例外狀況的中繼資料可供遠端執行的程式碼使用。 

例如，在支援應用程式定義域的 .NET 實作上，例外狀況可能會跨應用程式定義域發生。 假定應用程式定義域 A 建立應用程式定義域 B，它會執行擲回例外狀況的程式碼。 為使應用程式定義域 A 能夠正確地攔截及處理例外狀況，其必須能夠尋找含有應用程式定義域 B 所擲回之例外狀況的組件。若應用程式定義域 B 擲回例外狀況，但此例外狀況包含在位於其應用程式基底之下的組件，而不是位於在應用程式定義域 A 的應用程式基底之下的組件，應用程式定義域 A 將無法尋找例外狀況，而且 Common Language Runtime 將會擲回 <xref:System.IO.FileNotFoundException> 例外狀況。 若要避免這個情形，您可以透過兩種方式部署含有例外狀況資訊的組件：

- 將組件放入這兩個應用程式定義域共用的通用應用程式基底。

    \-或-

- 如果定義域不共用通用應用程式基底，則以強式名稱簽署含有例外狀況資訊的組件，並將組件部署到全域組件快取中。

## <a name="use-grammatically-correct-error-messages"></a>使用文法正確的錯誤訊息

撰寫清楚的句子並包含結尾標點符號。 在每個指派給 <xref:System.Exception.Message?displayProperty=nameWithType> 屬性的字串中之句子，都應以句點結束。 例如，「記錄資料表已溢位」。 就是正確的訊息字串。

## <a name="include-a-localized-string-message-in-every-exception"></a>在每個例外狀況中，納入當地語系化的字串訊息

使用者所看到的錯誤訊息，衍生自擲回的例外狀況之 <xref:System.Exception.Message?displayProperty=nameWithType> 屬性，而並非來自例外狀況類別的名稱。 一般來說，您要將值指派到 <xref:System.Exception.Message?displayProperty=nameWithType> 屬性，方法是將訊息字串傳遞到[例外狀況建構函式](xref:System.Exception.%23ctor%2A)的 `message` 引數。 

若是當地語系化的應用程式，則應對每個應用程式可能會擲回的例外狀況，該提供當地語系化的訊息字串。 您可使用資源檔，提供當地語系化的錯誤訊息。 如需當地語系化應用程式與擷取當地語系化字串的詳細資訊，請參閱[傳統型應用程式中的資源](../../framework/resources/index.md)與 <xref:System.Resources.ResourceManager?displayProperty=nameWithType>。

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>在自訂例外狀況中，視需要提供額外的屬性

只有在其他資訊對某個程式設計案例實用時，才為例外狀況提供其他屬性 (以及自訂訊息字串)。 例如，<xref:System.IO.FileNotFoundException> 提供 <xref:System.IO.FileNotFoundException.FileName> 屬性。

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>放置 throw 陳述式讓堆疊追蹤更有用

堆疊追蹤會從擲回例外狀況所在的陳述式開始，並在攔截例外狀況的 `catch` 陳述式結束。

## <a name="use-exception-builder-methods"></a>使用例外狀況產生器方法

類別在它的實作中從不同的地方擲回相同的例外狀況是很常見的。 若要避免過多的程式碼，請使用 Helper 方法，以建立例外狀況並將它傳回。 例如: 

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
在某些情況下，使用例外狀況的建構函式來建置例外狀況會更適當。 範例為全域例外狀況類別 <xref:System.ArgumentException>。

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>在擲回例外狀況時清除中繼結果

呼叫端應該能夠假設，從方法擲回例外狀況時不會產生副作用。 例如，如果您有用來轉帳的程式碼，會從某個帳戶提款再存入另一個帳戶，而且在執行存款時擲回例外狀況，則您不想要讓提款仍有效。

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

處理這種情況的一個方式是攔截存款交易所擲回的任何例外狀況，並復原提款。

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

此範例說明如何使用 `throw` 重新擲回原始的例外狀況，以方便呼叫端無須檢視 <xref:System.Exception.InnerException>屬性，就能輕鬆查看問題的實際原因。 另一種做法是擲回新的例外狀況，並包含原始例外狀況作為內部例外狀況：

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a>另請參閱

- [例外狀況](index.md)
