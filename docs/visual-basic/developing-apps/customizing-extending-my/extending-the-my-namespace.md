---
title: 擴充 Visual Basic 中的 My 命名空間
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 4d7bb6eef398746a4bd2dc4dbf3d526da1c1e0f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014215"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>擴充 Visual Basic 中的 My 命名空間
`My` Visual Basic 中的命名空間會公開屬性和方法可讓您輕鬆地利用.NET Framework 的強大功能。 `My`命名空間簡化了一般的程式設計問題，通常在一行程式碼中減少困難的工作。 此外，`My`命名空間是完全可延伸，讓您可以自訂的行為`My`並將新的服務新增至階層中以配合特定應用程式的需求。 本主題討論如何進行自訂的現有成員`My`命名空間，以及如何新增您自己的自訂類別，以`My`命名空間。  
  
 **主題內容**  
  
- [自訂現有的 My 命名空間成員](#customizing)  
  
- [將成員加入至我的物件](#addingtoobjects)  
  
- [新增自訂的物件，以 My 命名空間](#addingcustom)  
  
- [將成員加入至我的命名空間](#addingtonamespace)  
  
- [將事件加入至自訂的 My 物件](#addingevents)  
  
- [設計指導方針](#design)  
  
- [設計類別庫的我](#designing)  
  
- [封裝和部署擴充功能](#packaging)  
  
## <a name="customizing"></a> 自訂現有的 My 命名空間成員  
 `My`命名空間，在 Visual Basic 會公開中的常用的應用程式、 您的電腦，和更多功能的相關資訊。 如需完整的清單中的物件`My`命名空間，請參閱 <<c2> [ 我參考](../../../visual-basic/language-reference/keywords/my-reference.md)。 您可能需要自訂的現有成員`My`命名空間，讓它們更符合您的應用程式的需求。 中的物件的任何屬性`My`不是唯讀的命名空間可以設定為某個自訂值。  
  
 例如，假設您經常使用`My.User`物件來存取目前安全性內容執行您的應用程式的使用者。 不過，貴公司會使用自訂的使用者物件公開的其他資訊和在公司內的使用者功能。 在此案例中，您可以取代預設值`My.User.CurrentPrincipal`與您自己自訂的主體物件，如下列範例所示的執行個體的屬性。  
  
 [!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]  
  
 設定`CurrentPrincipal`屬性上的`My.User`物件變更應用程式所執行的身分識別。 `My.User`物件，接著會傳回新指定的使用者的相關資訊。  
  
## <a name="addingtoobjects"></a> 將成員加入至我的物件  
 從傳回的型別`My.Application`並`My.Computer`定義為`Partial`類別。 因此，您可以延伸`My.Application`並`My.Computer`所建立的物件`Partial`名為類別`MyApplication`或`MyComputer`。 這個類別不能`Private`類別。 如果您指定的類別的一部分`My`命名空間中，您可以新增屬性和方法，將會包含`My.Application`或`My.Computer`物件。  
  
 例如，下列範例會將名為的屬性`DnsServerIPAddresses`至`My.Computer`物件。  
  
 [!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]  
  
## <a name="addingcustom"></a> 新增自訂的物件，以 My 命名空間  
 雖然`My`命名空間提供許多常見的程式設計工作的解決方案，您可能會遇到的工作，`My`命名空間不能解決。 例如，您的應用程式可能需要存取使用者資料的自訂目錄服務，或您的應用程式可能會使用與 Visual Basic 預設不會安裝的組件。 您可以擴充`My`命名空間包含您環境特有的一般工作的自訂解決方案。 `My`命名空間可以輕鬆擴充至加入新的成員，以滿足不斷成長的應用程式需求。 此外，您可以在其中部署您`My`做為 Visual Basic 範本的其他開發人員的命名空間延伸模組。  
  
### <a name="addingtonamespace"></a> 將成員加入至我的命名空間  
 因為`My`是命名空間類似任何其他命名空間，您可以加入最上層屬性，只新增一個模組，並指定`Namespace`的`My`。 加上註解的模組`HideModuleName`屬性，如下列範例所示。 `HideModuleName`屬性可確保，IntelliSense 會顯示模組名稱顯示的成員時`My`命名空間。  
  
 [!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]  
  
 若要將成員新增至`My`命名空間，將屬性加入所需的模組。 每個屬性新增至`My`命名空間，加入私用欄位的型別`ThreadSafeObjectProvider(Of T)`，其中型別是您的自訂屬性所傳回的類型。 這個欄位用來建立安全執行緒物件執行個體，藉由呼叫由屬性所傳回`GetInstance`方法。 如此一來，每個執行緒都存取擴充的屬性，就會收到自己的傳回型別執行個體。 下列範例會將名為的屬性`SampleExtension`型別的`SampleExtension`至`My`命名空間：  
  
 [!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]  
  
## <a name="addingevents"></a> 將事件加入至自訂的 My 物件  
 您可以使用`My.Application`來公開您的自訂事件的物件`My`物件來擴充`MyApplication`中的部分類別`My`命名空間。 對於以 Windows 為基礎的專案，您可以按兩下**My Project**中為您的專案中的節點**方案總管 中**。 在 Visual Basic**專案設計工具**，按一下`Application`索引標籤，然後按一下`View Application Events` 按鈕。 將建立名為 ApplicationEvents.vb 的新檔案。 它包含下列程式碼來擴充`MyApplication`類別。  
  
 [!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]  
  
 您可以新增您的自訂事件處理常式`My`物件加入至自訂的事件處理常式`MyApplication`類別。 自訂事件可讓您新增事件處理常式加入、 移除或引發事件時執行的程式碼。 請注意，`AddHandler`程式碼的自訂事件只會執行程式碼會加入使用者對處理事件。 比方說，認為`SampleExtension`物件上一節有`Load`您想要新增的自訂事件處理常式的事件。 下列程式碼範例顯示名為自訂的事件處理常式`SampleExtensionLoad`，它就會叫用時`My.SampleExtension.Load`就會發生事件。 程式碼來處理新的新增時`My.SampleExtensionLoad`事件，`AddHandler`執行此自訂事件的程式碼的一部分。 `MyApplication_SampleExtensionLoad`方法以顯示處理的事件處理常式的範例程式碼範例包含`My.SampleExtensionLoad`事件。 請注意，`SampleExtensionLoad`事件時，會提供您所選取**我的應用程式事件**在左邊的下拉式清單上方的程式碼編輯器編輯 ApplicationEvents.vb 檔案時的選項。  
  
 [!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]  
  
## <a name="design"></a> 設計指導方針  
 當您開發延伸模組`My`命名空間中，使用下列指導方針，以協助您擴充功能元件的維護成本降至最低。  
  
- **包含延伸模組邏輯。** 中包含的邏輯`My`命名空間延伸模組應該包含需要公開所需的功能中的程式碼`My`命名空間。 因為您的延伸模組會位在使用者專案中，以原始碼，更新擴充功能的元件會產生較高的維護成本，並應該儘可能避免。  
  
- **最小化專案的假設。** 當您建立您的擴充功能的`My`命名空間，不要假設一組參考，專案層級 imports 或特定的編譯器設定 (例如`Option Strict`關閉)。 相反地，最小化相依性，並使用完整限定所有型別參考`Global`關鍵字。 此外，請確定擴充功能會編譯使用`Option Strict`在延伸模組中的錯誤降至最低。  
  
- **找出延伸模組程式碼。** 將程式碼放在單一檔案，可讓您的擴充功能可輕鬆部署為 Visual Studio 項目範本。 如需詳細資訊，請參閱本主題稍後的 「 封裝及部署擴充功能 」。 將所有`My`命名空間延伸模組程式碼，在單一檔案或不同的資料夾中的專案，也有助於使用者找出`My`命名空間延伸模組。  
  
## <a name="designing"></a> 設計類別庫的我  
 在此情況下，大部分的物件模型，一些設計模式適用於`My`命名空間，有些則沒有。 設計的延伸模組時`My`命名空間，請考量以下原則：  
  
- **無狀態的方法。** 中的方法`My`命名空間應該提供特定工作的完整解決方案。 請確定傳遞給方法的參數值提供完成特定工作所需的所有輸入。 請避免建立依賴先前的狀態，例如開啟的連線資源的方法。  
  
- **全域執行個體。** 唯一的狀態會保留在`My`命名空間是專案的全域。 比方說，`My.Application.Info`封裝共用整個應用程式的狀態。  
  
- **簡單的參數型別。** 簡單起見藉由避免複雜的參數類型。 相反地，建立 不要使用輸入參數的方法，或可接受簡單的輸入的類型，例如字串、 基本類型，等等。  
  
- **Factory 方法。** 某些類型非常難以具現化。 提供 factory 方法當做擴充`My`命名空間可讓您更輕鬆地探索及取用屬於此分類的類型。 非常適合的 factory 方法的範例是`My.Computer.FileSystem.OpenTextFileReader`。 有.NET Framework 中可用的數個資料流類型。 藉由明確地說，指定文字檔案`OpenTextFileReader`可協助使用者了解要使用的資料流。  
  
 這些指導方針不會排除類別庫的一般設計原則。 相反地，它們是最適合用於開發人員使用 Visual Basic 的建議和`My`命名空間。 建立類別庫的一般設計原則，請參閱 < [Framework 設計方針](../../../standard/design-guidelines/index.md)。  
  
## <a name="packaging"></a> 封裝和部署擴充功能  
 您可以包含`My`命名空間延伸模組，Visual Studio 專案範本，或者您可以封裝您的擴充功能，並將其部署為 Visual Studio 項目範本。 當您封裝您`My`做為 Visual Studio 項目範本的命名空間延伸模組，您可以利用 Visual Basic 所提供的其他功能。 這些功能可讓您納入延伸模組，當專案參考特定組件，或是讓使用者明確地將您`My`使用的命名空間延伸模組**My 擴充**Visual basic 的頁面專案設計工具。  
  
 如需如何部署的詳細資訊`My`命名空間延伸模組，請參閱[封裝和部署自訂 My 擴充](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)。  
  
## <a name="see-also"></a>另請參閱

- [封裝和部署自訂的 My 擴充](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)
- [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [我的延伸模組頁面、專案設計工具](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [專案設計工具、應用程式頁面 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
