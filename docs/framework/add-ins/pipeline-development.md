---
title: 管線開發
ms.date: 03/30/2017
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f981d667f3cbf35ab010ac5bd26a9ecd5c2aae11
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135429"
---
# <a name="pipeline-development"></a>管線開發
增益集管線是主應用程式和其增益集必須使用與彼此進行通訊的管線區段的路徑。  
  
 下圖顯示的通訊管線和其區段。  
  
 ![新增&#45;管線模型中。](../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
增益集管線  
  
 主應用程式是其中一端的管線和增益集是在另一端。 從 每一端，且邁向中間，主應用程式和增益集已定義兩者共用的物件模型的檢視的抽象基底類別。 這些型別 （類別） 是由增益集檢視管線區段和增益集管線區段的 [主機] 檢視所組成。 增益集檢視管線區段通常會包含一個以上的抽象類別，但增益集繼承自的類別就所謂的增益集基底。  
  
 增益集端配接器管線區段，主應用程式端配接器管線區段轉換的型別，其檢視管線區段與合約管線區段之間的流程。 管線的中央區段是衍生自合約<xref:System.AddIn.Contract.IContract>介面。 此合約會定義主應用程式和其增益集都會使用的方法。  
  
 如果您將主機和增益集載入不同的應用程式定義域，您會有隔離界限分隔範圍從增益集主應用程式的範圍。 合約是只在主機和增益集應用程式定義域中載入的組件。 主機和增益集在每個只能參考其檢視的合約方法。 因此，會以從合約的抽象層分隔。  
  
 若要開發管線區段，您必須建立將包含的目錄結構。 如需有關開發需求和範圍的指導方針的詳細資訊，請參閱[管線開發需求](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。  
  
 下圖顯示管線區段所組成的類型。 在圖例中顯示的型別名稱是任意的但主機和主機以外的所有類型都檢視的增益集需要的屬性，所以建構資訊儲存庫的方法可以找到它們。  
  
 ![新增&#45;中具有所需屬性類型的模型。](../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
具有類型的增益集管線  
  
 下表描述用來啟用增益集管線區段。 如需有關這些區段的詳細資訊，請參閱 <<c0> [ 合約、 檢視和配接器](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)。  
  
|管線區段|描述|  
|----------------------|-----------------|  
|主機|建立增益集的執行個體的應用程式組件。|  
|增益集主應用程式檢視|表示物件型別和方法用來與增益集通訊的主應用程式的檢視。 [主機] 檢視是一個抽象基底類別或介面。|  
|主應用程式端配接器|調整與合約的方法具有一個或多個類別的組件。<br /><br /> 此管線區段由使用<xref:System.AddIn.Pipeline.HostAdapterAttribute>屬性。<br /><br /> 不支援多模組組件。|  
|合約|衍生自介面<xref:System.AddIn.Contract.IContract>介面以及定義的通訊協定進行通訊的主機和其增益集之間的類型。<br /><br /> 此管線區段由設定<xref:System.AddIn.Pipeline.AddInContractAttribute>屬性。|  
|增益集端配接器|調整與合約的方法具有一個或多個類別的組件。<br /><br /> 此管線區段由使用<xref:System.AddIn.Pipeline.AddInAdapterAttribute>屬性。<br /><br /> 包含具有類型的增益集端配接器目錄中的每個組件<xref:System.AddIn.Pipeline.AddInAdapterAttribute>屬性載入增益集的應用程式定義域。<br /><br /> 在自己的應用程式定義域中，會載入增益集端目錄中的每個組件。<br /><br /> 不支援多模組組件|  
|增益集檢視|組件，表示增益集檢視的物件類型和方法，用來與主機通訊。 增益集檢視是一個抽象基底類別或介面。<br /><br /> 此管線區段由使用<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性。<br /><br /> 在包含的類型具有 AddInViews 目錄中的每個組件<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性載入增益集的應用程式定義域。|  
|增益集|會執行的服務，主應用程式具現化的類型。|  
  
## <a name="pipeline-activation-path"></a>管線啟動路徑  
 啟動增益集時下, 圖顯示的啟動類型。 它也會顯示物件的傳遞至主機，例如計算或物件的集合的結果。 這是最常見的案例。  
  
 ![新增&#45;具有啟動路徑的模型中。](../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
從增益集主應用程式的啟動路徑  
  
 管線的啟動路徑會如下所示：  
  
1.  主應用程式會啟動增益集與<xref:System.AddIn.Hosting.AddInToken.Activate%2A>方法。  
  
2.  增益集、 增益集檢視、 增益集端配接器，以及合約組件會載入增益集的應用程式定義域。  
  
3.  使用增益集檢視來建立增益集端配接器執行個體 (所識別的類別與<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性) 作為其建構函式。 增益集端配接器會從合約繼承。  
  
4.  增益集端配接器，其為合約型別之間 （選擇性） 的隔離界限傳遞至主應用程式端配接器的建構函式。  
  
5.  主應用程式檢視的增益集，主應用程式端配接器，並將合約組件載入主機的應用程式定義域。  
  
6.  建立主應用程式端配接器執行個體作為其建構函式中使用合約。 主應用程式端配接器是由增益集的 [主機] 檢視所繼承。  
  
7.  主機有增益集，它主機檢視的增益集，以及可以繼續呼叫其方法型別。  
  
## <a name="walkthroughs"></a>逐步解說  
 有三個逐步解說主題描述如何使用 Visual Studio 來建立管線：  
  
-   [逐步解說：建立可延伸應用程式](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     描述主機執行加法、 減法、 乘法和除法計算的計算機增益集。  
  
-   [逐步解說： 啟用主應用程式變更的回溯相容性](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     描述計算機增益集與增強的計算功能，以及如何維護與第一個計算機增益集的相容性。  
  
-   [主機和增益集之間的逐步解說： 將集合](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     描述如何透過使用案例的管線傳遞資料集合。  
  
## <a name="see-also"></a>另請參閱  
- [增益集管線案例](https://msdn.microsoft.com/library/feb70e0b-8734-494c-aeaf-b567f014043e)  
- [增益集和擴充性](../../../docs/framework/add-ins/index.md)
