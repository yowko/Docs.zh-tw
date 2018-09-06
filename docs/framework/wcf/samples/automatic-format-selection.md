---
title: 自動格式選取
ms.date: 03/30/2017
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
ms.openlocfilehash: 4fd695195f5c7c13bc088248a6b3c12388328d37
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873045"
---
# <a name="automatic-format-selection"></a>自動格式選取
此範例會示範如何啟用自動格式選取 （XML 或 JSON） 使用的 Windows Communication Foundation (WCF) REST 程式設計模型，以及如何明確設定作業碼中的格式。  
  
## <a name="sample-details"></a>範例詳細資料  
 這個範例包含服務，以及可對服務發出要求的用戶端程式碼。 服務支援單一 HTTP `GET` 作業 (`EchoWithGet`) 以及單一 HTTP `POST` 作業 (`EchoWithPost`)。 這兩種作業都需要字串，然後會在回應中傳回字串。 在 `GET` 作業中，字串會在 URI 查詢字串參數中提供。 而在 `POST` 作業中，字串會在以 XML 序列化的要求主體中提供。 服務能夠以 XML 或 JSON 傳回回應，並且利用 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 中新的自動格式選取和命令式格式選取功能。  
  
 在這個範例中，自動格式選取是使用 App.config 檔啟用。 在預設的 Web HTTP 端點上，`automaticFormatSelectionEnabled` 屬性已有 `true` 值。 啟用自動格式選取，WCF 基礎結構會選取最適合的回應格式 （XML 或 JSON） 指定的要求 HTTP Accept 或 Content-type 標頭。 開發人員除了將 `automaticFormatSelectionEnabled` 屬性設定為 `true` 以使用這個新功能之外，不需要提供任何額外的程式碼或組態。 在 Program.cs 中用戶端程式碼中，要求會傳送兩個`GET`和`POST`HTTP Accept 標頭指定為"application/xml"或"application/json"的服務和服務作業傳回的回應個別的格式。  
  
 在 `GET` 作業中同樣會使用命令式格式選取。 `GET` 作業會檢查選擇性的 `format` 查詢字串參數，如果該參數存在，則會設定 <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A> 屬性上的回應格式。 以命令方式設定回應格式，如此一來，就會覆寫由 WCF 基礎結構自動格式化選取範圍。  
  
 此範例包含在主控台應用程式中執行的自我裝載服務和用戶端。 當主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  開啟「自動格式選取範例」的方案。 啟動 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 時，您必須以系統管理員身分執行，才能讓範例成功執行。 執行這項操作，以滑鼠右鍵按一下[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]圖示，然後選取**系統管理員身分執行**從內容功能表。  
  
2.  按下 CTRL+SHIFT+B 建置方案，然後按下 Ctrl+F5 執行主控台應用程式 AutomaticFormatSelection 專案。 主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。  
  
3.  當範例執行時，用戶端會對服務傳送要求，然後將回應寫入至主控台視窗。 請注意 XML 和 JSON 兩種不同格式的回應。  
  
4.  按下任何按鍵可終止此範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>另請參閱
