---
title: "Extending the My Namespace in Visual Basic | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AddingMyExtensions"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My namespace, customizing"
  - "My namespace"
  - "My namespace, extending"
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Extending the My Namespace in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Visual Basic 中的 `My` 命名空間所公開的屬性和方法可以讓您輕鬆利用 .NET Framework 的功能。  `My` 命名空間可簡化一般程式設計問題，通常能夠將困難的工作簡化成一行程式碼。  此外，`My` 命名空間可完全擴充，因此您可以自訂 `My` 的行為，並將新的服務加入至階層中以配合特定應用程式的需求。  本主題同時討論如何自訂 `My` 命名空間現有的成員，以及如何將您的自訂類別加入至 `My` 命名空間。  
  
 **主題內容**  
  
-   [自訂現有的 My 命名空間成員](#customizing)  
  
-   [將成員加入至 My 物件](#addingtoobjects)  
  
-   [將自訂物件加入至 My 命名空間](#addingcustom)  
  
-   [將成員加入至 My 命名空間](#addingtonamespace)  
  
-   [將事件加入至自訂的 My 物件](#addingevents)  
  
-   [設計方針](#design)  
  
-   [設計 My 的類別庫](#designing)  
  
-   [封裝和部署擴充](#packaging)  
  
##  <a name="customizing"></a> 自訂現有的 My 命名空間成員  
 Visual Basic 中的 `My` 命名空間會公開有關您的應用程式、電腦等其他常用資訊。  如需 `My` 命名空間中物件的完整清單，請參閱 [My Reference](../../../visual-basic/language-reference/keywords/my-reference.md)。  您可能必須自訂 `My` 命名空間現有的成員，才能使這些成員更符合應用程式的需求。  `My` 命名空間中物件的任何屬性，只要不是唯讀，就可以設定為自訂值。  
  
 例如，假設您經常使用 `My.User` 物件來存取執行您的應用程式之使用者的目前安全性內容。  但是，您的公司使用自訂的使用者物件來公開其他資訊與功能供公司內的使用者使用。  在這個情況下，您可以使用自訂主體物件的執行個體，取代 `My.User.CurrentPrincipal` 屬性的預設值。  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/visualbasic/extending-the-my-namespace_1.vb)]  
  
 設定 `My.User` 物件上的 `CurrentPrincipal` 屬性，會變更應用程式執行的識別。  `My.User` 物件會傳回新指定之使用者的相關資訊。  
  
##  <a name="addingtoobjects"></a> 將成員加入至 My 物件  
 從 `My.Application` 和 `My.Computer` 傳回的型別是定義為 `Partial` 類別。  因此，您可以藉由建立 `Partial` 類別 \(名稱為 `MyApplication` 或 `MyComputer`\) 來擴充 `My.Application` 和 `My.Computer` 物件。  類別不能是 `Private` 類別。  如果您將類別指定為 `My` 命名空間的一部分，就可以加入將會隨附於 `My.Application` 或 `My.Computer` 物件的屬性和方法。  
  
 例如，下列範例會將名為 `DnsServerIPAddresses` 的屬性加入至 `My.Computer` 物件。  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/visualbasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a> 將自訂物件加入至 My 命名空間  
 雖然 `My` 命名空間提供許多常見程式設計工作的方案，但是，您可能會遇到 `My` 命名空間無法處理的工作。  例如，您的應用程式可能會存取自訂目錄服務以取得使用者資料，或者您的應用程式可能會使用預設不會與 Visual Basic 一起安裝的組件。  您可以擴充 `My` 命名空間，將自訂方案納入您的環境特定的一般工作中。  您可以很容易地擴充 `My` 命名空間，以便加入新的成員來滿足不斷成長的應用程式需求。  此外，您可以將 `My` 命名空間擴充部署至其他開發程式，做為 Visual Basic 範本。  
  
###  <a name="addingtonamespace"></a> 將成員加入至 My 命名空間  
 因為 `My` 命名空間和任何其他命名空間一樣，只要加入模組並指定 `My` 的 `Namespace`，就可以加入上層屬性。  為模組加上 `HideModuleName` 屬性的附註，如下列範例所示。  `HideModuleName` 屬性可確保 IntelliSense 在顯示 `My` 命名空間的成員時，不會顯示模組名稱。  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/visualbasic/extending-the-my-namespace_3.vb)]  
  
 若要將成員加入至 `My` 命名空間，請視需要將屬性加入至模組中。  對每一個加入至 `My` 命名空間的屬性而言，加入型別為 `ThreadSafeObjectProvider(Of T)` 的私用欄位，這個型別就是您的自訂屬性所傳回的型別。  這個欄位是用於建立執行緒安全的物件執行個體，呼叫 `GetInstance` 方法可傳回這個執行個體。  因此，每一個存取擴充的屬性的執行緒，都會收到本身傳回之型別的執行個體。  下列範例會將型別為 `SampleExtension` 的屬性 \(名稱為 `SampleExtension`\) 加入至 `My` 命名空間：  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/visualbasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a> 將事件加入至自訂的 My 物件  
 您可以使用 `My.Application` 物件，透過擴充 `My` 命名空間中的 `MyApplication` 部分類別，以公開您自訂 `My` 物件的事件。  如果是 Windows 架構專案，您可以在 \[**方案總管**\] 中的專案上，按兩下 \[**我的專案**\] 節點。  按一下 Visual Basic \[**專案設計工具**\] 中的 \[`Application`\] 索引標籤，然後按一下 \[`View Application Events`\] 按鈕。  隨即會建立名稱為 ApplicationEvents.vb 的新檔案。  檔案內含下列程式碼以擴充 `MyApplication` 類別。  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/visualbasic/extending-the-my-namespace_5.vb)]  
  
 您可以將自訂事件處理常式加入至 `MyApplication` 類別，即可加入自訂的 `My` 物件之事件處理常式。  自訂事件可讓您加入程式碼，此程式碼會在加入、移除事件處理常式或引發事件時執行。  請注意，自訂事件的 `AddHandler` 程式碼只會在使用者將程式碼加入以處理事件時才會執行。  例如，假設上一節中的 `SampleExtension` 物件有 `Load` 事件，而您要為這個事件加入一個自訂事件處理常式。  下列程式碼範例顯示名稱為 `SampleExtensionLoad` 的自訂事件處理常式，這個事件處理常式會於 `My.SampleExtension.Load` 事件發生時叫用。  當加入程式碼以處理新的 `My.SampleExtensionLoad` 事件時，就會執行這個自訂事件程式碼的 `AddHandler` 部分。  `MyApplication_SampleExtensionLoad` 方法會包含在程式碼範例中，以顯示處理 `My.SampleExtensionLoad` 事件的事件處理常式範例。  請注意，當您編輯 ApplicationEvents.vb 檔案時，如果在 \[程式碼編輯器\] 上的下拉式清單中選取 \[**我的應用程式事件**\] 選項時，就可以使用 `SampleExtensionLoad` 事件。  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/visualbasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a> 設計方針  
 當您開發 `My` 命名空間的擴充時，請遵循下列方針以協助降低擴充元件的維護成本。  
  
-   **只包含擴充邏輯。** `My` 命名空間擴充中所包含的邏輯，只能包括用來公開 `My` 命名空間中所需功能的程式碼。  因為您的擴充會存在使用者專案中做為原始程式碼，所以更新擴充元件會導致過高的維護成本，因此應該盡可能避免。  
  
-   **盡可能簡化專案的規模。** 當您建立 `My` 命名空間的擴充時，請不要使用一組參考、專案層級的匯入或特定的編譯器設定 \(例如 `Option Strict` 設定為 Off\)。  但是請將相依性減至最低，並使用 `Global` 關鍵字以完整限定所有型別參考。  此外，請確保擴充程式編譯時 `Option Strict` 會設定為 On，以盡可能降低擴充中的錯誤。  
  
-   **隔離擴充程式碼。** 將程式碼放在單一檔案中，讓您的擴充可以輕鬆部署為 Visual Studio 項目範本。  如需詳細資訊，請參閱本主題稍後的「封裝及部署擴充」。  將所有 `My` 命名空間擴充程式碼放在單一檔案中，或是專案中的獨立資料夾中，也有助於使用者找到 `My` 命名空間擴充。  
  
##  <a name="designing"></a> 設計 My 的類別庫  
 和大部分物件模型的情形一樣，有些設計模式在 `My` 命名空間中能正常運作，有些則不行。  設計 `My` 命名空間的擴充時，請考慮下列原則：  
  
-   **沒有狀態的方法。** `My` 命名空間中的方法，應為特定工作提供完整的方案。  確保傳送給方法的參數值，會提供完成特定工作所需的所有輸入。  避免建立必須依賴前一個狀態的方法，例如開啟資源的連接。  
  
-   **全域執行個體。** `My` 命名空間中唯一維持的狀態，就是專案的全域狀態。  例如，`My.Application.Info` 會封裝應用程式所共用的狀態。  
  
-   **簡單的參數型別。** 避免使用複雜的參數型別，以維持簡易性。  因此，建立方法時不要使用參數輸入，或只使用簡單的輸入型別，例如字串、基本型別等等。  
  
-   **Factory 方法。** 有些型別非常難以具現化。  提供 Factory 方法做為 `My` 命名空間的擴充，可以讓您更容易探索及使用這個種類的型別。  其中一個可正常運作的 Factory 方法就是 `My.Computer.FileSystem.OpenTextFileReader`。  .NET Framework 中提供幾個資料流型別。  `OpenTextFileReader` 會特別指定文字檔案，以協助使用者了解該使用哪個資料流。  
  
 這些方針並未預先排除類別庫的一般設計原則。  相反地，這些建議還經過最佳化，以供使用 Visual Basic 和 `My` 命名空間的開發人員參考。  如需建立類別庫的一般設計原則，請參閱[Framework 設計方針](../Topic/Framework%20Design%20Guidelines.md)。  
  
##  <a name="packaging"></a> 封裝和部署擴充  
 您可以將 `My` 命名空間擴充包含在 Visual Studio 專案範本中，或者，您可以封裝擴充並將其部署為 Visual Studio 項目範本。  當您將 `My` 命名空間擴充封裝為 Visual Studio 項目範本時，就可以使用 Visual Basic 所提供的其他功能。  這些功能可以讓您在專案參考特定組件時包含擴充，或讓使用者使用 Visual Basic 專案設計工具的 \[**My Extensions**\] 頁面，以明確加入 `My` 命名空間擴充。  
  
 如需如何部署 `My` 命名空間擴充的詳細資訊，請參閱 [Packaging and Deploying Custom My Extensions](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)。  
  
## 請參閱  
 [Packaging and Deploying Custom My Extensions](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)   
 [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [專案設計工具、My 擴充頁](/visual-studio/ide/reference/my-extensions-page-project-designer-visual-basic)   
 [應用程式頁面，專案設計工具 \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)