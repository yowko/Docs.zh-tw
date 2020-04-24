---
title: 擴充 My 命名空間
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 2a7b0b84061fccd9a333a68e4a19477bd19ca4ff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330306"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>擴充中`My`的命名空間 Visual Basic

Visual Basic `My`中的命名空間會公開屬性和方法，讓您可以輕鬆地利用 .NET Framework 的功能。 `My`命名空間簡化了常見的程式設計問題，通常會減少一行程式碼的困難工作。 此外，命名`My`空間是完全可擴充的，因此您可以自訂的`My`行為，並將新的服務新增至其階層，以適應特定的應用程式需求。 本主題討論如何自訂`My`命名空間的現有成員，以及如何將您自己的自訂類別加入`My`命名空間。

## <a name="customizing-existing-my-namespace-members"></a>自訂`My`現有命名空間成員

Visual Basic `My`中的命名空間會公開有關您的應用程式、電腦和其他的常用資訊。 如需`My`命名空間中物件的完整清單，請參閱[我的參考](../../language-reference/keywords/my-reference.md)。 您可能必須自訂`My`命名空間的現有成員，使其更符合應用程式的需求。 `My`命名空間中不是唯讀之物件的任何屬性，都可以設定為自訂值。

例如，假設您經常使用`My.User`物件來存取執行應用程式之使用者的目前安全性內容。 不過，您的公司會使用自訂的使用者物件，為公司內的使用者公開其他資訊和功能。 在此案例中，您可以使用您自己的自`My.User.CurrentPrincipal`定義主體物件的實例來取代屬性的預設值，如下列範例所示：

[!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]

在`My.User`物件`CurrentPrincipal`上設定屬性會變更用來執行應用程式的身分識別。 接著`My.User` ，物件會傳回新指定使用者的相關資訊。
  
## <a name="adding-members-to-my-objects"></a>將成員加入`My`至物件

從`My.Application`和`My.Computer`傳回的類型會定義為`Partial`類別。 因此，您可以藉由`My.Application`建立`My.Computer`名為`MyApplication`或`MyComputer`的`Partial`類別來擴充和物件。 類別不可以是`Private`類別。 如果您指定類別做為`My`命名空間的一部分，您可以加入將包含在`My.Application`或`My.Computer`物件中的屬性和方法。

下列範例會將名`DnsServerIPAddresses`為的`My.Computer`屬性加入至物件：

[!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]

## <a name="adding-custom-objects-to-the-my-namespace"></a>將自訂物件新增`My`至命名空間

雖然`My`命名空間提供許多常見程式設計工作的解決方案，但您可能會遇到`My`命名空間無法解決的工作。 例如，您的應用程式可能會存取使用者資料的自訂目錄服務，或者您的應用程式可能會使用預設不會隨 Visual Basic 安裝的元件。 您可以擴充`My`命名空間，以將自訂解決方案納入您環境特有的一般工作。 `My`命名空間可以輕鬆地擴充，以加入新的成員，以滿足不斷成長的應用程式需求。 此外，您也可以將`My`命名空間延伸模組部署到其他開發人員做為 Visual Basic 範本。
  
### <a name="adding-members-to-the-my-namespace"></a>將成員新增至`My`命名空間

因為`My`是命名空間，就像任何其他命名空間一樣，只要加入模組並指定`Namespace`的`My`，您就可以將最上層的屬性加入其中。 使用`HideModuleName`屬性標注模組，如下列範例所示。 `HideModuleName`屬性可確保 IntelliSense 在顯示`My`命名空間的成員時，不會顯示模組名稱。

[!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]

若要將成員新增`My`至命名空間，請視需要將屬性新增至模組。 針對加入至`My`命名空間的每個屬性，加入類型`ThreadSafeObjectProvider(Of T)`為的私用欄位，其中類型是自訂屬性所傳回的類型。 這個欄位是用來建立由屬性呼叫`GetInstance`方法所傳回的安全線程物件實例。 因此，每個存取擴充屬性的執行緒都會收到自己的傳回型別實例。 下列範例會將類型`SampleExtension` `SampleExtension`為的屬性新增至`My`命名空間：

[!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]

## <a name="adding-events-to-custom-my-objects"></a>將事件加入至`My`自訂物件

您可以藉由`My.Application`擴充`My`命名空間中的`MyApplication`部分類別`My` ，使用物件來公開自訂物件的事件。 對於以 Windows 為基礎的專案，您可以在**方案總管**中按兩下專案的 [**我的專案**] 節點。 在 Visual Basic**專案設計**工具中，按一下 [**應用程式**] 索引標籤，然後按一下 [**視圖應用程式事件**] 按鈕。 將會建立名為*applicationevents.vb*的新檔案。 它包含用來擴充`MyApplication`類別的下列程式碼：

[!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]

