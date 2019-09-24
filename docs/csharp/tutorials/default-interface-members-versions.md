---
title: 在 C# 中使用預設介面成員安全地更新介面
description: 本進階教學課程探討如何安全地將新功能新增至現有的介面定義，而不會中斷實作該介面的所有類別和結構。
ms.date: 05/06/2019
ms.custom: mvc
ms.openlocfilehash: 271c737e17cc2b93424108e7e1d434fd1c7198be
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216573"
---
# <a name="tutorial-update-interfaces-with-default-interface-members-in-c-80"></a>教學課程：在 C# 8.0 中使用預設介面成員更新介面

從 C# 8.0 開始，您可以在宣告介面成員時，於 .NET Core 3.0 上定義實作。 最常見的情節是安全地將成員新增至已發行並由無數個用戶端所使用的介面。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 新增附實作的方法來安全地擴充介面。
> * 建立參數化實作以提高彈性。
> * 讓實作者提供覆寫形式的更特定實作。

## <a name="prerequisites"></a>必要條件

您必須設定電腦以執行 .NET Core，包括C# 8.0 編譯器。 從C# [Visual Studio 2019 16.3 版](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或[.net Core 3.0 SDK](https://dotnet.microsoft.com/download)開始，可以使用8.0 編譯器。

## <a name="scenario-overview"></a>情節概觀

本教學課程從客戶關係程式庫第 1 版開始。 您可以在 [GitHub 的範例存放庫](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship)中取得入門應用程式。 建置此程式庫的公司想要讓客戶透過現有應用程式來採用其程式庫。 他們提供可讓其程式庫使用者實作的基本介面定義。 以下是客戶的介面定義：

[!code-csharp[InitialCustomerInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

他們定義代表訂單的第二個介面：

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

針對這些介面，小組可以建置適用於其使用者的程式庫，來為其客戶打造更好的體驗。 其目標是加深與現有客戶的關係，並改善與新客戶的關係。

現在，您可以將程式庫升級到下一版。 其中一項所要求功能是讓擁有許多訂單的客戶享有忠誠度折扣。 此新的忠誠度折扣會在每次客戶下單時套用。 此特定折扣屬於每個個別客戶。 每個的`ICustomer`執行都可以為忠誠度折扣設定不同的規則。 

新增此功能的最自然方式，就是使用方法來增強 `ICustomer` 介面以套用任何忠誠度折扣。 此設計建議在有經驗的開發人員之間引起顧慮：「介面一旦發行，就不可改變！ 這是中斷性變更！」 C# 8.0 新增「預設介面實作」來升級介面。 程式庫作者可以將新成員新增至介面，並為這些成員提供預設實作。

預設介面實作可讓開發人員升級介面，同時仍可讓任何實作者覆寫該實作。 程式庫使用者可以接受預設實作作為非中斷性變更。 如果他們的商務規則不同，則可以進行覆寫。

## <a name="upgrade-with-default-interface-members"></a>使用預設介面成員進行升級

小組同意最有可能的預設實作，就是客戶的忠誠度折扣。

升級應該提供設定兩個屬性的功能：必須符合折扣資格的訂單數目，以及折扣百分比。 因此非常適合使用預設介面成員。 您可以將方法加入至`ICustomer`介面，並提供最可能的執行。 所有現有及任何新的實作都可使用預設實作，或提供自己的實作。

首先，將新方法新增至實作：

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

程式庫作者撰寫第一個測試來檢查實作：

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

請注意下列測試部分：

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

`SampleCustomer` 必須轉換成 `ICustomer`。 `SampleCustomer` 類別不需要提供 `ComputeLoyaltyDiscount` 的實作；這會由 `ICustomer` 介面提供。 不過，`SampleCustomer` 類別不會從其介面繼承成員。 該規則並未變更。 為了呼叫在介面中宣告和實作的任何方法，變數必須是介面類型，在本例中為 `ICustomer`。

## <a name="provide-parameterization"></a>提供參數化

這是一個不錯的起點。 但預設實作太過侷限。 此系統的許多取用者可能選擇不同購買數目閾值、不同成員資格長度，或不同分比折扣。 您可以藉由提供設定這些參數的方法，來為更多客戶提供更好的升級體驗。 我們將新增靜態方法，設定這三個參數來控制預設實作：

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

該小型程式碼片段中顯示許多新的語言功能。 介面現在可以包含靜態成員，包括欄位和方法。 也會啟用不同的存取修飾詞。 其他欄位是私用的，而新方法是公用的。 介面成員上允許任何修飾詞。

使用一般公式來計算忠誠度折扣 (但參數不同) 的應用程式不需要提供自訂實作；這些應用程式可透過靜態方法來設定引數。 例如，下列程式碼會設定「客戶感謝」，獎勵其成員資格超過一個月的任何客戶：

[!code-csharp[SetLoyaltyThresholds](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>擴充預設實作

如果使用者想要類似預設實作的其他實作，或是想要提供一組不相關的規則，您到目前為止所新增程式碼為這些情節提供便利的實作。 針對最後一項功能，我們將稍微重構程式碼，讓使用者可以在預設實作上建置。 

假設有間新創公司想要吸引新客戶。 該公司提供 50% 折扣給首次下單的新客戶。 至於現有的客戶則享有標準折扣。 程式庫作者必須將預設實作移入 `protected static` 方法，才能讓實作此介面的任何類別在其實作中重複使用程式碼。 介面成員的預設實作也會呼叫此共用方法：

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

在實作此介面的類別實作中，覆寫可以呼叫靜態 Helper 方法，並擴充該邏輯以提供「新客戶」折扣：

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

您可以在 [GitHub 上的範例存放庫](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship) \(英文\) 中查看已完成的完整程式碼。 您可以在 [GitHub 的範例存放庫](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship)中取得入門應用程式。

這些新功能表示介面可在這些新成員有合理的預設實作時安全地更新。 請謹慎設計介面來表達可由多個類別實作的單一功能概念。 這讓您可以在發現該相同功能概念有新需求時，更輕鬆地升級這些介面定義。
