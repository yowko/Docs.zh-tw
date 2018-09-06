---
title: 使用文字檔追蹤
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: 19b4d544bc1d1c5bc9ebfa51b4ba28eb82c525d0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773342"
---
# <a name="tracking-using-a-text-file"></a>使用文字檔追蹤
此範例示範如何建立自訂追蹤參與者來擴充追蹤在 Windows Workflow Foundation (WF)。 追蹤參與者是可接收執行階段所發出之追蹤記錄的 .NET Framework 類別。 您可以建立追蹤參與者，將追蹤事件傳輸至特定狀況所需的任何目的地。 例如，ETW (Windows 事件追蹤) 追蹤參與者是在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中提供的。 這個範例中的追蹤參與者會將 XML 格式的記錄寫入至文字檔。  
  
## <a name="sample-details"></a>範例詳細資料  
 若要最佳化追蹤參與者的實用性和強固性，必須完成一些額外步驟，將追蹤參與者適當連接至執行階段。 下表描述這個範例中建立以最佳作法編譯之追蹤參與者所用的類別。  
  
|類別|描述|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 是用來定義用於設定文字檔追蹤參與者的組態區段。 這可讓使用者使用標準 .NET Framework 組態檔來指定記錄檔的目的地。|  
|`TextFileTrackingBehavior`|WCF 中的行為可讓使用者將延伸模組插入執行階段。 當服務啟動時，此行為會將追蹤參與者加入至服務。|  
|`TextFileTrackingParticipant`|在執行階段，接收追蹤記錄並將其以 XML 格式儲存至記錄檔的追蹤參與者。|  
  
## <a name="behavior-extension-elements-configuration"></a>行為延伸項目組態  
 必須完成另一個步驟，才能透過 .NET Framework 組態檔來利用先前描述的行為延伸項目。 下列組態必須放置在要使用此延伸模組的組態檔中。  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  如需行為延伸項目組態的完整範例使用方式，請參閱範例中的 Web.config 檔案。  
  
## <a name="custom-tracking-records"></a>自訂追蹤記錄  
 GetStockPrices.cs 檔案示範如何從 <xref:System.Activities.CodeActivity> 中建立自訂追蹤記錄。 在執行範例時請尋找此記錄。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 WFStockPriceApplication.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
     瀏覽器視窗隨即開啟並顯示應用程式的目錄清單。  
  
4.  在瀏覽器中，按一下 StockPriceService.xamlx。  
  
5.  瀏覽器會顯示**StockPriceService**頁面，其中包含本機服務 wsdl 位址。 複製此位址。  
  
     本機服務 wsdl 位址的範例是 http://localhost:53797/StockPriceService.xamlx?wsdl 。  
  
6.  使用 [[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]] 移至 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 資料夾 (預設安裝資料夾為 %SystemDrive%\Program Files\Microsoft Visual Studio 10.0)。 然後尋找 Common7\IDE\ 子資料夾。  
  
7.  按兩下 WcfTestClient.exe 檔案以啟動 WCF 測試用戶端。  
  
8.  在 WCF 測試用戶端中，選取 **新增服務...** 從**檔案**功能表。  
  
9. 將剛才複製的 URL 貼到文字方塊中。  
  
10. 按一下 **確定**以關閉對話方塊。  
  
11. 使用 WCF 測試用戶端測試此服務。  
  
    1.  在 WCF 測試用戶端中，按兩下**Istockpriceservice**下方**getstockprice （)** 節點。  
  
         **Istockpriceservice**方法會出現在右窗格中，具有一個參數。  
  
    2.  輸入 Contoso 做為參數值。  
  
    3.  按一下 **叫用**。  
  
12. 查看位於應用程式目錄之記錄檔 (即 %APPDATA%\trackingRecords.log) 的追蹤事件。  
  
    > [!NOTE]
    >  %APPDATA%是環境變數，可解析成 %SystemDrive%\Users\\< 使用者名稱\>中的 \AppData\Roaming [!INCLUDE[wv](../../../../includes/wv-md.md)]， [!INCLUDE[lserver](../../../../includes/lserver-md.md)]，或 Windows Server 2008。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 監控範例](https://go.microsoft.com/fwlink/?LinkId=193959)
