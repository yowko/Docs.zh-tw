---
title: "以組態為基礎的啟用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d520a46bc3380fc5dff76f5df866ae3411d5a6a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-based-activation"></a>以組態為基礎的啟用
此範例示範如何在不需要 .svc 檔案的情況下啟動 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a>範例詳細資料  
 在這個範例中，用戶端是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的測試用戶端，而服務是裝載在 IIS 中。  
  
> [!NOTE]
>  此範例的安裝與建立指示位於本主題的結尾。  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a>在不需要 .svc 檔案的情況下啟動服務  
 在 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 中，啟動服務需要 .svc 檔案。 這會造成額外的管理負荷，因為需要額外的檔案才能與應用程式一起進行部署和維護。 使用 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 版時，可以使用應用程式組態檔設定啟動元件。  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 在應用程式組態檔的 <xref:System.ServiceModel.Configuration.ServiceActivationElement> 中導入新的組態項目 (<xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>)。 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> 集合會接受一組要啟動的服務，如下列程式碼範例所示。  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 結果是，此組態看起來非常類似 .svc 檔案的組態。 所導入的其他屬性為提供服務位址的 `relativeAddress`。 相對位址也就是服務的虛擬路徑。 主機會從 `virtualPath` 位置擷取檔案的 Web.config 檔 (如果存在)，否則，主機會以遞迴方搜尋其上層資料夾。  
  
> [!NOTE]
>  此範例需要裝載在 IIS 中才能運作。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 Service.csproj 檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  執行 WCFTestClient.exe 來測試服務。  
  
4.  使用 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 巡覽至 %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE 資料夾。  
  
5.  執行 WcfTestClient.exe。  
  
6.  設定服務的 MEX 位址。  
  
7.  按下 CTRL+SHIFT+A 來設定服務位址。  
  
8.  將位址設定為 http://localhost/ServiceModelSamples/Calculator.svc。  
  
9. 執行 `Add` 作業。 將 `n1` 參數的值設定為 10，並將 `n2` 參數的值設定為 15。  
  
10. 按**叫用**。  
  
     預期的結果為 25。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  確認您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  在建立方案後，執行 Setup.bat 以便在 IIS 中安裝 ServiceModelSamples 應用程式。 ServiceModelSamples 目錄現在應該會顯示為 IIS 應用程式。  
  
4.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
## <a name="see-also"></a>請參閱  
 [AppFabric 主控與持續性範例](http://go.microsoft.com/fwlink/?LinkId=193961)
