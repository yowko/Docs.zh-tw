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
ms.openlocfilehash: 22d9d0def302b870de6f3e5ca4c142758b21314c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591829"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>擴充 Visual Basic 中的 My 命名空間
`My`在 Visual Basic 中的命名空間會公開屬性和方法，可讓您輕鬆地利用.NET Framework 的功能。 `My`命名空間可簡化常見的程式設計問題，通常在一行程式碼中減少困難的工作。 此外，`My`命名空間是完全可延伸，因此，您可以自訂的行為`My`並將新的服務加入至階層中以配合特定的應用程式的需求。 本主題討論如何以自訂的現有成員`My`命名空間，以及如何新增您自己自訂的類別，以`My`命名空間。  
  
 **主題內容**  
  
-   [自訂現有的 My 命名空間成員](#customizing)  
  
-   [將成員新增至 My 物件](#addingtoobjects)  
  
-   [將自訂物件，若要加入 My 命名空間](#addingcustom)  
  
-   [將成員加入至我的命名空間](#addingtonamespace)  
  
-   [將事件加入至自訂的 My 物件](#addingevents)  
  
-   [設計指導方針](#design)  
  
-   [設計的類別庫我](#designing)  
  
-   [封裝和部署擴充功能](#packaging)  
  
##  <a name="customizing"></a> 自訂現有的 My 命名空間成員  
 `My`經常使用在 Visual Basic 會公開的命名空間的應用程式、 您的電腦和更多相關資訊。 如需完整的清單中的物件`My`命名空間，請參閱[My 參考](../../../visual-basic/language-reference/keywords/my-reference.md)。 您可能必須自訂現有的成員`My`命名空間，讓它們更好的符合您的應用程式的需求。 物件中的任何屬性`My`不是唯讀的命名空間可以將自訂的值。  
  
 例如，假設您經常使用`My.User`物件來存取目前安全性內容執行您的應用程式的使用者。 不過，貴公司使用自訂的使用者物件公開的其他資訊與使用者在公司內的功能。 在此案例中，您可以取代預設值的`My.User.CurrentPrincipal`與您自己自訂的主體物件，如下列範例所示的執行個體的屬性。  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 設定`CurrentPrincipal`屬性`My.User`物件變更執行應用程式的身分識別。 `My.User`物件，接著，會傳回新指定的使用者的相關資訊。  
  
##  <a name="addingtoobjects"></a> 將成員新增至 My 物件  
 從傳回型別`My.Application`和`My.Computer`定義為`Partial`類別。 因此，您可以擴充`My.Application`和`My.Computer`物件藉由建立`Partial`名為類別`MyApplication`或`MyComputer`。 這個類別不能`Private`類別。 如果您指定之類別的一部分`My`命名空間中，您可以新增屬性和方法，將會包含在`My.Application`或`My.Computer`物件。  
  
 例如，下列範例會將名為的屬性`DnsServerIPAddresses`至`My.Computer`物件。  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a> 將自訂物件，若要加入 My 命名空間  
 雖然`My`命名空間提供許多常見的程式設計工作的解決方案，您可能會遇到工作，`My`命名空間不能解決。 例如，您的應用程式可能需要存取使用者資料的自訂目錄服務或應用程式可能會使用與 Visual Basic 預設不會安裝的組件。 您可以擴充`My`包含專屬於您的環境的一般工作的自訂方案的命名空間。 `My`命名空間可以輕易地延伸到將新成員加入需求日益增加的應用程式。 此外，您可以部署您`My`給其他開發人員做為 Visual Basic 範本命名空間擴充功能。  
  
###  <a name="addingtonamespace"></a> 將成員加入至我的命名空間  
 因為`My`是命名空間像任何其他命名空間，您可以加入最上層屬性，只將模組加入，並指定`Namespace`的`My`。 加上註解之模組的`HideModuleName`屬性，如下列範例所示。 `HideModuleName`屬性可確保，IntelliSense 會顯示模組名稱顯示的成員時`My`命名空間。  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 若要將成員加入`My`命名空間中，將屬性加入所需的模組。 每個屬性加入至`My`命名空間中，加入私用欄位的型別`ThreadSafeObjectProvider(Of T)`，其中型別是傳回自訂屬性的型別。 這個欄位用來建立具備執行緒安全物件執行個體的屬性所傳回的呼叫`GetInstance`方法。 如此一來，每個執行緒存取的擴充的屬性，就會收到自己的傳回型別執行個體。 下列範例會將名為的屬性`SampleExtension`型別的`SampleExtension`至`My`命名空間：  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a> 將事件加入至自訂的 My 物件  
 您可以使用`My.Application`物件來公開您的自訂事件`My`物件延伸`MyApplication`中的部分類別`My`命名空間。 針對 windows 專案，您可以按兩下**我的專案**中為您的專案中的節點**方案總管 中**。 在 Visual Basic 中**專案設計工具**，按一下 `Application`索引標籤，然後按一下  `View Application Events`  按鈕。 將會建立名為 ApplicationEvents.vb 新檔案。 它包含下列程式碼擴充`MyApplication`類別。  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 您可以加入事件處理常式，您的自訂`My`物件加入至自訂事件處理常式`MyApplication`類別。 自訂事件可讓您將加入事件處理常式加入、 移除或事件引發時執行的程式碼。 請注意，`AddHandler`自訂事件只會執行程式碼會加入由處理事件的使用者程式碼。 例如，請仔細考慮`SampleExtension`前一節的物件具有`Load`您想要新增的自訂事件處理常式的事件。 下列程式碼範例將示範名為的自訂事件處理常式`SampleExtensionLoad`，將會叫用時`My.SampleExtension.Load`就會發生事件。 程式碼加入至新處理時`My.SampleExtensionLoad`事件，`AddHandler`執行此自訂事件的程式碼的一部分。 `MyApplication_SampleExtensionLoad`方法包含程式碼範例所顯示的事件處理常式處理範例`My.SampleExtensionLoad`事件。 請注意，`SampleExtensionLoad`事件將在可用，當您選取**我的應用程式事件**左側下拉式清單上述程式碼編輯器中編輯 ApplicationEvents.vb 檔案時的選項。  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a> 設計指導方針  
 當您開發擴充功能`My`命名空間中，使用下列指導方針可協助您擴充功能元件的維護成本降至最低。  
  
-   **包含擴充邏輯。** 中所包含的邏輯`My`命名空間擴充功能應該包含來公開所需的功能中的程式碼`My`命名空間。 因為您的擴充功能會以原始碼存在使用者專案中，更新擴充功能的元件會產生較高的維護成本，應該儘可能避免。  
  
-   **最小化專案的假設。** 當您建立您的擴充功能的`My`命名空間，不會假設參考、 專案層級匯入或特定的編譯器設定的一組 (例如，`Option Strict`關閉)。 相反地，相依性降到最低，並使用完整限定類型的所有參考`Global`關鍵字。 此外，在使用編譯延伸模組`Option Strict`在延伸中的錯誤降至最低。  
  
-   **隔離的延伸模組程式碼。** 將程式碼放在單一檔案，可讓您的擴充功能輕鬆部署與 Visual Studio 項目範本。 如需詳細資訊，請參閱本主題稍後的 「 封裝和部署的擴充功能 」。 放置所有`My`單一檔案中的命名空間延伸模組程式碼或不同的資料夾中的專案，也有助於找出使用者`My`命名空間擴充功能。  
  
##  <a name="designing"></a> 設計的類別庫我  
 與大部分的物件模型的案例一樣，一些設計模式中正常運作`My`命名空間，有些則沒有。 設計的延伸模組時`My`命名空間，請考慮下列原則：  
  
-   **無狀態的方法。** 中的方法`My`命名空間應該提供完整的解決方案，以特定的工作。 請確定傳遞給方法的參數值提供完成特定工作所需的所有輸入。 應避免建立依賴先前的狀態，例如開啟的連接資源的方法。  
  
-   **全域執行個體。** 唯一的狀態會保留在`My`命名空間是專案的全域。 例如，`My.Application.Info`封裝共用整個應用程式的狀態。  
  
-   **簡單參數類型。** 避免使用複雜的參數類型，讓事情變簡單。 請改為建立方法時沒有參數輸入或可接受簡單的輸入的類型，例如字串或基本類型，等等。  
  
-   **Factory 方法。** 某些類型非常難以具現化。 提供 factory 方法當做擴充`My`命名空間可讓您更輕鬆地探索及取用歸類到此類別的類型。 Factory 方法，可正常運作的範例是`My.Computer.FileSystem.OpenTextFileReader`。 有數個資料流類型的.NET Framework 中可用。 具體來說，指定文字檔案`OpenTextFileReader`可協助使用者了解要使用的資料流。  
  
 這些指導方針不會排除之類別庫的一般程式設計原則。 而是在不適合用於使用 Visual Basic 開發人員的建議和`My`命名空間。 建立類別庫的一般設計原則，請參閱[Framework 設計方針](../../../standard/design-guidelines/index.md)。  
  
##  <a name="packaging"></a> 封裝和部署擴充功能  
 您可以包含`My`命名空間擴充 Visual Studio 專案範本，或者您可以封裝您的擴充功能，並將其部署為 Visual Studio 項目範本。 當您封裝您`My`命名空間擴充與 Visual Studio 項目範本，您可以利用 Visual Basic 所提供的其他功能。 這些功能可讓您在專案參考特定組件，包括副檔名，或讓使用者明確地將您`My`命名空間擴充功能，使用**My 擴充**Visual Basic 的頁面專案設計工具。  
  
 如需如何部署詳細資料`My`命名空間擴充功能，請參閱[封裝和部署自訂 My 擴充](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [封裝和部署自訂的 My 擴充](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)  
 [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [專案設計工具 my 擴充頁](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)  
 [專案設計工具、應用程式頁面 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
