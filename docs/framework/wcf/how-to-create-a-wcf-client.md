---
title: "HOW TO：建立 Windows Communication Foundation 用戶端 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "用戶端 [WCF], 執行"
  - "WCF 用戶端 [WCF], 執行"
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
caps.latest.revision: 64
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 64
---
# HOW TO：建立 Windows Communication Foundation 用戶端
這是在建立 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式時必須進行的六個工作中的第四個。如需這六個工作的概觀，請參閱[快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。  
  
 本主題會說明如何從 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務擷取中繼資料，以建立可以存取服務的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Proxy。這個工作是使用 Visual Studio 提供的 \[加入服務參考\] 功能來完成。這個工具會從服務的 MEX 端點取得中繼資料，並以您所選擇的語言 \(預設為 C\#\) 產生用戶端 Proxy 的 Managed 原始程式碼檔。除了建立用戶端 Proxy，此工具也會建立或更新用戶端組態檔，讓用戶端應用程式在其中一個端點與服務連線。  
  
> [!NOTE]
>  您還可以使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具來產生 Proxy 類別和組態，而不使用 Visual Studio 中的 \[加入服務參考\]。  
  
> [!WARNING]
>  從 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 的類別庫專案中呼叫 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務時，您可以使用 \[加入服務參考\] 功能來自動產生 Proxy 與相關聯的組態檔。類別庫專案將不會使用組態檔。您必須將所產生組態檔中的設定加入至將會呼叫類別庫之可執行檔的 app.config 檔案。  
  
 用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。這個程序會於 [HOW TO：使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)中說明。  
  
### 若要建立 Windows Communication Foundation 用戶端  
  
1.  用滑鼠右鍵按一下 \[使用者入門\] 方案並選取 \[**加入** **新的專案**\]，以建立新的主控台應用程式專案。在 \[**加入新的專案**\] 對話方塊左側，選取 \[**C\#**\] 或 \[**VB**\] 下方的 \[**Windows**\]。在對話方塊的中間區段中選取 \[**主控台應用程式**\]。將專案命名為 `GettingStartedClient`。  
  
2.  以滑鼠右鍵按一下 \[方案總管\] 中的 \[**GettingStartedClient**\] 並選取 \[**屬性**\]，將 GettingStartedClient 專案的目標 Framework 設定為 .NET Framework 4.5。在標示 \[**目標 Framework**\] 的下拉式方塊中選取 \[**.NET Framework 4.5**\]。設定 VB 專案目標 Framework 的方式稍有不同，請在 GettingStartedClient 專案屬性對話方塊中，按一下螢幕左側的 \[**編譯**\] 索引標籤，然後按一下對話方塊左下角的 \[**進階編譯選項**\] 按鈕。接著在標籤為 \[**目標 Framework**\] 的下拉式方塊中選取 \[**.NET Framework 4.5**\]。  
  
     設定目標 Framework 會導致 Visual Studio 2011 重新載入該方案，請在出現提示時按下 \[**確定**\]。  
  
3.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[GettingStartedClient\] 專案底下的 \[**參考**\] 資料夾並選取 \[**加入參考**\]，將 System.ServiceModel 專案的參考加入至 GettingStartedClient 專案。在 \[**加入參考**\] 對話方塊中，選取對話方塊左側的 \[**Framework**\]。在 \[搜尋組件\] 文字方塊中輸入 `System.ServiceModel`。在對話方塊中間區段中選取 \[**System.ServiceModel**\]，按一下 \[**加入**\] 按鈕，然後按一下 \[**關閉**\] 按鈕。按一下主功能表下的 \[**全部儲存**\] 按鈕，以儲存方案。  
  
4.  下次您會將服務參考加入至計算器服務。在您這樣做之前，必須先啟動 GettingStartedHost 主控台應用程式。一旦主機在執行中，您就可以在 \[方案總管\] 中用滑鼠右鍵按一下 \[GettingStartedClient\] 專案底下的 \[參考\] 資料夾，並選取 \[加入服務參考\]，然後在 \[加入服務參考\] 對話方塊的位址方塊中輸入下列 URL：http:\/\/localhost:8000\/ServiceModelSamples\/Service，再按一下 \[**執行**\] 按鈕。CalculatorService 接著應該會顯示在 \[服務\] 清單方塊中，請按兩下 \[CalculatorService\]，其將隨即展開並顯示服務所實作的服務合約。保留預設命名空間，並按一下 \[**確定**\] 按鈕。  
  
     當您使用 Visual Studio 加入服務的參考時，新項目將會在 \[方案總管\] 中 \[GettingStartedClient\] 專案底下的 \[服務參考\] 資料夾下方出現。如果您使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具，則會產生原始程式碼檔和 app.config 檔。  
  
     您也可以使用命令列工具 \([ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)\) 搭配適當的參數來建立用戶端程式碼。下列範例會產生服務的程式碼檔案與組態檔。第一個範例顯示如何在 VB 中產生 Proxy，而第二個則示範如何在 C\# 中產生 Proxy：  
  
    ```  
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service  
  
    ```  
  
    ```csharp  
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service  
  
    ```  
  
 現在您已建立用戶端應用程式將用來呼叫計算器服務的 Proxy。繼續進行系列中的下一個主題：[HOW TO：設定用戶端](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
  
## 請參閱  
 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [使用者入門](../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [自我裝載](../../../docs/framework/wcf/samples/self-host.md)   
 [HOW TO：使用組態檔發行服務的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)   
 [HOW TO：使用 Svcutil.exe 來下載中繼資料文件](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)