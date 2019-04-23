---
title: 擷取桌面應用程式中的資源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- resource files, packaging
- application resources, packaging
- localization
- versioning satellite assemblies
- retrieving localized resources
- application resources, deploying
- packaging application resources
- versioning resources
- translating resources into languages
- localizing resources
ms.assetid: eca16922-1c46-4f68-aefe-e7a12283641f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74469948ffe4045e6d367f1f60b8e66dc2a7810d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109794"
---
# <a name="retrieving-resources-in-desktop-apps"></a>擷取桌面應用程式中的資源
當您在 .NET Framework 傳統型應用程式中使用當地語系化資源時，最好使用主要組件封裝預設或中性文化特性的資源，並針對應用程式支援的每個語言或文化特性，建立個別的附屬組件。 然後您可以使用下一節中所述的 <xref:System.Resources.ResourceManager> 類別，來存取具名資源。 如果您選擇不要將資源嵌入主要組件和附屬組件，您也可以直接存取二進位 .resources 檔，如本文稍後的 [從 .resources 檔擷取資源](#from_file) 一節中所述。  若要擷取 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中的資源，請參閱 Windows 開發人員中心的 [建立和擷取 Windows 市集應用程式中的資源](https://go.microsoft.com/fwlink/p/?LinkID=241674) 。  
  
<a name="from_assembly"></a>   
## <a name="retrieving-resources-from-assemblies"></a>從組件擷取資源  
 <xref:System.Resources.ResourceManager> 類別提供對執行階段資源的存取。 您可以使用 <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> 方法來擷取字串資源，以及使用 <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType> 或 <xref:System.Resources.ResourceManager.GetStream%2A?displayProperty=nameWithType> 方法來擷取非字串資源。 每個方法都有兩個多載：  
  
-   具有單一參數的多載，此參數是包含資源名稱的字串。 此方法會嘗試擷取目前執行緒文化特性的資源。 如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager.GetString%28System.String%29>、 <xref:System.Resources.ResourceManager.GetObject%28System.String%29>和 <xref:System.Resources.ResourceManager.GetStream%28System.String%29> 方法。  
  
-   具有兩個參數的多載︰一個包含資源名稱的字串，以及一個代表所擷取資源之文化特性的 <xref:System.Globalization.CultureInfo> 物件。 如果找不到為該文化特性設定的資源，資源管理員會使用後援規則來擷取適當的資源。 如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>、 <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>和 <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> 方法。  
  
 資源管理員使用資源後援處理序，來控制應用程式如何擷取文化特性專屬資源。 如需詳細資訊，請參閱 [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)中的＜Resource Fallback Process＞一節。 如需具現化 <xref:System.Resources.ResourceManager> 物件的資訊，請參閱 <xref:System.Resources.ResourceManager> 類別主題中的＜Instantiating a ResourceManager Object＞(具現化 ResourceManager 物件) 一節。  
  
### <a name="retrieving-string-data-an-example"></a>擷取字串資料：範例  
 下列範例會呼叫 <xref:System.Resources.ResourceManager.GetString%28System.String%29> 方法來擷取目前 UI 文化特性的字串資源。 其中包含英文 (美國) 文化特性的中性字串資源，以及法文 (法國) 和俄文 (俄羅斯) 文化特性的當地語系化資源。 下列英文 (美國) 資源是在名為 Strings.txt 的檔案中：  
  
```  
TimeHeader=The current time is  
```  
  
 法文 (法國) 資源是在名為 Strings.fr-FR.txt 的檔案中：  
  
```  
TimeHeader=L'heure actuelle est  
```  
  
 俄文 (俄羅斯) 資源是在名為 Strings.ru-RU-txt 的檔案中：  
  
```  
TimeHeader=Текущее время —  
```  
  
 此範例的原始程式碼 (C# 版程式碼的檔名為 GetString.cs，Visual Basic 版為 GetString.vb) 會定義一個字串陣列，其中包含四個文化特性的名稱︰可用資源的三個文化特性，以及西班牙文 (西班牙) 文化特性。 會出現一個迴圈隨機執行五次，然後選取其中一個文化特性並將其指派給 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 屬性。 然後它會呼叫 <xref:System.Resources.ResourceManager.GetString%28System.String%29> 方法來擷取當地語系化字串，並連同日期時間一起顯示。  
  
 [!code-csharp[Conceptual.Resources.Retrieving#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstring.cs#3)]
 [!code-vb[Conceptual.Resources.Retrieving#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstring.vb#3)]  
  
 下列批次 (.bat) 檔案會編譯此範例，並在適當的目錄中產生附屬組件。 然後提供適用於 C# 語言和編譯器的命令。 若為 Visual Basic，請將 `csc` 變更為 `vbc`，並將 `GetString.cs` 變更為 `GetString.vb`。  
  
```  
resgen strings.txt  
csc GetString.cs -resource:strings.resources  
  
resgen strings.fr-FR.txt  
md fr-FR  
al -embed:strings.fr-FR.resources -culture:fr-FR -out:fr-FR\GetString.resources.dll  
  
resgen strings.ru-RU.txt  
md ru-RU  
al -embed:strings.ru-RU.resources -culture:ru-RU -out:ru-RU\GetString.resources.dll  
```  
  
 當目前 UI 文化特性為西班牙文 (西班牙) 時，請注意，此範例會顯示英文語言資源，因為西班牙文語言資源無法使用，而英文是此範例的預設文化特性。  
  
### <a name="retrieving-object-data-two-examples"></a>擷取物件資料：兩個範例  
 您可以使用 <xref:System.Resources.ResourceManager.GetObject%2A> 和 <xref:System.Resources.ResourceManager.GetStream%2A> 方法來擷取物件資料。 包括基本資料類型、可序列化的物件，以及使用二進位格式儲存的物件 (例如影像)。  
  
 下列範例使用 <xref:System.Resources.ResourceManager.GetStream%28System.String%29> 方法來擷取應用程式開頭顯示畫面視窗中使用的點陣圖。 下列原始程式碼位於名為 CreateResources.cs (適用於 C#) 或 CreateResources.vb (適用於 Visual Basic) 的檔案中，會產生包含序列化影像的 .resx 檔。 在此情況下，會從名為 SplashScreen.jpg 的檔案載入影像；您可以修改檔案名稱以替代成您自己的影像。  
  
 [!code-csharp[Conceptual.Resources.Retrieving#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/createresources.cs#4)]
 [!code-vb[Conceptual.Resources.Retrieving#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/createresources.vb#4)]  
  
 下列程式碼會擷取資源，並顯示 <xref:System.Windows.Forms.PictureBox> 控制項中的影像。  
  
 [!code-csharp[Conceptual.Resources.Retrieving#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/getstream.cs#5)]
 [!code-vb[Conceptual.Resources.Retrieving#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/getstream.vb#5)]  
  
 您可以使用下列批次檔來建立 C# 範例。 若是 Visual Basic，請將 `csc` 變更為 `vbc`，並將原始程式碼檔案的副檔名從 `.cs` 變更為 `.vb`。  
  
```  
csc CreateResources.cs  
CreateResources  
  
resgen AppResources.resx  
  
csc GetStream.cs -resource:AppResources.resources  
```  
  
 下列範例使用 <xref:System.Resources.ResourceManager.GetObject%28System.String%29?displayProperty=nameWithType> 方法來還原序列化自訂物件。 此範例包含名為 UIElements.cs (若是 Visual Basic 則為 UIElements.vb) 的原始程式碼檔，其中包含名為 `PersonTable`的下列結構。 此結構是為了供一般資料表顯示常式使用，以顯示資料表資料行的當地語系化名稱。 請注意， `PersonTable` 結構會以 <xref:System.SerializableAttribute> 屬性標記。  
  
 [!code-csharp[Conceptual.Resources.Retrieving#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example.cs#6)]
 [!code-vb[Conceptual.Resources.Retrieving#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#6)]  
  
 下列程式碼來自於名為 CreateResources.cs (若是 Visual Basic 則為 CreateResources.vb) 的檔案，會建立用以儲存資料表標題的 XML 資源檔 UIResources.resx，以及包含針對英文語言當地語系化之應用程式資訊的 `PersonTable` 物件。  
  
 [!code-csharp[Conceptual.Resources.Retrieving#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example1.cs#7)]
 [!code-vb[Conceptual.Resources.Retrieving#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example.vb#7)]  
  
 原始程式碼檔 GetObject.cs (GetObject.vb) 中的下列程式碼會接著擷取資源，並將其顯示到主控台。  
  
 [!code-csharp[Conceptual.Resources.Retrieving#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example2.cs#8)]
 [!code-vb[Conceptual.Resources.Retrieving#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example2.vb#8)]  
  
 您可以建立必要的資源檔和組件，並藉由執行下列批次檔來執行應用程式。 您必須使用 `/r` 選項將 UIElements.dll 的參考提供給 Resgen.exe，使其可以存取有關 `PersonTable` 結構的資訊。 如果使用 C#，請將 `vbc` 編譯器名稱取代成 `csc`，並將 `.vb` 副檔名取代成 `.cs`。  
  
```  
vbc -t:library UIElements.vb  
vbc CreateResources.vb -r:UIElements.dll  
CreateResources  
  
resgen UIResources.resx  -r:UIElements.dll  
vbc GetObject.vb -r:UIElements.dll -resource:UIResources.resources  
  
GetObject.exe  
```  
  
## <a name="versioning-support-for-satellite-assemblies"></a>附屬組件的版本控制支援  
 根據預設，當 <xref:System.Resources.ResourceManager> 物件擷取要求的資源時，它會尋找其版本號碼符合主要組件之版本號碼的附屬組件。 部署應用程式之後，您可能需要更新主要組件或特定資源附屬組件。 .NET Framework 提供主要組件和附屬組件的版本控制支援。  
  
 <xref:System.Resources.SatelliteContractVersionAttribute> 屬性為主要組件提供了版本控制支援。 在應用程式的主要組件上指定這個屬性可讓您更新並重新部署主要組件，而不更新其附屬組件。 更新主要組件之後，主要組件的版本號碼會遞增，但附屬合約版本號碼則保持不變。 當資源管理員擷取要求的資源時，它會載入此屬性指定的附屬組件版本。  
  
 發行者原則組件提供附屬組件的版本控制支援。 您可以更新並重新部署附屬組件，而不更新主要組件。 更新附屬組件之後，其版本號碼會遞增，並隨附於發行者原則組件。 在發行者原則組件中，指定您的新附屬組件與其舊版相容。 資源管理員會使用 <xref:System.Resources.SatelliteContractVersionAttribute> 屬性來判斷附屬組件的版本，但組件載入器會繫結至發行者原則所指定的附屬組件版本。 如需發行者原則組件的詳細資訊，請參閱 [Creating a Publisher Policy File](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)(建立發行者原則檔)。  
  
 若要啟用完整的組件版本控制支援，建議您在 [全域組件快取](../../../docs/framework/app-domains/gac.md) 中部署強式名稱的組件，並在應用程式目錄中部署沒有強式名稱的組件。 如果您想要在應用程式目錄中部署強式名稱的組件，當您更新組件時，將無法遞增附屬組件的版本號碼。 相反地，您必須執行就地更新，以更新的程式碼取代現有程式碼，並維持相同的版本號碼。 例如，如果您想要更新 1.0.0.0 版的附屬組件，而且該組件已完整指定組件名稱 "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a"，請覆寫成使用完整指定之相同組件名稱 "myApp.resources, Version=1.0.0.0, Culture=de, PublicKeyToken=b03f5f11d50a3a" 編譯的已更新 myApp.resources.dll。 請注意，在附屬組件檔上使用就地更新，會讓應用程式很難正確判斷附屬組件的版本。  
  
 如需組件版本控制的詳細資訊，請參閱 [組件版本控制](../../../docs/framework/app-domains/assembly-versioning.md) 和 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
<a name="from_file"></a>   
## <a name="retrieving-resources-from-resources-files"></a>從 .resources 檔擷取資源  
 如果您選擇不要部署附屬組件中的資源，您仍然可以使用 <xref:System.Resources.ResourceManager> 物件直接從 .resources 檔存取資源。 若要這樣做，您必須正確部署 .resources 檔。 然後您可以使用 <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%2A?displayProperty=nameWithType> 方法具現化 <xref:System.Resources.ResourceManager> 物件，並指定包含獨立 .resources 檔的目錄。  
  
### <a name="deploying-resources-files"></a>部署 .resources 檔  
 當您將 .resources 檔嵌入應用程式組件和附屬組件時，每個附屬組件都有相同的檔案名稱，但會放在反映附屬組件之文化特性的子目錄中。 相反地，當您直接從 .resources 檔存取資源時，您可以將所有 .resources 檔放在單一目錄中，通常是應用程式目錄的子目錄。 應用程式之預設 .resources 檔的名稱只包含根目錄名稱，而不會有其文化特性指示 (例如 strings.resources)。 每個當地語系化文化特性的資源會儲存在其名稱包含根目錄名稱後面接著文化特性的檔案 (例如 strings.ja.resources 或 strings.de-DE.resources)。 
 
 下圖顯示資源檔在目錄結構中的位置。 它也會提供 .resource 檔案的命名慣例。  

 ![顯示您應用程式主目錄的圖例。](./media/retrieving-resources-in-desktop-apps/resource-application-directory.gif)  
  
### <a name="using-the-resource-manager"></a>使用資源管理員  
 建立資源並放在適當目錄之後，您可以呼叫 <xref:System.Resources.ResourceManager> 方法，建立 <xref:System.Resources.ResourceManager.CreateFileBasedResourceManager%28System.String%2CSystem.String%2CSystem.Type%29> 物件來使用資源。 第一個參數指定應用程式預設 .resources 檔的根目錄名稱 (這會是上一節範例中的 "strings")。 第二個參數指定資源的位置 (上一個範例中的 "Resources")。 第三個參數指定要使用的 <xref:System.Resources.ResourceSet> 實作。 如果第三個參數是 `null`，則會使用預設執行階段 <xref:System.Resources.ResourceSet> 。  
  
> [!NOTE]
>  請勿使用獨立 .resources 檔部署 ASP.NET 應用程式。 這會造成鎖定問題並中斷 XCOPY 部署。 建議您部署附屬組件中的 ASP.NET 資源。 如需詳細資訊，請參閱 [ASP.NET Web Page Resources Overview](https://docs.microsoft.com/previous-versions/aspnet/ms227427(v=vs.100))。  
  
 具現化 <xref:System.Resources.ResourceManager> 物件之後，您可以使用稍早所述的 <xref:System.Resources.ResourceManager.GetString%2A>、 <xref:System.Resources.ResourceManager.GetObject%2A>和 <xref:System.Resources.ResourceManager.GetStream%2A> 方法來擷取資源。 不過，直接從 .resources 檔擷取資源，與從組件擷取內嵌資源不同。 當您從 .resources 檔擷取資源時， <xref:System.Resources.ResourceManager.GetString%28System.String%29>、 <xref:System.Resources.ResourceManager.GetObject%28System.String%29>和 <xref:System.Resources.ResourceManager.GetStream%28System.String%29> 方法一律會擷取預設文化特性的資源，而不論目前的文化特性為何。 若要擷取應用程式之目前文化特性或特定文化特性的資源，您必須呼叫 <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>、 <xref:System.Resources.ResourceManager.GetObject%28System.String%2CSystem.Globalization.CultureInfo%29>或 <xref:System.Resources.ResourceManager.GetStream%28System.String%2CSystem.Globalization.CultureInfo%29> 方法，並指定所要擷取之資源的文化特性。 若要擷取目前文化特性的資源，請將 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性的值指定為 `culture` 引數。 如果資源管理員無法擷取 `culture`的資源，則會使用標準資源後援規則來擷取適當的資源。  
  
### <a name="an-example"></a>範例  
 下列範例說明資源管理員如何直接從 .resources 檔擷取資源。 此範例是由英文 (美國)、法文 (法國) 和俄文 (俄羅斯) 文化特性的三個文字資源檔所組成。 英文 (美國) 是此範例的預設文化特性。 其資源會儲存在以下名為 Strings.txt 的檔案中：  
  
```  
Greeting=Hello  
Prompt=What is your name?  
```  
  
 法文 (法國) 文化特性的資源會儲存在以下名為 Strings.fr-FR.txt 的檔案中：  
  
```  
Greeting=Bon jour  
Prompt=Comment vous appelez-vous?  
```  
  
 俄文 (俄羅斯) 文化特性的資源會儲存在以下名為 Strings.ru-RU.txt 的檔案中：  
  
```  
Greeting=Здравствуйте  
Prompt=Как вас зовут?  
```  
  
 以下是範例的原始程式碼。 此範例會具現化英文 (美國)、英文 (加拿大)、法文 (法國) 和俄文 (俄羅斯) 文化特性的 <xref:System.Globalization.CultureInfo> 物件，並設定每個文化特性作為目前的文化特性。 <xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> 方法會接著提供 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性的值作為 `culture` 引數，來擷取適當的文化特性專屬資源。  
  
 [!code-csharp[Conceptual.Resources.Retrieving#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.retrieving/cs/example3.cs#9)]
 [!code-vb[Conceptual.Resources.Retrieving#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.retrieving/vb/example3.vb#9)]  
  
 您可以執行下列批次檔來編譯 C# 版的範例。 如果使用 Visual Basic，請將 `csc` 取代成 `vbc`，並將 `.cs` 副檔名取代成 `.vb`。  
  
```  
Md Resources  
Resgen Strings.txt Resources\Strings.resources  
Resgen Strings.fr-FR.txt Resources\Strings.fr-FR.resources  
Resgen Strings.ru-RU.txt Resources\Strings.ru-RU.resources  
  
csc Example.cs  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Resources.ResourceManager>
- [桌面應用程式中的資源](../../../docs/framework/resources/index.md)
- [封裝和部署資源](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [建立和擷取 Windows 市集應用程式中的資源](https://go.microsoft.com/fwlink/p/?LinkID=241674)