您可以藉由將自訂事件`My`處理常式新增至`MyApplication`類別，為您的自訂物件新增事件處理常式。 自訂事件可讓您加入在加入、移除事件處理常式或引發事件時，將執行的程式碼。 請注意， `AddHandler`只有當使用者新增程式碼來處理事件時，才會執行自訂事件的程式碼。 例如，假設上一節`SampleExtension`中的物件有您想要`Load`為其加入自訂事件處理常式的事件。 下列程式碼範例會示範名為的自`SampleExtensionLoad`定義事件處理常式，當`My.SampleExtension.Load`事件發生時將會叫用它。 加入程式碼以處理新`My.SampleExtensionLoad`的事件時，會`AddHandler`執行此自訂事件的部分。 `MyApplication_SampleExtensionLoad`方法包含在程式碼範例中，以顯示處理`My.SampleExtensionLoad`事件的事件處理常式範例。 請注意， `SampleExtensionLoad`當您在編輯*applicationevents.vb*檔時，當您在程式碼編輯器上方的左側下拉式清單中選取 [**我的應用程式事件**] 選項時，就會出現此事件。

[!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]

## <a name="design-guidelines"></a>設計指導方針

當您開發`My`命名空間的延伸模組時，請使用下列指導方針來協助將延伸模組元件的維護成本降至最低：

- **只包含延伸模組邏輯。** `My`命名空間延伸中包含的邏輯應該只包含在`My`命名空間中公開必要功能所需的程式碼。 因為您的延伸模組會在使用者專案中做為原始程式碼，所以更新延伸模組元件會產生較高的維護成本，而且應該盡可能避免。
- **最小化專案假設。** 當您建立`My`命名空間的擴充功能時，請勿假設一組參考、專案層級的匯入或特定編譯器設定（例如， `Option Strict` off）。 相反地，請將`Global`相依性降至最低，並使用關鍵字來完整限定所有類型參考。 此外，請確定擴充功能會使用`Option Strict` on 進行編譯，以將擴充功能中的錯誤降至最低。
- **隔離延伸模組程式碼。** 將程式碼放在單一檔案中，可讓您輕鬆地將擴充功能部署為 Visual Studio 專案範本。 如需詳細資訊，請參閱本主題稍後的「封裝和部署擴充功能」。 將所有命名`My`空間延伸模組程式碼放入單一檔案或專案中的個別資料夾，也有助於使用者尋找`My`命名空間延伸模組。

## <a name="designing-class-libraries-for-my"></a>設計類別庫`My`

就像大部分的物件模型一樣，某些設計模式在`My`命名空間中的運作良好，其他則不適用。 設計`My`命名空間的延伸模組時，請考慮下列原則：

- **無狀態方法。** 命名空間中`My`的方法應該為特定工作提供完整的解決方案。 請確定傳遞至方法的參數值提供完成特定工作所需的所有輸入。 避免建立依賴先前狀態的方法，例如開啟資源的連接。
- **全域實例。** 在`My`命名空間中維護的唯一狀態，對專案而言是全域的。 例如， `My.Application.Info`會封裝在整個應用程式中共用的狀態。
- **簡單的參數類型。** 避免複雜的參數類型，讓事情保持簡單。 相反地，請建立不接受參數輸入或接受簡單輸入類型（例如字串、基本類型等等）的方法。
- **Factory 方法。** 有些類型一定很難具現化。 提供 factory 方法做為命名空間`My`的延伸模組，可讓您更輕鬆地探索及使用屬於此類別的類型。 正常運作的 factory 方法範例是`My.Computer.FileSystem.OpenTextFileReader`。 .NET Framework 中有數個可用的資料流程類型。 `OpenTextFileReader`藉由明確指定文字檔，可協助使用者瞭解要使用哪一個資料流程。

這些指導方針不會排除類別庫的一般設計原則。 相反地，它們是針對使用 Visual Basic 和`My`命名空間的開發人員優化的建議。 如需建立類別庫的一般設計原則，請參閱[架構設計方針](../../../standard/design-guidelines/index.md)。

## <a name="packaging-and-deploying-extensions"></a>封裝和部署擴充功能

您可以在`My` Visual Studio 專案範本中包含命名空間延伸模組，也可以封裝您的擴充功能，並將其部署為 Visual Studio 專案範本。 當您將`My`命名空間延伸模組封裝為 Visual Studio 專案範本時，您可以利用 Visual Basic 提供的其他功能。 這些功能可讓您在專案參考特定元件時包含延伸模組，或讓使用者使用 [Visual Basic 專案設計`My`工具] 的 [**我的延伸**模組] 頁面，明確地加入您的命名空間延伸模組。

如需如何部署`My`命名空間延伸模組的詳細資訊，請參閱[封裝和部署自訂 My extensions](packaging-and-deploying-custom-my-extensions.md)。

## <a name="see-also"></a>另請參閱

- [封裝和部署自訂的 My 擴充](packaging-and-deploying-custom-my-extensions.md)
- [擴充 Visual Basic 應用程式模型](extending-the-visual-basic-application-model.md)
- [自訂 My 中可用的物件](customizing-which-objects-are-available-in-my.md)
- [My 擴充頁、專案設計工具](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [部分](../../language-reference/modifiers/partial.md)
