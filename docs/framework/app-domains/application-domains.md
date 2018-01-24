---
title: "應用程式定義域"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process boundaries for isolation
- application isolation
- application domains, about
- common language runtime, application domains
- application domains
- runtime, application domains
- isolation between applications
- code, verification process
- verification testing code
ms.assetid: 113a8bbf-6875-4a72-a49d-ca2d92e19cc8
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe2d8ea8be2781e747398e18cc99cc6ce6cf6dc5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="application-domains"></a>應用程式定義域
作業系統和執行階段環境通常會在應用程式之間提供某種形式的隔離。 例如，Windows 會使用處理序來隔離應用程式。 這種隔離確保在某一應用程式中執行之程式碼不會對其他不相關應用程式造成負面影響。  
  
 應用程式定義域針對組件的安全性、可靠性和版本控制以及卸載提供了隔離界限。 應用程式定義域通常是由負責在應用程式執行前啟動 Common Language Runtime 的執行階段主應用程式所建立。  
  
 這一節中的主題將說明如何使用應用程式定義域來提供組件之間的隔離。  
  
 本概觀包含下列各節：  
  
-   [隔離應用程式的優點](#benefits)  
  
-   [參考資料](#reference)  
  
<a name="benefits"></a>   
## <a name="the-benefits-of-isolating-applications"></a>隔離應用程式的優點  
 在過去，一直是用處理序 (Process) 界限來隔離在同一電腦上執行的應用程式。 每個應用程式都會被載入用來分隔在同一電腦上執行之不同應用程式的個別處理序中。  
  
 這些應用程式所以能被分隔，是因為記憶體位址是相對於處理序；從一個處理序傳遞到另一個處理序的記憶體指標，在目標處理序中無法以任何有意義的方式使用。 此外，您也不能在兩個處理序之間直接進行呼叫。 而必須使用提供了一層間接取值 (Indirection) 的 Proxy。  
  
 Managed 程式碼必須通過驗證程序才能夠執行 (除非系統管理員已授予略過驗證的使用權限)。 驗證過程中會決定程式碼是否可能嘗試存取無效的記憶體位址，或執行可能導致執行該程式碼之處理序無法正常運作的動作。 通過驗證測試的程式碼被稱為型別安全。 驗證程式碼是否為型別安全的能力，可以讓 Common Language Runtime 以極低的效能損失，提供盡可能與處理序界限同樣高的隔離等級。  
  
 應用程式定義域提供了安全且多用途的處理單位，可以讓 Common Language Runtime 用來提供應用程式間的隔離。 使用存在於個別處理序中的相同隔離等級，您可以在單一處理序中執行好幾個應用程式定義域，而不會造成進行跨處理序呼叫或在處理序間切換的額外負荷。 在單一處理序中執行多個應用程式的能力大幅增加了伺服器的延展性 (Scalability)。  
  
 隔離應用程式對於應用程式安全性也極為重要。 例如，您可以從單一瀏覽器處理序中的幾個 Web 應用程式執行一些控制項，而且以此方法讓這些控制項不能存取彼此的資料和資源。  
  
 應用程式定義域提供的隔離具有以下優點：  
  
-   在某一應用程式中的錯誤不會影響其他應用程式。 由於型別安全程式碼不會導致記憶體錯誤，所以使用應用程式定義域可確保在某一定義域中執行的程式碼不會影響處理序中的其他應用程式。  
  
-   可以停止個別應用程式而不需停止整個處理序。 使用應用程式定義域可以讓您卸載在單一應用程式中執行的程式碼。  
  
    > [!NOTE]
    >  您不能卸載個別組件或型別。 只有完整的定義域可以卸載。  
  
-   在某一應用程式中執行的程式碼不能直接從其他應用程式存取程式碼或資源。 Common Language Runtime 是藉由防止不同應用程式定義域中物件之間的呼叫來強制執行這種隔離。 在不同定義域之間傳遞的物件必須用複製方式傳遞或由 Proxy 存取。 如果物件是複製的，那麼對該物件的呼叫就是區域呼叫。 也就是說，呼叫端和被參考的物件是在同一個應用程式定義域中。 如果物件是透過 Proxy 存取，那麼對物件的呼叫便是遠端呼叫。 在這種情況下，呼叫端和被參考的物件是在不同的應用程式定義域中。 跨定義域呼叫是使用與兩個處理序或兩部電腦之間呼叫相同的遠端呼叫基礎結構。 因此，所參考之物件的中繼資料 (Metadata) 必須在這兩個應用程式定義域中都能使用，才能讓該方法呼叫被 JIT 適當地編譯。 如果呼叫定義域無權存取所呼叫的物件之中繼資料，則編譯可能會失敗，並擲回 **System.IO.FileNotFound** 類型的例外狀況。 如需詳細資訊，請參閱[遠端物件](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)。 決定如何跨定義域存取物件的機制是由該物件決定。 如需詳細資訊，請參閱<xref:System.MarshalByRefObject?displayProperty=nameWithType>。  
  
-   程式碼的行為範圍是由執行該程式碼的應用程式決定。 換言之，應用程式定義域會提供應用程式版本原則、它所取之任何遠端組件的位置，以及有關在哪裡尋找載入定義域中之組件等組態設定。  
  
-   授予程式碼的使用權限可以由執行該程式碼的應用程式定義域控制。  
  
  
## <a name="application-domains-and-assemblies"></a>應用程式定義域和組件  
 這個主題是描述應用程式定義域和組件之間的關聯性。 您必須先將組件載入到應用程式定義域之後，才能執行它所包含的程式碼。 執行一個典型的應用程式會讓好幾個組件載入應用程式定義域。  
  
 載入組件的方式會決定其 Just-in-Time (JIT) 編譯程式碼是否能在處理序中由多個應用程式定義域所共用，以及組件是否能夠從處理序卸載。  
  
-   如果組件是以定義域中性方式 (Domain-neutral) 載入，所有共用相同安全性授權集的應用程式定義域，也就都能共用相同的 JIT 編譯程式碼，進而減少應用程式所需要的記憶體。 然而，組件則會永遠無法從處理序中卸載。  
  
-   如果組件不是以定義域中性方式載入，則在載入該組件的每一個應用程式定義域中，都必須是 JIT 編譯的。 然而，只要卸載所有載入該組件的應用程式定義域，即可從處理序中卸載組件。  
  
 執行階段主機會判斷將執行階段載入處理序時，是否要以定義域中性方式載入組件。 針對 Managed 應用程式，會將 <xref:System.LoaderOptimizationAttribute> 屬性 (Attribute) 套用到處理序的進入點方法，並從關聯的 <xref:System.LoaderOptimization> 列舉型別 (Enumeration) 中指定值。 針對裝載 Common Language Runtime 的 Unmanaged 應用程式，指定您在呼叫 [CorBindToRuntimeEx 函式](../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)方法時的適當旗標。  
  
 載入定義域中性組件的選項有三種：  
  
-   除了永遠以定義域中性方式載入的 Mscorlib 之外，<xref:System.LoaderOptimization> 不會以定義域中性方式載入任何組件。 這種設定稱為單一定義域，因為它通常使用於裝載程式只在處理序中執行單一應用程式的情況。  
  
-   <xref:System.LoaderOptimization> 會將所有組件都以定義域中性方式載入。 處理序中有多個應用程式定義域，而且它們全部都執行相同的程式碼時，請使用這種設定。  
  
-   如果強式名稱組件及其所有相依性項目都已安裝在全域組件快取中，<xref:System.LoaderOptimization> 便會以定義域中性方式載入這些組件。 其他組件都會分別載入並針對載入組件的每個應用程式定義域進行 JIT 編譯，因此這些組件都可以從處理序中卸載。 在相同處理序中執行多個應用程式時，或是有許多應用程式定義域及組件 (需要從處理序卸載) 共用的混合組件時，請使用這項設定。  
  
 對於使用 <xref:System.Reflection.Assembly.LoadFrom%2A> 類別 (Class) 的 <xref:System.Reflection.Assembly> 方法將載入內容載入的組件，以及使用指定位元組陣列之 <xref:System.Reflection.Assembly.Load%2A> 方法的多載而自影像載入組件，都無法共用 JIT 編譯程式碼。  
  
 已經使用 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 編譯成機器碼的組件，如果在第一次載入處理序時，是以定義域中性方式載入的，就可以在應用程式定義域之間共用。  
  
 針對包含應用程式進入點的組件，只有在能夠共用組件的所有相依性項目時，才能共用其 JIT 編譯程式碼。  
  
 對於以定義域中性方式載入的組件，可以進行一次以上的 JIT 編譯。 例如，當兩個應用程式定義域的安全性授權集不同時，兩者就不能共用相同的 JIT 編譯程式碼。 然而，JIT 編譯組件的每個複本都能與具有相同授權集的其他應用程式定義域共用。  
  
 在決定是否要將組件以定義域中性方式載入時，您必須在減少記憶體使用與其他效能考量之間做出取捨。  
  
-   對於定義域中性的組件，存取靜態資料和方法會比較緩慢，這是因為需要隔離組件。 存取該組件的每一個應用程式定義域都必須有靜態資料的單獨複本，以避免靜態欄位中物件的參考跨越定義域界限。 而其結果是，執行階段會含有額外的邏輯以便將呼叫端導向至靜態資料或方法的適當複本。 這些額外的邏輯就會讓呼叫慢下來。  
  
-   在將組件以定義域中性方式載入時，必須找到和載入組件的所有相依性項目。這是因為無法以定義域中性方式載入的相依性項目，也會使組件無法以定義域中性方式載入。  
  
## <a name="application-domains-and-threads"></a>應用程式定義域和執行緒  
 應用程式定義域會形成 Managed 程式碼的安全性、版本控制、可靠性及卸載的隔離界限。 執行緒是 Common Language Runtime 用來執行程式碼的作業系統建構。 在執行階段，所有 Managed 程式碼都會載入至應用程式定義域，並由一個或多個 Managed 執行緒來執行。  
  
 在應用程式定義域和執行緒之間不是一對一的相互關聯。 數個執行緒可以在任何指定時間於單一應用程式定義域內執行，而一個特定的執行緒並不受限於單一的應用程式定義域。 也就是說，執行緒可以自由跨越應用程式定義域界限；不會對每一應用程式定義域建立一個新的執行緒。  
  
 在任何指定的時間，每個執行緒都會在一個應用程式定義域中執行。 可能會有零個、一個或多個執行緒在任何指定的應用程式定義域中執行。 執行階段會不斷追蹤哪一個執行緒在哪一個應用程式定義域中執行。 您可以隨時呼叫 <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> 方法來找出有某個執行緒正在其中執行的定義域。  
  
### <a name="application-domains-and-cultures"></a>應用程式定義域和文化特性  
 文化特性 (由 <xref:System.Globalization.CultureInfo> 物件表示) 會與執行緒產生關聯。 您可以使用 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性取得與目前執行中執行緒相關聯的文化特性，也可以使用 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 屬性來取得或設定與目前執行中執行緒相關聯的文化特性。 如果已經使用 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 屬性明確設定與執行緒相關聯的文化特性，當執行緒跨越應用程式定義域界限時，文化特性會繼續與該執行緒相關聯。 否則，在任何指定時間與執行緒相關聯的文化特性會由執行緒執行所在之應用程式定義域中的 <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> 屬性值決定：  
  
-   如果該屬性的值不是 `null`，則該屬性所傳回的文化特性會與執行緒相關聯 (也因此會由 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性傳回)。  
  
-   如果該屬性的值為 `null`，則目前系統的文化特性會與執行緒相關聯。  
  
## <a name="programming-with-application-domains"></a>使用應用程式定義域設計程式  
 應用程式定義域通常是由執行階段主應用程式以程式方式建立和運用。 不過，有時候應用程式也會希望配合應用程式定義域來運作。 例如，應用程式可將應用程式元件載入到定義域中，如此才能夠卸載此定義域 (及此元件)，而不需要停止整個應用程式。  
  
 <xref:System.AppDomain> 是應用程式定義域的程式設計介面。 這個類別包括了一些方法，可用來建立及卸載定義域、建立定義域中的型別執行個體，以及註冊各種告知 (例如，應用程式定義域的卸載)。 下表列出常用的 <xref:System.AppDomain> 方法。  
  
|AppDomain 方法|描述|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|建立新的應用程式定義域。 建議您要使用指定 <xref:System.AppDomainSetup> 物件的這個方法多載。 這是設定新定義域之屬性的慣用方法，例如，應用程式基底或應用程式的根目錄；定義域組態檔的位置；以及 Common Language Runtime 要用來將組件載入定義域的搜尋路徑等屬性。|  
|<xref:System.AppDomain.ExecuteAssembly%2A> 和 <xref:System.AppDomain.ExecuteAssemblyByName%2A>|執行應用程式定義域中的組件。 這是執行個體方法，所以可用來在另一個您擁有參考的應用程式定義域中執行程式碼。|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|在應用程式定義域中建立指定之型別的執行個體，並傳回 Proxy。 使用這個方法可避免將包含建立之型別的組件載入到呼叫組件中。|  
|<xref:System.AppDomain.Unload%2A>|執行定義域的非失誤性的關閉。 一直要到在定義域中執行的所有執行緒都已停止或者已經離開定義域，應用程式定義域才會被卸載。|  
  
> [!NOTE]
>  Common Language Runtime 並不支援全域方法的序列化 (Serialization)，因此不能使用委派 (Delegate) 在其他應用程式定義域中執行全域方法。  
  
 Common Language Runtime 裝載介面規格中描述的 Unmanaged 介面也可提供應用程式定義域的存取。 Runtime 主應用程式可以從 Unmanaged 程式碼使用這些介面來建立並且取得處理序內應用程式定義域的存取。  
  
## <a name="complusloaderoptimization-environment-variable"></a>COMPLUS_LoaderOptimization 環境變數  
 環境變數，用於設定可執行應用程式的預設載入器最佳化原則。  
  
### <a name="syntax"></a>語法  
  
```  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>備註  
 一般的應用程式會將數個組件載入至應用程式定義域中，以便執行其中包含的程式碼。  
  
 載入組件的方式會決定其 Just-In-Time (JIT) 編譯程式碼是否能在處理序中由多個應用程式定義域所共用。  
  
-   如果組件是以定義域中性 (Domain-neutral) 方式載入，所有共用相同安全性授權集的應用程式定義域都能共用相同的 JIT 編譯程式碼。 這會減少應用程式所需要的記憶體。  
  
-   如果組件不是以定義域中性方式載入，則在載入該組件的每一個應用程式定義域中，該組件都必須是 JIT 編譯的，並且載入器不可以跨越應用程式定義域來共用內部資源。  
  
 當設定為 1 時，COMPLUS_LoaderOptimization 環境旗標會強制執行階段主應用程式以稱為 SingleDomain 的非定義域中性方式載入所有組件。 除了永遠以定義域中性方式載入的 Mscorlib 之外，SingleDomain 不會以定義域中性方式載入任何組件。 這種設定稱為單一定義域，因為它通常使用於裝載程式只在處理序中執行單一應用程式的情況。  
  
> [!CAUTION]
>  COMPLUS_LoaderOptimization 環境旗標是設計用於診斷及測試情節。 開啟旗標可能會造成速度大幅減慢，並增加記憶體使用量。  
  
### <a name="code-example"></a>程式碼範例  
 若要強制所有組件不載入為 IISADMIN 服務的定義域中性組件，可透過將 `COMPLUS_LoaderOptimization=1` 附加至 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN 機碼中環境的多字串值來完成。  
  
```  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
<a name="reference"></a>   
## <a name="reference"></a>參考資料  
 <xref:System.MarshalByRefObject?displayProperty=nameWithType>
