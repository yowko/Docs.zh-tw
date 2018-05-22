---
title: 逐步解說：使用 C# 保存物件
ms.date: 04/26/2018
ms.openlocfilehash: 6c9719dc3aaf997ea144515a553f787450e54041
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="walkthrough-persisting-an-object-using-c"></a>逐步解說：使用 C# 保存物件 #

您可以使用序列化來保存執行個體之間的物件資料，藉此儲存值，並在下次將物件具現化時加以擷取。

在本逐步解說中，您將建立基本的 `Loan` 物件，並將其資料保存至檔案。 當您重新建立物件時，即會從檔案擷取資料。

> [!IMPORTANT]
> 如果檔案不存在，此範例就會建立新的檔案。 如果應用程式需要建立檔案，該應用程式就必須具有資料夾的 `Create` 權限。 您可以使用存取控制清單來設定權限。 如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。 若有可能，更為安全的做法是在部署期間建立檔案，並只授與單一檔案的 `Read` 權限 (而不是資料夾的 Create 權限)。 此外，將資料寫入使用者資料夾，而不是根資料夾或 Program Files 資料夾，也更加安全。

> [!IMPORTANT]
> 這個範例會使用二進位格式檔案來儲存資料。 這些格式不適用於敏感性資料，例如密碼或信用卡資訊。

## <a name="prerequisites"></a>必要條件

* 若要建置並執行，請安裝 [.NET Core SDK](https://www.microsoft.com/net/core)。

* 如果您還沒有這麼做，請安裝您慣用的程式碼編輯器。

> [!TIP]
> 需要安裝程式碼編輯器嗎？ 試用 [Visual Studio](https://visualstudio.com/downloads)！

您可以在 [.NET 範例 GitHub 存放庫](https://github.com/dotnet/samples/tree/master/csharp/serialization) (英文) 線上檢查範例程式程。

## <a name="creating-the-loan-object"></a>建立 Loan 物件

第一個步驟是建立 `Loan` 類別，以及使用該類別的主控台應用程式：

1. 建立新的應用程式。 輸入 `dotnet new console -o serialization`，在名為 `serialization` 的子目錄中建立新的主控台應用程式。
1. 在編輯器中開啟應用程式，並新增名為 `Loan.cs` 的新類別。
1. 將下列程式碼新增至 `Loan` 類別：

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#1)]

您還必須建立使用 `Loan` 類別的應用程式。

## <a name="serialize-the-loan-object"></a>序列化 Loan 物件

1. 開啟 `Program.cs`。 加入下列程式碼：

[!code-csharp[Create a loan object](../../../../../samples/csharp/serialization/Program.cs#1)]

為 `PropertyChanged` 事件新增事件處理常式，並新增幾行來修改 `Loan` 物件和顯示所做的變更。 您可以在下列程式碼中看到新增的項目：

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/csharp/serialization/Program.cs#2)]

此時，您可以執行該程式碼，並查看目前的輸出：

```console
New customer value: Henry Clay
7.5
7.1
```

執行此應用程式一律會重複寫入相同的值。 每次您執行程式時，就會建立一個新的 Loan 物件。 在現實生活中，利率會定期變更，但不一定每次都需要執行應用程式。 序列化程式碼表示您要保存應用程式執行個體之間的最近利率。 在下一個步驟中，您會將序列化新增至 Loan 類別以進行上述作業。

## <a name="using-serialization-to-persist-the-object"></a>使用序列化來保存物件

為了保存 Loan 類別的值，您必須先使用 `Serializable` 屬性來標示類別。 在 Loan 類別定義之上新增下列程式碼：

[!code-csharp[Loan class definition](../../../../../samples/csharp/serialization/Loan.cs#2)]

編譯器接收到 <xref:System.SerializableAttribute> 時，即會了解類別中的所有項目皆可保存至檔案。 因為 `PropertyChanged` 事件不代表應儲存之物件圖形的一部分，所以它不應該被序列化。 這樣做會序列化附加至該事件的所有物件。 您可以將 <xref:System.NonSerializedAttribute> 新增至 `PropertyChanged` 事件處理常式的欄位宣告。

[!code-csharp[Disable serialization for the event handler](../../../../../samples/csharp/serialization/Loan.cs#3)]

從 C# 7.3 開始，您可以使用 `field` 目標值，將屬性 (attribute) 附加至使用自動實作屬性 (property) 的支援欄位。 下列程式碼會新增 `TimeLastLoaded` 屬性，並將它標示為不可序列化：

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/csharp/serialization/Loan.cs#4)]

下一個步驟是將序列化程式碼新增至 LoanApp 應用程式。 若要序列化類別並將它寫入檔案，您必須使用 <xref:System.IO> 和 <xref:System.Runtime.Serialization.Formatters.Binary> 命名空間。 若要避免輸入完整的名稱，您可以新增必要命名空間的參考，如下列程式碼所示：

[!code-csharp[Adding namespaces for serialization](../../../../../samples/csharp/serialization/Program.cs#3)]

下一個步驟是新增程式碼，以在建立物件時，從檔案還原序列化物件。 將常數新增至已序列化資料檔案名稱的類別，如下列程式碼所示：

[!code-csharp[Define the name of the saved file](../../../../../samples/csharp/serialization/Program.cs#4)]

接下來，在建立 `TestLoan` 物件這一行之後新增下列程式碼：

[!code-csharp[Read from a file if it exists](../../../../../samples/csharp/serialization/Program.cs#5)]

您必須先檢查檔案是否存在。 如果存在的話，請建立 <xref:System.IO.Stream> 類別以讀取二進位檔案，並建立 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 類別來轉譯該檔案。 您也需要將資料流類型轉換成 Loan 物件類型。

接下來，您必須新增程式碼，將類別序列化為檔案。 在 `Main` 方法的現有程式碼之後，新增下列程式碼：

[!code-csharp[Save the existing Loan object](../../../../../samples/csharp/serialization/Program.cs#6)]

您現在可以再次建置並執行應用程式。 第一次執行時，請注意利率會從 7.5 開始，然後變更為 7.1。 關閉應用程式，然後再重新執行。 現在，應用程式會列印訊息，表示它已讀取儲存的檔案，而利率即使在變更它的程式碼之前也是 7.1。

## <a name="see-also"></a>另請參閱

 [序列化 (C# )](index.md)  
 [C# 程式設計指南](../..//index.md)  
