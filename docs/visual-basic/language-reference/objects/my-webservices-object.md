---
title: "My.WebServices Object | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "My.WebServices"
  - "My.MyProject.WebServices"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.WebServices object"
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# My.WebServices Object
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

提供屬性，這些屬性建立並存取目前專案參考之每個 XML Web Service 的單一執行個體。  
  
## 備註  
 `My.WebServices` 物件會提供目前專案所參考之每個 Web 服務的執行個體。  每個執行個體都會視需要執行個體化。  您可以透過 `My.WebServices` 物件的屬性 \(Property\) 存取這些 Web 服務。  屬性名稱會與屬性所存取的 Web 服務名稱相同。  任何繼承自 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> 的類別 \(Class\) 都是 Web 服務。  如需將 Web 服務加入至專案的詳細資訊，請參閱 [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 `My.WebServices` 物件只會公開 \(Expose\) 與目前專案相關聯的 Web 服務。  它不會對在參考之 DLL 中宣告的 Web 服務提供存取權限。  若要存取 DLL 提供的 Web 服務，您必須使用 Web 服務的限定名稱 \(Qualified Name\)，格式為 *DllName*.*WebServiceName*。  如需詳細資訊，請參閱 [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 Web 應用程式無法使用物件和它的屬性。  
  
## 屬性  
 `My.WebServices` 物件的每個屬性都會對目前專案所參考之 Web 服務的執行個體提供存取。  屬性名稱會與屬性所存取的 Web 服務名稱相同，而屬性型別會與 Web 服務型別相同。  
  
> [!NOTE]
>  如果發生名稱衝突，存取 Web 服務的屬性名稱就是 *RootNamespace*\_*Namespace*\_*ServiceName*。  例如，假設有兩個名稱為 `Service1` 的 Web 服務。  如果其中一個服務位於根命名空間 `WindowsApplication1` 的命名空間 `Namespace1` 中，您可以使用 `My.WebServices.WindowsApplication1_Namespace1_Service1` 存取該服務。  
  
 當您第一次存取其中一個 `My.WebServices` 物件的屬性時，會建立新的 Web 服務執行個體並儲存它。  該屬性後續的存取權限會傳回 Web 服務的該執行個體。  
  
 您可以藉由將 `Nothing` 指定給該 Web 服務的屬性來處置 Web 服務。  屬性 Setter 會將 `Nothing` 指定給儲存的值。  如果將 `Nothing` 以外的任何值指定給屬性，則 Setter 會擲回 <xref:System.ArgumentException> 例外狀況。  
  
 您可以使用 `Is` 或 `IsNot` 運算子，測試 `My.WebServices` 物件的屬性是否會儲存 Web 服務的執行個體。  也可以使用這些運算子，檢查屬性的值是否為 `Nothing`。  
  
> [!NOTE]
>  通常，`Is` 或 `IsNot` 運算子必須讀取屬性值，才能執行比較作業。  不過，如果屬性目前儲存 `Nothing`，則屬性會建立 Web 服務的新執行個體，然後傳回該執行個體。  然而，Visual Basic 編譯器會特別處理 `My.WebServices` 物件的屬性，並允許 `Is` 或 `IsNot` 運算子檢查屬性的狀態，但是不會變更屬性的值。  
  
## 範例  
 這個範例會呼叫 `TemperatureConverter` XML Web Service 的 `FahrenheitToCelsius` 方法，並傳回結果。  
  
 [!CODE [VbVbalrMyWebService#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrMyWebService#1)]  
  
 若要讓這個範例運作，您的專案必須參考名為 `Converter` 的 Web 服務，而且該 Web 服務必須公開 `ConvertTemperature` 方法。  如需詳細資訊，請參閱 [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 這個程式碼不會在 Web 應用程式專案中運作。  
  
## 需求  
  
### 依專案類型的可用性  
  
|||  
|-|-|  
|專案類型|是否可用|  
|Windows 應用程式|**是**|  
|類別庫|**是**|  
|主控台應用程式|**是**|  
|Windows 控制項程式庫|**是**|  
|Web 控制項程式庫|**是**|  
|Windows 服務|**是**|  
|網站|否|  
  
## 請參閱  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>   
 <xref:System.ArgumentException>   
 [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)