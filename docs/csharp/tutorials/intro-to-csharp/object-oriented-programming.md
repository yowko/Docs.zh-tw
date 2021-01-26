---
title: 物件導向程式設計 (C#)
description: 'C # 提供物件導向程式設計的完整支援，包括抽象、封裝、繼承和多型。'
ms.date: 09/30/2020
ms.openlocfilehash: b778b7c42bbfb1f20bdd2d83b9cb10512ea3f41b
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794842"
---
# <a name="object-oriented-programming-c"></a>Object-Oriented c # 程式設計 (c # ) 

C # 是物件導向的語言。 物件導向程式設計中所使用的四個關鍵技術包括：

- *抽象* 表示隱藏型別取用者不必要的詳細資料。
- 「封裝」指的是將一組相關的屬性、方法和其他成員，視為單一單位或物件。
- 「繼承」則是描述依據現有類別來建立新類別的能力。
- 「多型」指的是您可以有多個交替使用的類別，即使每個類別是以不同的方式來實作相同的屬性或方法。

在上述教學課程中，您看到的 [類別簡介](introduction-to-classes.md) 包括 *抽象* 和 *封裝*。 `BankAccount`類別提供了銀行帳戶概念的抽象概念。 您可以修改其執行，而不會影響使用該類別的任何程式碼 `BankAccount` 。 `BankAccount`和類別都 `Transaction` 提供在程式碼中描述這些概念所需元件的封裝。

在本教學課程中，您將擴充該應用程式，以利用 *繼承* 和 *多* 型的方式來新增新功能。 您也會將功能加入至 `BankAccount` 類別，以利用您在上一個教學課程中學到的 *抽象概念* 和 *封裝* 技術。

## <a name="create-different-types-of-accounts"></a>建立不同類型的帳戶

建立此程式之後，您會收到將功能新增至其中的要求。 它適用于只有一個銀行帳戶類型的情況。 經過一段時間之後，需要變更，並要求相關的帳戶類型：

- 在每個月結束時累算興趣的利息收益帳戶。
- 可以有負數餘額的信用額度，但如果有餘額，每個月會有相關的費用。
- 預先付費的禮物卡帳戶，以單一存款開頭，且僅可供付費。 您可以在每個月開始時重新填一次。

所有這些不同的帳戶都類似于稍 `BankAccount` 早教學課程中所定義的類別。 您可以複製該程式碼、重新命名類別，並進行修改。 這項技術會在短期內運作，但在一段時間內會有更多工作。 任何變更都會複製到所有受影響的類別。

相反地，您可以建立新的銀行帳戶類型，從 `BankAccount` 先前教學課程中建立的類別繼承方法和資料。 這些新的類別可以 `BankAccount` 使用每種類型所需的特定行為來擴充類別：

```csharp
public class InterestEarningAccount : BankAccount
{
}

public class LineOfCreditAccount : BankAccount
{
}

public class GiftCardAccount : BankAccount
{
}
```

每個類別都會 *繼承* 其共用 *基類*（類別）的共用行為 `BankAccount` 。 針對每個 *衍生類別* 中的新功能和不同的功能撰寫實作為。  這些衍生類別已經具有類別中定義的所有行為 `BankAccount` 。

在不同的原始程式檔中建立每個新類別是很好的作法。 在 [Visual Studio](https://visualstudio.com)中，您可以在專案上按一下滑鼠右鍵，然後選取 [ *加入類別* ]，在新的檔案中加入新的類別。 在 [Visual Studio Code](https://code.visualstudio.com)中， *選取 [* 檔案]，然後選取 [ *新增* ] 以建立新的原始檔。 在任一項工具中，將檔案命名以符合類別： *InterestEarningAccount.cs*、 *LineOfCreditAccount.cs* 和 *GiftCardAccount.cs*。

當您建立如先前範例所示的類別時，您會發現沒有任何衍生類別會進行編譯。 函式負責初始化物件。 衍生類別的函式必須初始化衍生類別，並提供如何初始化衍生類別中所包含之基類物件的指示。 適當的初始化通常會發生，而不需要任何額外的程式碼。 類別會使用下列簽章宣告一個公用的函式 `BankAccount` ：

```csharp
public BankAccount(string name, decimal initialBalance)
```

當您自行定義函式時，編譯器不會產生預設的函式。 這表示每個衍生類別都必須明確呼叫這個函式。 您可以宣告可將引數傳遞至基類的函式的函式。  下列程式碼顯示的函式 `InterestEarningAccount` ：

:::code language="csharp" source="./snippets/object-oriented-programming/InterestEarningAccount.cs" ID="DerivedConstructor":::

這個新的函式的參數符合基類函式的參數類型和名稱。 您可以使用 `: base()` 語法來表示呼叫基類的函式。 某些類別會定義多個函式，而此語法可讓您挑選您要呼叫的基類函式。 更新這些函式之後，您可以為每個衍生類別開發程式碼。 新類別的需求可陳述如下：

- 利息收益帳戶：
  - 將取得每月的點數（以月為結束餘額）。
- 信用額度：
  - 可以有負數餘額，但絕對值不能大於點數限制。
  - 每個月都會產生利息費，而月底餘額不是0。
  - 會在每次提款時產生費用，並超過點數限制。
- 禮品卡帳戶：
  - 可以在每個月的最後一天，以指定的數量一次重新填入。

您可以看到這些帳戶類型的三個都有一個動作會在每個月的結尾處進行。 不過，每個帳戶類型都會執行不同的工作。 您可以使用 *多* 型來執行此程式碼。 `virtual`在類別中建立單一方法 `BankAccount` ：

:::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="DeclareMonthEndTransactions":::

上述程式碼示範如何使用 `virtual` 關鍵字來宣告基類中的方法，衍生類別可能會提供不同的執行方式。 `virtual`方法是一種方法，其中任何衍生的類別都可以選擇重新進行。 衍生的類別會使用 `override` 關鍵字來定義新的實作為。 通常您會將此稱為「覆寫基類實」。 `virtual`關鍵字會指定衍生類別可能會覆寫行為。 您也可以宣告 `abstract` 衍生類別必須覆寫行為的方法。 基類不提供方法的執行 `abstract` 。 接下來，您必須為您所建立的兩個新類別定義執行。 從開始 `InterestEarningAccount` ：

:::code language="csharp" source="./snippets/object-oriented-programming/InterestEarningAccount.cs" ID="ApplyMonthendInterest":::

將下列程式碼加入至 `LineOfCreditAccount` 。 此程式碼會否定餘額，以計算從帳戶中撤銷的正面利息費用：

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="ApplyMonthendInterest":::

此 `GiftCardAccount` 類別需要兩個變更，才能執行其 month end 功能。 首先，修改函式以包含每個月新增的選擇性數量：

:::code language="csharp" source="./snippets/object-oriented-programming/GiftCardAccount.cs" ID="GiftCardAccountConstruction":::

此函式會提供值的預設值 `monthlyDeposit` ，因此呼叫者可以省略，而 `0` 不是每月的存款。 接下來，覆寫 `PerformMonthEndTransactions` 方法以新增每月存款（如果它在函式中設定為非零的值）：

:::code language="csharp" source="./snippets/object-oriented-programming/GiftCardAccount.cs" ID="AddMonthlyDeposit":::

覆寫會在此函式中套用每月存款集。 將下列程式碼加入至 `Main` 方法，以測試 `GiftCardAccount` 和的這些變更 `InterestEarningAccount` ：

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="FirstTests":::

確認結果。 現在，為下列各項新增一組類似的測試程式碼 `LineOfCreditAccount` ：

```
    var lineOfCredit = new LineOfCreditAccount("line of credit", 0);
    // How much is too much to borrow?
    lineOfCredit.MakeWithdrawal(1000m, DateTime.Now, "Take out monthly advance");
    lineOfCredit.MakeDeposit(50m, DateTime.Now, "Pay back small amount");
    lineOfCredit.MakeWithdrawal(5000m, DateTime.Now, "Emergency funds for repairs");
    lineOfCredit.MakeDeposit(150m, DateTime.Now, "Partial restoration on repairs");
    lineOfCredit.PerformMonthEndTransactions();
    Console.WriteLine(lineOfCredit.GetAccountHistory());
 ```

當您新增上述程式碼並執行程式時，將會看到類似下列的錯誤：

```console
Unhandled exception. System.ArgumentOutOfRangeException: Amount of deposit must be positive (Parameter 'amount')
   at OOProgramming.BankAccount.MakeDeposit(Decimal amount, DateTime date, String note) in BankAccount.cs:line 42
   at OOProgramming.BankAccount..ctor(String name, Decimal initialBalance) in BankAccount.cs:line 31
   at OOProgramming.LineOfCreditAccount..ctor(String name, Decimal initialBalance) in LineOfCreditAccount.cs:line 9
   at OOProgramming.Program.Main(String[] args) in Program.cs:line 29
```

> [!NOTE]
> 實際的輸出會包含專案之資料夾的完整路徑。 為了簡潔起見，已省略資料夾名稱。 此外，根據您的程式碼格式，行號可能稍有不同。

此程式碼會失敗，因為 `BankAccount` 假設初始餘額必須大於0。 在類別中內建的另一個假設 `BankAccount` 是，餘額不能為負數。 相反地，overdraws 帳戶的任何提款都會遭到拒絕。 這兩個假設都需要變更。 信用額度帳戶的行從0開始，而且通常會有負餘額。 此外，如果客戶借用太多錢，則會產生費用。 交易會被接受，而只是成本更高。 第一個規則可以藉由將選擇性引數新增至 `BankAccount` 指定最小餘額的函式來執行。 預設為 `0`。 第二個規則需要能讓衍生類別修改預設演算法的機制。 就某種意義而言，基類「會詢問」衍生型別透支時應該發生的情況。 預設行為是藉由擲回例外狀況來拒絕交易。

首先，讓我們加入第二個包含選擇性參數的函式 `minimumBalance` 。 這個新的函式會執行現有的函式所執行的所有動作。 此外，它也會設定最小餘額屬性。 您可以複製現有的函式主體。 但這表示未來有兩個要變更的位置。 相反地，您可以使用函式 *連結* 來呼叫另一個函式。 下列程式碼顯示兩個函式和新的額外欄位：

 :::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="ConstructorModifications":::

上述程式碼顯示兩個新的技巧。 首先， `minimumBalance` 欄位會標示為 `readonly` 。 這表示在建立物件之後，就無法變更此值。 一旦 `BankAccount` 建立之後，就 `minimumBalance` 無法變更。 其次，採用兩個參數的函式會使用 `: this(name, initialBalance, 0) { }` 做為其實作為。 `: this()`運算式會呼叫另一個具有三個參數的函式。 雖然用戶端程式代碼可以選擇許多個函式的其中一個，但是這項技術可讓您在初始化物件時進行單一初始化。

`MakeDeposit`只有在初始餘額大於時，才會呼叫此實作為 `0` 。 這會保留存款必須是正數的規則，但會讓點數帳戶以餘額開啟 `0` 。

既然 `BankAccount` 類別具有最小餘額的唯讀欄位，最後的變更是 `0` `minimumBalance` 在方法中將硬式程式碼變更為 `MakeWithdrawal` ：

```csharp
if (Balance - amount < minimumBalance)
```

擴充類別之後 `BankAccount` ，您可以修改函式 `LineOfCreditAccount` 來呼叫新的基底函式，如下列程式碼所示：

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="ConstructLineOfCredit":::

請注意，此函式會 `LineOfCreditAccount` 變更參數的正負號， `creditLimit` 使其符合參數的意義 `minimumBalance` 。

## <a name="different-overdraft-rules"></a>不同的透支規則

最後一個要新增的功能，可讓您 `LineOfCreditAccount` 收取超過信用額度的費用，而不會拒絕交易。

其中一個技術是定義虛擬函式，您可以在其中執行所需的行為。 類別會將 `BankAccount` `MakeWithdrawal` 方法重構為兩個方法。 當提款將餘額降到低於最小值時，新的方法會執行指定的動作。 現有的 `MakeWithdrawal` 方法具有下列程式碼：

```csharp
public void MakeWithdrawal(decimal amount, DateTime date, string note)
{
    if (amount <= 0)
    {
        throw new ArgumentOutOfRangeException(nameof(amount), "Amount of withdrawal must be positive");
    }
    if (Balance - amount < minimumBalance)
    {
        throw new InvalidOperationException("Not sufficient funds for this withdrawal");
    }
    var withdrawal = new Transaction(-amount, date, note);
    allTransactions.Add(withdrawal);
}
```

使用下列程式碼將其取代：

:::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="RefactoredMakeWithdrawal":::

加入的方法是 `protected` ，這表示它只能從衍生類別呼叫。 該宣告可防止其他用戶端呼叫該方法。 此外 `virtual` ，衍生類別也可以變更行為。 傳回型別為 `Transaction?` 。 `?`批註表示方法可能會傳回 `null` 。 在中新增下列實行 `LineOfCreditAccount` ，以在超過提款限制時收取費用：

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="AddOverdraftFee":::

Overdrawn 帳戶時，覆寫會傳回費用交易。 如果提款未超過限制，則方法會傳回 `null` 交易。 這表示不會有任何費用。 將下列程式碼新增至 `Main` 類別中的方法，以測試這些變更 `Program` ：

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="TestLineOfCredit":::

執行程式，並檢查結果。

## <a name="summary"></a>摘要

如果您遇到困難，您可以 [在 GitHub 存放庫中](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/object-oriented-programming)看到此教學課程的來源。

本教學課程示範 Object-Oriented 程式設計中使用的許多技術：

- 當您在每個類別中保留許多詳細資料時，就會使用 *抽象概念* `private` 。
- 當您針對每個不同的帳戶類型定義了類別時，就會使用 *封裝* 。 這些類別描述了該帳戶類型的行為。
- 當您利用已在類別中建立的實存程式碼時，就會使用 *繼承* `BankAccount` 。
- 當您建立 `virtual` 衍生類別可覆寫的方法，以建立該帳戶類型的特定行為時，您會使用多型。

恭喜，您已完成所有的 c # 教學課程簡介。 若要深入瞭解，請嘗試更多 [教學](../index.md)課程。
