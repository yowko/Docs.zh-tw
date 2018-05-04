---
title: 增益集和擴充性
ms.date: 03/30/2017
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f097a14486b9a07df867ffa5514da33f3db6d4b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="add-ins-and-extensibility"></a>增益集和擴充性
<a name="top"></a> 增益集可以為主應用程式提供擴充的功能或服務。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 提供程式設計模型，開發人員可用來開發增益集，並且在其主應用程式中加以啟動。 模型的做法是在主應用程式與增益集之間建構通訊管線。 此模型是藉由使用 <xref:System.AddIn>、 <xref:System.AddIn.Hosting>、 <xref:System.AddIn.Pipeline>和 <xref:System.AddIn.Contract> 命名空間中的類型來實作。  
  
 本概觀包含下列各節：  
  
-   [增益集模型](#addin_model)  
  
-   [增益集與主應用程式的區別](#distinguishing_between_addins_and_hosts)  
  
-   [相關主題](#related_topics)  
  
-   [參考資料](#reference)  
  
> [!NOTE]
>  您可以在 [CodePlex 的 Managed 擴充性和增益集架構網站](http://go.microsoft.com/fwlink/?LinkId=121190)上找到其他範例程式碼，以及用來建立增益集管線之工具的客戶技術預覽。  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a>增益集模型  
 增益集模型是由一連串區段所組成，這些區段構成增益集管線 (也稱為通訊管線)，負責增益集與主應用程式之間的所有通訊。 管線是區段的對稱式通訊模型，這些區段會在增益集及其主應用程式之間交換資料。 在主應用程式與增益集之間開發這些區段，可提供必要的抽象層，以支援增益集的版本控制和隔離。  
  
 下圖顯示管線。  
  
 ![新增&#45;管線模型中。] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
增益集管線  
  
 這些區段的組件不一定要在相同的應用程式定義域中。 您可以將增益集載入至其本身的新應用程式定義域、現有的應用程式定義域，甚至主機的應用程式定義域中。 您可以將多個增益集載入相同的應用程式定義域中，讓增益集能夠共用資源和安全性內容。  
  
 增益集模型可支援並建議主應用程式與增益集之間的選擇性界限，就是所謂的隔離界限 (又稱為遠端界限)。 這個界限可以是應用程式定義域或處理序界限。  
  
 管線中間的合約區段會載入至主應用程式定義域和增益集的應用程式定義域中。 此合約會定義主應用程式和增益集用來彼此交換類型的虛擬方法。  
  
 若要通過隔離界限，類型必須是合約或可序列化的類型。 不是合約或可序列化的類型，必須由管線中的配接器區段轉換成合約。  
  
 管線的檢視區段是抽象基底類別或介面，依照合約的定義，提供主應用程式和增益集其共用方法的檢視。  
  
 如需有關開發管線區段的詳細資訊，請參閱 [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md)。  
  
 以下各節說明增益集模型的功能。  
  
### <a name="independent-versioning"></a>獨立版本設定  
 此增益集模型可讓主應用程式和增益集獨立進行版本設定。 所以此增益集模型可用於下列案例：  
  
-   建立配接器，讓主應用程式能夠使用針對舊版主應用程式建置的增益集。  
  
-   建立配接器，讓主應用程式能夠使用針對新版主應用程式建置的增益集。  
  
-   建立配接器，讓主應用程式能夠使用針對不同主應用程式建置的增益集。  
  
### <a name="discovery-and-activation"></a>探索和啟動  
 若要啟動增益集，您可以使用從資訊存放區找到之增益集集合中的語彙基元。 若要尋找增益集，您可以搜尋用來定義增益集之主應用程式檢視的類型。 您也可以依據定義增益集的類型來尋找特定增益集。 資訊存放區是由兩個快取檔案所組成：管線存放區和增益集存放區。  
  
 更新和重建資訊存放區的相關資訊，請參閱[增益集探索](http://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421)。 如需啟動增益集的相關資訊，請參閱[增益集啟動](http://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f)和[如何： 啟動增益集具有不同的隔離和安全性](http://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5)。  
  
### <a name="isolation-levels-and-external-processes"></a>隔離等級和外部處理序  
 此增益集模型可支援增益集及其主應用程式之間或增益集之間的數個隔離等級。從最低的隔離等級開始，這些等級如下：  
  
-   增益集在與主應用程式相同的應用程式定義域中執行。 不建議這麼做，因為這樣就少了使用不同應用程式定義域時所提供的隔離和卸載功能。  
  
-   多個增益集載入至相同的應用程式定義域中，而其不同於主應用程式所使用的應用程式定義域。  
  
-   每個增益集都獨自載入至其本身的應用程式定義域中。 這是最常見的隔離等級。  
  
-   多個增益集在外部處理序中，載入至相同的應用程式定義域。  
  
-   每個增益集都在外部處理序中，獨自載入至其本身的應用程式定義域中。 這是隔離等級最高的案例。  
  
 如需有關使用外部處理序的詳細資訊，請參閱[如何： 啟動增益集具有不同的隔離和安全性](http://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5)。  
  
### <a name="lifetime-management"></a>存留期管理  
 由於增益集模型跨越應用程式定義域和處理序界限，因此記憶體回收本身並不足以釋放及回收物件。 增益集模型提供一種生命週期管理機制，其使用語彙基元和參考計數，而且通常不需要額外的程式設計。 如需詳細資訊，請參閱[生命週期管理](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5)。  
  
 [回到頁首](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a>增益集與主應用程式的區別  
 增益集與主應用程式之間的差異，只在於增益集是由主應用程式啟動。 主應用程式可以是兩者中較大的一個，例如文字處理應用程式及其拼字檢查工具；或者，主應用程式可以是兩者中較小的一個，例如內嵌媒體播放程式的立即訊息用戶端。 此增益集模型支援用戶端及伺服器案例中的增益集。 伺服器增益集的範例，包括為郵件伺服器提供病毒掃描、垃圾郵件篩選和 IP 保護的增益集。 用戶端增益集範例包括參考增益集文字處理器、 圖形程式和遊戲，以及本機電子郵件用戶端掃描病毒的特製化功能。  
  
 [回到頁首](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md)|說明從主應用程式到增益集之區段的通訊管道。 提供逐步解說主題描述如何建構管線，以及如何將區段部署至 Visual Studio 中的管線中的程式碼範例。|  
|[應用程式定義域和組件](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|說明應用程式定義域 (針對安全性、可靠性和版本控制提供隔離界限) 與組件之間的關係。|  
  
 [回到頁首](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>參考資料  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [回到頁首](#top)