---
title: "管線開發"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33646bbd7b0043cb5fc036b9b11aa4cf37cd537f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="pipeline-development"></a>管線開發
增益集管線是主應用程式和增益集必須用來與對方進行通訊管線區段的路徑。  
  
 下圖顯示的通訊管線及其區段。  
  
 ![新增 &#45; 管線模型中。] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
增益集管線  
  
 主機應用程式管線的一端與增益集的另一端。 從每一個結尾開始，而且移動中間，主應用程式和增益集已定義檢視的物件模型，它們都共用的抽象基底類別。 這些型別 （類別） 會構成檢視增益集管線區段和增益集管線區段的 [主機] 檢視。 檢視增益集管線區段通常會包含一個以上的抽象類別，但是加入在繼承自的類別就所謂的增益集基底。  
  
 增益集端配接器管線區段，主應用程式端配接器管線區段轉換類型，其檢視管線區段與合約管線區段之間的流量。 管線的中央區段是衍生自合約<xref:System.AddIn.Contract.IContract>介面。 這個合約會定義主應用程式和其增益集將會同時使用的方法。  
  
 如果成個別的應用程式定義域中載入主機和增益集，您必須隔離界限分隔主應用程式範圍從增益集的範圍。 合約是只有主機和增益集應用程式定義域中載入的組件。 主機和中的每個參考其檢視的合約方法。 因此，它們被分隔的從合約的抽象層。  
  
 若要開發管線區段，您必須建立包含它們的目錄結構。 如需開發需求與範圍的指導方針的詳細資訊，請參閱[管線開發需求](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)。  
  
 下圖顯示管線區段所組成的類型。 在圖例中顯示的型別名稱是任意的但主機和主機以外的所有類型都檢視的增益集需要屬性，所以建構資訊存放區的方法可以找到它們。  
  
 ![新增 &#45; 所需屬性的型別與模型中。] (../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
具有類型的增益集管線  
  
 下表描述用於啟用增益集管線區段。 如需有關這些區段的詳細資訊，請參閱[合約、 檢視和配接器](http://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)。  
  
|管線區段|描述|  
|----------------------|-----------------|  
|主機|建立增益集的執行個體應用程式組件。|  
|增益集的 [主機] 檢視|代表主應用程式檢視的物件類型和用來與增益集通訊的方法。 [主機] 檢視是一個抽象基底類別或介面。|  
|主機端配接器|會調整方法與合約具有一或多個類別的組件。<br /><br /> 這個管線區段由使用<xref:System.AddIn.Pipeline.HostAdapterAttribute>屬性。<br /><br /> 不支援多模組組件。|  
|合約|衍生自介面<xref:System.AddIn.Contract.IContract>介面以及定義通訊類型主機和其增益集之間的通訊協定。<br /><br /> 這個管線區段由設定<xref:System.AddIn.Pipeline.AddInContractAttribute>屬性。|  
|增益集端配接器|會調整方法與合約具有一或多個類別的組件。<br /><br /> 這個管線區段由使用<xref:System.AddIn.Pipeline.AddInAdapterAttribute>屬性。<br /><br /> 包含具有類型的增益集端配接器目錄中的每個組件<xref:System.AddIn.Pipeline.AddInAdapterAttribute>屬性載入增益集應用程式定義域。<br /><br /> 新增在端的目錄中的每個組件會在它自己的應用程式定義域中載入。<br /><br /> 不支援多模組組件|  
|增益集的檢視|組件，表示增益集的檢視物件型別和方法，可用來與主機通訊。 增益集檢視是一個抽象基底類別或介面。<br /><br /> 這個管線區段由使用<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性。<br /><br /> 每個組件中包含具有類型的 AddInViews 目錄<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性載入增益集應用程式定義域。|  
|增益集|會執行服務，主應用程式具現化的類型。|  
  
## <a name="pipeline-activation-path"></a>管線啟動路徑  
 下圖顯示類型的啟動時啟動增益集。 它也會顯示物件的傳遞至主機，例如計算或物件的集合的結果。 這是最常見的案例。  
  
 ![新增 &#45; 具有啟動路徑的模型中。] (../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
從增益集的啟動路徑至主機  
  
 管線的啟動路徑，就會發生，如下所示：  
  
1.  主應用程式會啟動增益集與<xref:System.AddIn.Hosting.AddInToken.Activate%2A>方法。  
  
2.  增益集，增益集的檢視、 新增在端配接器和合約組件會載入增益集應用程式定義域。  
  
3.  使用 [增益集] 檢視來建立增益集端配接器執行個體 (所識別的類別與<xref:System.AddIn.Pipeline.AddInBaseAttribute>屬性) 當做其建構函式。 增益集端配接器，繼承自該合約。  
  
4.  增益集端配接器，其為合約型別 （選擇性） 隔離界限之間傳遞至主應用程式端配接器的建構函式。  
  
5.  主機的應用程式定義域載入增益集，主應用程式端配接器，以及合約組件的 [主機] 檢視。  
  
6.  建立主應用程式端配接器執行個體當做其建構函式中使用合約。 主機端配接器會繼承自增益集的 [主機] 檢視。  
  
7.  主機具有增益集，其中型別為主機檢視的增益集，而且可以繼續呼叫其方法。  
  
## <a name="walkthroughs"></a>逐步解說  
 有三個逐步解說主題描述如何建立管線使用 Visual Studio:  
  
-   [逐步解說：建立可延伸應用程式](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     描述主控件執行加法、 減法、 乘法和除法計算的計算機增益集。  
  
-   [逐步解說： 啟用主機變更為回溯相容性](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     說明 [小算盤] 增益集與計算增強的功能，以及如何維護與第一個計算機增益集的相容性。  
  
-   [主控件與增益集之間的逐步解說： 傳遞集合](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     描述如何通過管線使用案例的資料集合。  
  
## <a name="see-also"></a>請參閱  
 [增益集管線案例](http://msdn.microsoft.com/library/feb70e0b-8734-494c-aeaf-b567f014043e)  
 [增益集和擴充性](../../../docs/framework/add-ins/index.md)
