---
title: "執行 Windows Communication Foundation 範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 603a6dce17d527a3f14e408da19006509514df52
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="running-the-windows-communication-foundation-samples"></a>執行 Windows Communication Foundation 範例
此 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 範例可以在單一機器或跨機器組態中執行。 這些範例可依提供現狀直接執行於單一機器上。 在跨機器組態中，就需要修改範例的組態檔設定。 下列程序會說明如何在相同機器與跨機器組態中執行此範例。 請注意，透過網際網路資訊服務 (IIS) 裝載與自我裝載範例中的服務步驟會有所變化。 大部分的範例都是以 IIS 進行裝載；請參閱範例讀我資訊以決定其裝載方式。  
  
 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，不是裝載在 IIS 中的範例需要更高的權限向 Http.sys 註冊接聽項。 請使用 Httpcfg.exe 以在其中執行服務的帳戶來註冊服務的接聽位址，或從使用系統管理員權限執行的命令提示字元來啟用服務。  
  
> [!NOTE]
>  在建置或執行任何之前[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]範例，確認您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>若要在同一部機器上執行範例  
  
1.  如果服務是由 IIS 裝載，請輸入下列位址：http://localhost/servicemodelsamples/service.svc，確定您能夠使用瀏覽器來存取服務。 確認頁面應該會顯示在回應中。 如果未顯示 [確認] 頁面，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
2.  如果服務是自我裝載，請從語言特定資料夾中的 \service\bin 執行 Service.exe。 服務活動會顯示在服務主控台視窗上。  
  
3.  從 \client\bin 執行 Client.exe\\，將語言特定資料夾下。 用戶端活動會顯示在用戶端主控台視窗上。  
  
4.  如果用戶端和服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
### <a name="to-run-the-sample-across-machines"></a>若要跨機器執行範例  
  
1.  如果服務是以 IIS 裝載：  
  
    1.  在服務機器上，建立一個名稱為 ServiceModelSamples 的虛擬目錄。 批次檔隨附的 Setupvroot.bat[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)可用來建立磁碟和虛擬目錄。  
  
    2.  將服務程式檔案從 %SystemDrive%\Inetpub\wwwroot\servicemodelsamples 複製到服務機器上的 ServiceModelSamples 虛擬目錄。 確定您有將這些檔案包含至 \bin 目錄中。  
  
    3.  測試您是否能夠使用瀏覽器，從用戶端機器存取服務。  
  
     如果服務是自我裝載：  
  
    1.  在服務機器上，建立可儲存這些服務檔案的目錄。  
  
    2.  將語言特定資料夾下 \service\bin\ 資料夾中的服務程式檔複製到服務機器中。  
  
    3.  在服務組態檔案中，將端點定義的位址值變更成符合服務的新位址。 以位址中的完整網域名稱取代 "localhost" 的任何參考。  
  
    4.  從命令提示字元啟動 Service.exe。  
  
2.  將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端機器中。  
  
3.  設定端點位址。  
  
    1.  如果服務不是使用網域帳戶執行，請開啟用戶端組態檔，並將端點定義的位址值變更成符合服務的新位址。 以位址中的完整網域名稱取代 "localhost" 的任何參考。  
  
    2.  如果服務是使用網域帳戶執行，請針對服務執行 Svcutil.exe 以重新產生用戶端組態。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]執行 Svcutil.exe 時，請參閱[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。 使用產生的檔案，而不要使用範例中的組態檔。 產生的組態檔還有其他身分識別資訊，而且包含連接至服務端點需要的所有設定 (即使是預設的設定)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]身分識別資訊，請參閱[服務識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)，和[\<識別 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)。  
  
4.  在用戶端機器上，從命令提示字元啟動 Client.exe。  
  
### <a name="to-debug-a-service"></a>偵錯服務  
  
1.  建置方案 （用戶端和服務） 使用**建置**功能表或 CTRL + SHIFT + B。  
  
2.  如果服務是以 IIS 裝載：  
  
    1.  在瀏覽器輸入位址 http://localhost/servicemodelsamples/service.svc 來啟動服務。  
  
    2.  在方案中，選擇 **偵錯**功能表和**附加至處理序**功能表項目。  
  
    3.  選取**顯示所有使用者的處理序**核取方塊。  
  
    4.  選取主機背景工作處理序 W3wp.exe 來進行偵錯 (在 Windows XP 中選取 ASPNet_wp.exe)。  
  
3.  您現在可以在服務程式碼中設定中斷點，然後啟用發生例外狀況時的中斷點。  
  
4.  以滑鼠右鍵按一下 用戶端專案項目，然後選擇 **偵錯**，**開始新執行個體**。  
  
### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
-   如果因為考量安全性而以 IIS 裝載服務，則請在完成範例時，移除虛擬目錄定義以及在安裝步驟中所授與的權限。  
  
## <a name="see-also"></a>請參閱  
 [建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [工作群組中與跨電腦執行範例](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [疑難排解秘訣](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
