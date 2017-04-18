---
title: "擴充 My 命名空間，在 Visual Basic |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddingMyExtensions
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
- My namespace, extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1d1e957536f35b81a9672994c9d4d261afb764ea
ms.lasthandoff: 03/13/2017

---
# <a name="extending-the-my-namespace-in-visual-basic"></a>擴充 Visual Basic 中的 My 命名空間
`My`在 Visual Basic 中的命名空間會公開屬性和方法，可讓您輕鬆地利用.NET Framework 的功能。 `My`命名空間簡化一般的程式設計問題，通常以一行程式碼能夠困難的工作。 此外，`My`命名空間可完全擴充，可讓您可以自訂的行為`My`並將新的服務加入至階層中以配合特定應用程式的需求。 本主題同時討論如何以自訂現有的成員`My`命名空間，以及如何加入您自己的自訂類別，以`My`命名空間。  
  
 **主題內容**  
  
-   [自訂現有的 My 命名空間成員](#customizing)  
  
-   [將成員加入至 My 物件](#addingtoobjects)  
  
-   [新增自訂物件以 My 命名空間](#addingcustom)  
  
-   [將成員加入至 My 命名空間](#addingtonamespace)  
  
-   [將事件加入至自訂的 My 物件](#addingevents)  
  
-   [設計指導方針](#design)  
  
-   [設計的類別庫我](#designing)  
  
-   [封裝和部署擴充功能](#packaging)  
  
##  <a name="customizing"></a>自訂現有的 My 命名空間成員  
 `My`命名空間，在 Visual Basic 會公開常用的應用程式、 您的電腦，及更多相關資訊。 如需完整的清單中物件的`My`命名空間，請參閱[我參考](../../../visual-basic/language-reference/keywords/my-reference.md)。 您可能必須自訂現有的成員`My`命名空間，讓它們更符合應用程式的需求。 物件中的任何屬性`My`不是唯讀的命名空間可以設定為某個自訂值。  
  
 例如，假設您經常使用`My.User`物件來存取目前安全性內容執行您的應用程式的使用者。 不過，您的公司會使用自訂的使用者物件公開 （expose） 的其他資訊與公司內的使用者功能。 在此案例中，您可以取代預設值的`My.User.CurrentPrincipal`與您自己自訂的主體物件，如下列範例所示的執行個體的屬性。  
  
 [!code-vb[VbVbcnExtendingMy #&1;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 設定`CurrentPrincipal`屬性`My.User`物件變更執行應用程式的身分識別。 `My.User`物件，反而會傳回新指定的使用者的相關資訊。  
  
##  <a name="addingtoobjects"></a>將成員加入至 My 物件  
 從傳回的型別`My.Application`和`My.Computer`定義為`Partial`類別。 因此，您可以擴充`My.Application`和`My.Computer`藉由建立物件`Partial`名為類別`MyApplication`或`MyComputer`。 這個類別不能`Private`類別。 如果您指定之類別的一部分`My`命名空間，您可以新增屬性和方法，將會包含在`My.Application`或`My.Computer`物件。  
  
 例如，下列範例會加入一個名為屬性`DnsServerIPAddresses`到`My.Computer`物件。  
  
 [!code-vb[VbVbcnExtendingMy #&2;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a>新增自訂物件以 My 命名空間  
 雖然`My`命名空間提供許多常見的程式設計工作的解決方案，可能會遇到的工作，`My`命名空間不能解決。 例如，您的應用程式可能需要存取使用者資料的自訂目錄服務或應用程式可能會使用與 Visual Basic 預設不會安裝的組件。 您可以擴充`My`命名空間包含專屬於您的環境的一般工作的自訂解決方案。 `My`命名空間可以輕鬆地擴充以加入新的成員，以符合成長的應用程式需求。 此外，您可以部署您`My`給其他開發人員為 Visual Basic 範本命名空間擴充。  
  
###  <a name="addingtonamespace"></a>將成員加入至 My 命名空間  
 因為`My`是命名空間，像任何其他命名空間，您可以加入最上層屬性，只要加入模組，並指定`Namespace`的`My`。 加上註解與模組`HideModuleName`屬性，如下列範例所示。 `HideModuleName`屬性可確保，IntelliSense 將不會顯示模組名稱顯示的成員時`My`命名空間。  
  
 [!code-vb[VbVbcnExtendingMy #&3;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 若要將成員加入至`My`命名空間，將屬性加入所需的模組。 每個屬性加入至`My`命名空間，加入私用欄位的型別`ThreadSafeObjectProvider(Of T)`，其中型別是由您的自訂屬性所傳回的型別。 這個欄位用來建立安全執行緒物件執行個體，要傳回的屬性，藉由呼叫`GetInstance`方法。 如此一來，每個執行緒存取的擴充的屬性，就會收到自己的傳回型別執行個體。 下列範例會加入一個名為屬性`SampleExtension`別的`SampleExtension`到`My`命名空間︰  
  
 [!code-vb[VbVbcnExtendingMy #&4;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a>將事件加入至自訂的 My 物件  
 您可以使用`My.Application`物件來公開您的自訂事件`My`擴充物件`MyApplication`中的部分類別`My`命名空間。 您可以按兩下 Windows 為基礎的專案**我的專案**中為您的專案中的節點**方案總管 中**。 在 Visual Basic 中**專案設計工具**，按一下 `Application`索引標籤，然後按一下  `View Application Events`  按鈕。 將建立名為 ApplicationEvents.vb 的新檔案。 它包含下列程式碼來擴充`MyApplication`類別。  
  
 [!code-vb[VbVbcnExtendingMy #&5;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 您可以新增您的自訂事件處理常式`My`物件加入至自訂的事件處理常式`MyApplication`類別。 自訂事件可讓您將會在事件處理常式加入、 移除或引發事件時執行的程式碼。 請注意，`AddHandler`自訂事件只會執行程式碼會加入由處理事件的使用者程式碼。 例如，請考慮`SampleExtension`物件從上一節有`Load`您想要新增的自訂事件處理常式的事件。 下列程式碼範例顯示名為的自訂事件處理常式`SampleExtensionLoad`，它就會叫用時`My.SampleExtension.Load`就會發生事件。 程式碼加入至新的處理時`My.SampleExtensionLoad`事件`AddHandler`這個自訂事件程式碼的一部分執行。 `MyApplication_SampleExtensionLoad`方法來處理事件處理常式的範例程式碼範例包含`My.SampleExtensionLoad`事件。 請注意，`SampleExtensionLoad`事件時，會使用您選取**我的應用程式事件**中左邊的下拉式清單上述程式碼編輯器中編輯 ApplicationEvents.vb 檔案時的選項。  
  
 [!code-vb[VbVbcnExtendingMy #&6;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a>設計指導方針  
 當您開發的擴充功能`My`命名空間中，使用下列指導方針來協助您擴充功能元件的維護成本降至最低。  
  
-   **包含擴充邏輯。** 中所包含的邏輯`My`命名空間擴充功能應該包含來公開必要的功能中的程式碼`My`命名空間。 因為您的擴充功能會以原始程式碼存在使用者專案中，更新擴充功能元件成本也較高的維護，應儘可能避免。  
  
-   **最小化專案的假設。** 當您建立您的擴充功能的`My`命名空間，請不要假設一組參考、 匯入專案層級或特定的編譯器設定 (例如，`Option Strict`關閉)。 相反地，最小化的相依性，並使用完整限定所有型別參考`Global`關鍵字。 此外，請確定延伸模組編譯與`Option Strict`上延伸模組中的錯誤降至最低。  
  
-   **隔離的延伸模組程式碼。** 將程式碼放在單一檔案，可讓您擴充功能可方便部署以 Visual Studio 項目範本。 如需詳細資訊，請參閱本主題稍後的 「 封裝及部署擴充 」。 將所有`My`單一檔案中的命名空間延伸模組程式碼或個別的資料夾，在專案中，也有助於找出使用者`My`命名空間擴充。  
  
##  <a name="designing"></a>設計的類別庫我  
 在此情況下，與大多數的物件模型，一些設計模式中正常運作`My`命名空間和其他人則否。 設計的擴充功能時`My`命名空間，請考慮下列原則︰  
  
-   **無狀態的方法。** 中的方法`My`命名空間應該提供特定工作的完整解決方案。 請確定傳遞至方法的參數值，提供完成特定工作所需的所有輸入。 請避免建立依賴前一個狀態，例如資源的開啟連接的方法。  
  
-   **全域執行個體。** 唯一的狀態會保留在`My`命名空間是專案的全域。 例如，`My.Application.Info`封裝共用整個應用程式的狀態。  
  
-   **簡單的參數型別。** 簡單起見，避免複雜的參數型別。 相反地，建立 不要使用輸入參數的方法，或只使用簡單的輸入的類型，例如字串、 基本型別，等等。  
  
-   **原廠方法。** 某些類型非常難以具現化。 提供 factory 方法當做擴充`My`命名空間可讓您更輕鬆地探索及使用屬於此分類的類型。 適合的 factory 方法的範例是`My.Computer.FileSystem.OpenTextFileReader`。 沒有可用的.NET Framework 中的數個資料流類型。 具體來說，指定文字檔案`OpenTextFileReader`可協助使用者了解要使用的資料流。  
  
 這些指導方針並未預先排除類別庫的一般設計原則。 而是在最適合用於使用 Visual Basic 開發人員的建議和`My`命名空間。 建立類別庫的一般設計原則，請參閱[Framework 設計方針](http://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b)。  
  
##  <a name="packaging"></a>封裝和部署擴充功能  
 您可以包含`My`命名空間擴充 Visual Studio 專案範本，或者您可以封裝您的擴充功能，並將其部署為 Visual Studio 項目範本。 當您封裝您`My`做為 Visual Studio 項目範本的命名空間擴充功能，您可以利用 Visual Basic 所提供的其他功能。 這些功能可讓您在專案參考特定的組件，包括副檔名，或讓使用者明確地加入您`My`所使用的命名空間擴充**My 擴充**Visual Basic 專案設計工具頁面。  
  
 如需詳細資訊，有關如何部署`My`命名空間擴充功能，請參閱[封裝和部署自訂 My 擴充](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [封裝和部署自訂的 My 延伸模組](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)   
 [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [自訂可用的物件在我](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [專案設計工具 my 擴充頁](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)   
 [專案設計工具、應用程式頁面 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)   
 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
