---
title: HOW TO：使用 COM+ 服務模型組態工具
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: d26e3b127328a3de4df6bd58fb6015bee045f3c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>HOW TO：使用 COM+ 服務模型組態工具
一旦您選取了適當的裝載模式，請使用 COM+ 服務模型組態命令列工具 (ComSvcConfig.exe) 來設定將公開為 Web 服務的應用程式介面。  
  
> [!NOTE]
>  您必須是電腦的系統管理員，才能執行下列任何一項工作。  
  
 在 Windows 7 電腦上使用 ComSvcConfig.exe 設定 Web 服務以使用最新的服務模型版本 (目前為 4.5 版) 時，請執行下列步驟：  
  
1.  設定登錄機碼`[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR`DWORD 值 （0x00000001）  
  
2.  執行 comsvcconfig.exe  
  
3.  將步驟 1 新增的登錄機碼還原成其原始值，或將它刪除 (如果不存在的話)。  
  
> [!IMPORTANT]
>  將這個登錄機碼還原是非常重要的步驟。 此為相容性的關鍵。 未還原這項變更可能會導致在電腦上執行的其他 .NET 應用程式發生問題)。  
  
> [!WARNING]
>  當使用 ComSvcConfig.exe 進行 Windows 8 電腦 對話方塊上的會顯示說明 「 您的電腦上的應用程式需要下列 Windows 功能：.NET Framework 3.5 (包括.NET 2.0 和.NET 3.0"如果未安裝.NET Framework 3.5。 您可以忽略這個對話方塊， 也可以將 OnlyUseLatestCLR 登錄機碼設定為 DWORD 值 (0x00000001)  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>若要將介面新增到即將公開為 Web 服務的介面集合，請使用 COM+ 裝載模式  
  
-   請使用 `/install` 和 `/hosting:complus` 選項來執行 ComSvcConfig，如下列範例所示。  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     此命令會將 `IFinances` 元件的 `ItemOrders.IFinancial` 介面 (來自 OnlineStore COM+ 應用程式) 新增到即將公開為 Web 服務的介面集合。 服務將使用 COM+ 裝載模式，因此需要明確的應用程式啟動。  
  
     儘管萬用星號 (*) 字元可以用在元件與介面上，但是因為您可能只想要將選取的功能公開為 Web 服務，因此請避免使用該字元。 如果與此元件的未來版本一起執行，使用萬用字元會不小心將決定組態語法時尚不存在的介面一併公開出來。  
  
     /verbose 選項會指示工具在任何錯誤旁邊加上警告。  
  
     公開服務的合約將包含來自 `IFinances` 介面的所有方法。  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>若只要將來自介面的特定方法新增至即將公開為 Web 服務的介面集合，請使用 COM+ 裝載模式  
  
-   請使用包含必要方法之明確命名的 `/install` 和 `/hosting:complus` 選項來執行 ComSvcConfig，如下列範例所示。  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     此命令只會將來自 `Credit` 介面的 `Debit` 和 `IFinances` 方法當成作業新增至公開的服務合約中。 介面上的其他所有方法都會從合約中省略，而且無法透過 Web 服務用戶端來呼叫。  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a>若要將介面新增到即將公開為 Web 服務的介面集合，請使用 Web 裝載模式  
  
-   請使用 `/install` 選項和 `/hosting:was` 選項來執行 ComSvcConfig，如下列範例所示。  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     此命令會將 `IStockLevels` 元件上的 `ItemInventory.Warehouse` 介面 (來自 OnlineWarehouse COM+ 應用程式) 新增至即將公開為 Web 服務的介面集合。 此服務是由 Web 裝載到 IIS (而不是 COM+) 的 OnlineWarehouse 虛擬目錄，因此必要時會自動啟動應用程式。  
  
     若要使用 Web 裝載的同處理序組態，必須將 COM+ 應用程式設定為透過元件服務系統管理主控台，並以程式庫應用程式身分，而不是以伺服器應用程式身分來執行。 設定為伺服器應用程式身分的應用程式會使用標準 Web 裝載模式，並產生處理序躍點來處理每項要求。  
  
     `/mex` 選項會新增使用相同傳輸的額外中繼資料交換 (MEX) 服務做為應用程式服務端點，以支援想要從服務中擷取合約定義的用戶端。  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a>若要移除指定介面的 Web 服務  
  
-   請使用 `/uninstall` 選項來執行 ComSvcConfig，如下列範例所示。  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     此命令會移除 `IFinances` 元件的 `ItemOrders.Financial` 介面 (來自 OnlineStore COM+ 應用程式)。  
  
### <a name="to-list-currently-exposed-interfaces"></a>若要列出目前公開的介面  
  
-   請使用 `/list` 選項來執行 ComSvcConfig，如下列範例所示。  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     此命令會列出限定於本機電腦範圍內，目前公開的介面以及對應的位址與繫結詳細資訊。  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a>若要列出目前公開的特定介面  
  
-   請使用 `/list` 選項來執行 ComSvcConfig，如下列範例所示。  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     此命令會列出本機電腦上 OnlineStore COM+ 應用程式目前公開的 COM+ 裝載介面，以及對應的位址與繫結詳細資訊。  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>若要針對可與公用程式一併使用的選項顯示相關說明  
  
-   請使用 /? 選項來執行 ComSvcConfig， 如下列範例所示。  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [整合 COM+ 應用程式概觀](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
