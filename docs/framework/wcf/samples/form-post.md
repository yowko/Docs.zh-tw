---
title: "表單張貼"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa6f84f9-2e07-4e3c-92d0-a245308b7dff
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0fe1f8641de2b4ee504deeae8f97b312dfe9b99
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="form-post"></a>表單張貼
這個範例示範如何擴充 WCF REST 程式設計模型，以支援新的傳入要求格式。 這個範例還包括格式子的實作，可將 HTML 表單張貼的要求還原序列化為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 類型。 此外，這個範例使用 T4 範本傳回 HTML 頁面，該頁面提供可讓使用者回傳至 WCF REST 服務的 HTML 表單。  
  
## <a name="demonstrates"></a>示範  
  
-   延伸對傳入要求格式的支援。  
  
-   整合 T4 範本。  
  
## <a name="discussion"></a>討論  
 此範例包含兩個專案。 一個專案是包括自訂要求格式子的 HtmlFormProcessing 程式庫，該格式子可將 HTML 表單張貼還原序列化為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 類型。 另一個專案是主控台應用程式，它會擴充「基本資源服務」範例以使用 HtmlFormProcessing 程式庫的自訂要求格式子。  
  
 可還原序列化 HTML 表單張貼的自訂格式子 (HtmlFormRequestDispatchFormatter) 同時接受兩種類型，一種是可以使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 從字串轉換的 <xref:System.ServiceModel.Dispatcher.QueryStringConverter> 類型，另一種是以 <xref:System.Runtime.Serialization.DataContractAttribute> 標記的類型，它只有可使用 QueryStringConverter 從字串轉換的成員。  
  
 HtmlFormProcessing 程式庫專案還包括抽象基底類別 `RequestBodyDispatchFormatter`，可用來建立其他自訂要求格式子。 衍生自 `RequestBodyDispatchFormatter` 的方式可讓開發人員著重於要求主體還原序列化邏輯，該邏輯可讓基底類別將 URI 範本參數對應至作業的方法參數。 另外，HtmlFormProcessing 程式庫專案還包括 `HtmlFormProcessingBehavior` 類別，該類別會示範如何衍生自 <xref:System.ServiceModel.Description.WebHttpBehavior>，以便將預設要求格式子取代為自訂要求格式子。  
  
 此主控台應用程式專案擴充[基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)範例。 「基本資源服務」範例會示範如何以使用 WCF REST 程式設計模型的方式公開資源。 在「基本資源服務」範例中會公開客戶集合資源，以便建立、擷取、更新和刪除集合中的客戶。 「基本資源服務」範例僅使用兩種原本就支援的傳入要求格式：XML 和 JSON。  
  
 在這個「表單張貼」範例中的主控台應用程式會利用 HtmlFormProcessing 程式庫中的自訂格式子，該程式庫可讓使用者使用瀏覽器從 HTML 表單張貼傳送要求，藉此建立客戶。 它還會加入傳回 HTML 頁面的作業，該頁面包括回傳至服務的表單。 這個 HTML 頁面是使用預先處理的 T4 範本產生，而這個範本是由 .tt 檔和自動產生的 .cs 檔所組成。 .tt 檔可讓開發人員以包含變數和控制項結構的範本形式撰寫回應。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]T4，請參閱[所使用文字範本產生成品](http://go.microsoft.com/fwlink/?LinkId=178139)。  
  
#### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  開啟「表單張貼範例」的方案。 啟動 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 時，您必須以系統管理員身分執行，才能成功執行範例。 執行這項操作，以滑鼠右鍵按一下[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]圖示，然後從內容功能表中選擇 「 系統管理員身分執行 」。  
  
2.  按下 CTRL+SHIFT+B 建置方案，然後按下 CTRL+F5 執行主控台應用程式 FormPost 專案。  
  
3.  主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。  
  
4.  範例執行時，用戶端將目前活動的狀態 (無論是加入客戶、更新客戶、刪除客戶或取得目前客戶的清單) 從服務寫入至主控台視窗。  
  
5.  接著會提示您瀏覽至客戶表單的 URI。 開啟瀏覽器並瀏覽至指定的 URI。 輸入名稱和地址做為客戶按一下**送出** 按鈕。  
  
6.  按下主控台視窗的任意鍵，即可繼續執行範例。  
  
7.  範例完成時，請注意您使用瀏覽器建立的客戶會包含在最終客戶清單內。  
  
8.  按下任何按鍵可終止此範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Web\FormPost`
